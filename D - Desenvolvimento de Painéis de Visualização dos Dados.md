# Uso de dados para otimizar a alocação de recursos públicos destinados ao saneamento básico de Goiás

### ADENILSON SILVA

 Para controle do fluxo de atividades do projeto, a consultoria utilizou o trello. Painel: [aqui](https://trello.com/b/RIgkWLxE/projeto-uso-de-dados-para-otimizar-a-aloca%C3%A7%C3%A3o-de-recursos-p%C3%BAblicos-destinados-ao-saneamento-b%C3%A1sico-de-goi%C3%A1s).
 
## DESENVOLVIMENTO DE PAINÉIS DE VISUALIZAÇÃO DOS DADOS
Para a elaboração dos painéis, a empresa de consultoria decidiu utilizá-los no _Power BI_.  Os dados serão extraídos diretamente do banco de dados _PostgreSQL_ por meio de três  [_views_](https://www.postgresql.org/docs/current/sql-createview.html).



### Modelo Entidade Relacionamento - MER

<div align="center">
  <img src="https://drive.google.com/uc?export=view&id=1nPYlpvguwwpdgGJYLUxSyF6reZRWsKNx" width="800">
</div>

### _Script_ criação das _views_
```sql
create
view view_desempenho as
with parametros as (
select
	3 as rtp, -- peso da relação tratado/produzido
	2 as rtc, -- peso da relação tratado/coletado
	1 as rcp -- peso da relação coletado/produzido
),
desempenho_calc as (
select
	vae.id_municipio,
	vae.ano_referencia,
	((p.rtp * vae.relacao_tratado_produzido) + 
         (p.rtc * vae.relacao_tratado_coletado) + 
         (p.rcp * vae.relacao_coletado_produzido)) / 6 as desempenho
from
	volume_anual_esgotos vae
cross join parametros p
)
select
	mun.nome,
	mun.codigo_ibge,
	vae.populacao_total_urbana,
	vae.volume_produzido_m3,
	vae.volume_coletado_m3,
	vae.volume_tratado_m3,
	vae.relacao_coletado_produzido,
	vae.relacao_tratado_coletado,
	vae.relacao_tratado_produzido,
	vae.ano_referencia,
	vae.possui_dado_interpolado,
	case
		when d.desempenho between 0 and 0.25 and vae.populacao_total_urbana > 0 then 'Ruim'
		when d.desempenho between 0.25 and 0.5 and vae.populacao_total_urbana > 0 then 'Regular'
		when d.desempenho between 0.5 and 0.75 and vae.populacao_total_urbana > 0 then 'Bom'
		when d.desempenho >= 0.75 and vae.populacao_total_urbana > 0 then 'Ótimo'
		else 'Indefinido'
	end as desempenho_geral
from
	desempenho_calc d
inner join municipio mun on
	d.id_municipio = mun.id_municipio
inner join volume_anual_esgotos vae on
	d.id_municipio = vae.id_municipio and d.ano_referencia = vae.ano_referencia
order by vae.ano_referencia desc, mun.nome asc;

create
view view_ranking_melhorias as
with ano_base as (
select
	2021 as ano
)
select
	row_number() over (
	order by vae.relacao_coletado_produzido,
	vae.relacao_tratado_produzido,
	vae.relacao_tratado_coletado asc,
        vae.populacao_total_urbana desc) posicao,
	mun.nome,
	mun.codigo_ibge
from
	volume_anual_esgotos vae
inner join municipio mun on
	vae.id_municipio = mun.id_municipio
inner join ano_base ab on
	vae.ano_referencia = ab.ano;

create
view view_ranking_novas_obras as
with ano_base as (
select
	2021 as ano
)
select
	row_number() over (
	order by vae.relacao_tratado_coletado,
	vae.relacao_coletado_produzido,
	vae.relacao_tratado_produzido asc,
	vae.populacao_total_urbana desc) posicao,
	mun.nome,
	mun.codigo_ibge
from
	volume_anual_esgotos vae
inner join municipio mun on
	vae.id_municipio = mun.id_municipio
inner join ano_base ab on
	vae.ano_referencia = ab.ano;
```

Feito isso, o _Power BI_ foi conectado ao banco de dados _PosgreSQL_ para a importação dos dados necessários.

Foram desenvolvido dois painéis:

**Painel I:**
<div align="center">
  <img src="https://drive.google.com/uc?export=view&id=1cQYE1HO1blWQq_mvFcpQZCnl8iKecwBr" width="1000">
</div>

* 1 - Filtro de Ano;

* 2 - Filtro de Minicípio;

* 3 - Número de Habitantes referente ao Município (2) ao Ano (1) filtrados;

* 4 - Desempenho dos serviços de tratamento de esgotos referente ao Município (2) ao Ano (1) filtrados, e com base na metodologia desenvolvida pela Secretaria Estadual de Meio Ambiente;

* 5 - Posição de prioridade do Município (2) filtrado para recebimento de recursos do governo estadual para obras de melhorias dos serviços públicos de saneamento atuais, e com base na metodologia desenvolvida pela Secretaria Estadual de Meio Ambiente;

* 6 - Posição de prioridade do Município (2) filtrado para recebimento de recursos do governo estadual para novas obras, com base na metodologia desenvolvida pela Secretaria Estadual de Meio Ambiente;

* 7 - Gráfico de eficiência (%) dos serviços de tratamento de esgotos do Município (2), em função do tempo (1992 a 2021);

* 8 - Gráfico de volume de esgotos produzidos, coletados e tratados do Município (2), em função do tempo (1992 a 2021).

 
**Painel II:**
<div align="center">
  <img src="https://drive.google.com/uc?export=view&id=1KPnviK14IXHb0D7GHq2PGyDdOVUyMNkH" width="1000">
</div>

* 9 - Filtro de Ano;

* 10 - Gráfico quantificando quantos Munícipios do estado se enquandrou em cada categoria de desempenho com base no Ano (9) filtrado e na metodologia desenvolvida pela Secretaria Estaudal de Meio Ambiente;

* 11 - Filtro de faixa de posição dos Munícipios que receberão recursos para obras de melhorias;
  
* 12 - Filtro de faixa de posição dos Munícipios que receberão recursos para novas obras;
  
* 13  - Lista de Municípios, e da sua respectiva posição de prioridade, que receberão recursos para obras de melhorias, com base no filtro (11);  

* 14 - Lista de Municípios, e da sua respectiva posição de prioridade, que receberão recursos para novas obras, com base no filtro (12).  


