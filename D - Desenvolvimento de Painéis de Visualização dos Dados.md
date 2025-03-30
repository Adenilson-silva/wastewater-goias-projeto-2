# Uso de dados para otimizar a alocação de recursos públicos destinados ao saneamento básico de Goiás

### ADENILSON SILVA

 Para controle do fluxo de atividades do projeto, a consultoria utilizou o trello. O painel criado [aqui](https://trello.com/b/RIgkWLxE/projeto-uso-de-dados-para-otimizar-a-aloca%C3%A7%C3%A3o-de-recursos-p%C3%BAblicos-destinados-ao-saneamento-b%C3%A1sico-de-goi%C3%A1s).
 
## DESENVOLVIMENO DE PAINÉIS DE VISUALIZAÇÃO DOS DADOS

    "Para controle do fluxo de atividades do projeto, a consultoria utilizou o trello. Painel: [aqui](https://trello.com/b/RIgkWLxE/projeto-uso-de-dados-para-otimizar-a-aloca%C3%A7%C3%A3o-de-recursos-p%C3%BAblicos-destinados-ao-saneamento-b%C3%A1sico-de-goi%C3%A1s)."



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
https://app.powerbi.com/view?r=eyJrIjoiMGM1ZmFkNjgtOGU5Yy00YTdlLWJlOTYtYmI2OTg2YmNlOTkyIiwidCI6ImQ4YmRlNjVhLTNkZWQtNDM0Ni05NTE4LTY3MDIwNGU2ZTE4NCIsImMiOjR9


