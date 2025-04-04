# Análise, Engenharia e Visualização de Dados
##  Uso de dados para otimizar a alocação de recursos públicos destinados ao saneamento básico de Goiás
<div align="center">
  <img src="https://drive.google.com/uc?export=view&id=1a98lYwnDTbwElQLKGG5bvBI0VYLEdx-x" width="500">
</div>

## Sobre este Projeto 
Os dados utilizados neste projeto são oficiais; no entanto, o cenário descrito na contextualização é fictício.

Este projeto é uma ramificação do projeto desenvolvido <a href="https://github.com/Adenilson-silva/wastewater-goias-projeto-1/tree/main" target="_blank">aqui</a>.

## Contextualização
Após a entrega dos <a href="https://github.com/Adenilson-silva/wastewater-goias-projeto-1/blob/main/E%20-%20Resultados.md" target="_blank">resultados da Análise Descritiva e Preditiva da Gestão de Esgotos em Goiás </a>, o governo decidiu que o estado proativamente destinaria recursos às prefeituras para melhoria dos sistemas de esgotamento sanitário dos municípios. Entretanto, o governo sabia que não seria possível destinar imediatamente recursos a todos os munícipios, pois isso dependeria do orçamento do estado. 

Em busca de uma solução, o governador soliciou que a Secretaria de Meio Ambiente do Estado desenvolvesse uma metodologia que permitisse definir quais os munícipios teriam prioridade no recebimento desses recursos. Vale destacar que os recursos seriam distribuídos em dois lotes: o primeiro voltado para novas obras e o segundo destinado à melhoria da infraestrutura existente.


Ademais, foi solicitado que a secretaria desenvolvesse alguma ferramenta que permitisse a consulta situacional e histórica de cada município.


#### Definição das responsabilidades
Ao tomar ciência da demanda do governador, o secretário estadual de meio ambiente decidiu novamente utilizar a  <a href="https://www.gov.br/transportes/pt-br/assuntos/portal-da-estrategia/artigos-gestao-estrategica/como-implementar-a-matriz-raci" target="_blank">Matriz RACI</a> para organizar a gestão de elaboração do projeto, definindo assim os papéis e responsabilidades das partes envolvidas. Ademais, o secretário optou por utilizar o dados coletados no projeto anterior para embasar o desenvolvimento da metodologia de priorização. A seguir, é apresentada a matriz de inicio do projeto:
| Etapa  | Detalhamento |
|-----------|-----------------------------------------------------------------------------------|
| **_Responsible_** | Será criado um Grupo de Trabalho (GT) composto por dois (2) analistas ambientais da Secretaria de Meio Ambiente do Estado, responsáveis pelo desenvolvimento do projeto. Este projeto será desenvolvindo em conjunto com uma empresa contratada por meio de licitação, especializada em consultoria de ciência de dados. O objetivo principal é transformar os dados coletados em informações concretas.
| **_Accountable_**  | Secretário de Meio Ambiente do Estado de Goiás. |
| **_Consulted_** | Considerando a urgência na elaboração do estudo, os demais analistas ambientais da Secretaria poderão ser consultados para apoiar as atividades em desenvolvimento. Além disso, as secretarias municipais de Meio Ambiente estarão à disposição para colaborar no suporte e na execução do estudo. |
| **_Informed_**  | Governador, prefeitos e a população do estado de Goiás. |


#### Definição do fluxo de trabalho
Após definir as responsabilidades dos envolvidos, o secretario, juntamente com os analistas responsáveis pela elaboração do estudo, definiram o fluxo de trabalho por meio do <a href="https://medium.com/@gelsonm/pace-framework-a-beginners-guide-to-structured-ml-projects-7089b6001615" target="_blank">Método PACE</a>. A seguir, é apresentada a matriz:
| Etapa        | Descrição | Responsável | Prazo | Ações/Observações |
|--------------|-----------|-------------|-------|-------------------|
| **_Plan_**     | Planejamento e definição de metas e objetivos, além da definição da metodologia de priorização. | Analistas Ambientais | 25 dias | - |
| **_Analyse_**       | Processo de ETL (<a href="https://github.com/Adenilson-silva/wastewater-goias-projeto-2/blob/main/A%20-%20Extract.ipynb" target="_blank">_Extract_</a>, <a href="https://github.com/Adenilson-silva/wastewater-goias-projeto-2/blob/main/B%20-%20Transform.ipynb" target="_blank">_Transform_</a>, <a href="https://github.com/Adenilson-silva/wastewater-goias-projeto-2/blob/main/C%20-%20Load.ipynb" target="_blank">_Load_</a>) dos dados.  | Empresa de consultoria. | 25 dias | Durante esta etapa, poderá ser necessária a solicitação de esclarecimentos pela empresa de consultoria. |
| **_Construct_**    |  <a href="https://github.com/Adenilson-silva/wastewater-goias-projeto-2/blob/main/D%20-%20Desenvolvimento%20de%20Pain%C3%A9is%20de%20Visualiza%C3%A7%C3%A3o%20dos%20Dados.md" target="_blank"> Desenvolvimento de ferramenta que permita a consulta situacional e histórica de cada município</a>. | Empresa de consultoria. | 20 dias | - |
| **_Execute_**      | <a href="" target="_blank">Entrega dos resultados</a>. | Analistas ambientais e empresa de consultoria. | 10 dias | - |

#### Empresa de Consultoria ganhadora da licitação
Após a conclusão do processo licitatório, a empresa vencedora foi *O que dizem os Dados?*.

De acordo com a própria empresa:

<div align="center">
  <img src="https://drive.google.com/uc?export=view&id=1Hs-6FGRgBtCslkh9GsRE5cdtblEB_ENe"  width="300">
</div>

###### Quem Somos
*O que dizem os Dados?* é uma empresa de consultoria em ciência de dados que transforma informações em *insights* estratégicos. Oferecemos soluções como análise preditiva, modelagem estatística, inteligência artificial, visualização de dados e otimização de processos. Nosso foco é ajudar empresas a tomar decisões mais assertivas com base em dados, impulsionando eficiência e inovação.

#### Definição do problema e dos objetivos
Durante as reuniões de planejamento entre os analistas ambientais e a empresa de consultoria, ficou estabelecido que, para garantir uma compreensão clara e objetiva do projeto, seria utilizada a técnica [5W-S](https://www.esalq.usp.br/qualidade/ferramentas/5w1h.htm). Essa abordagem permitiria estruturar a descrição do problema de forma detalhada. A seguir, é apresentada a aplicação da técnica e os objetivos, respectivamente.
| **Pergunta**           | **Descrição**                                                                                                                                                                                                                       |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Quem? (_Who?_):** De quem são os dados analisados?      | Os dados utilizados neste projeto serão coletados de 3 fontes distintas: <br> 1 – Sistema Nacional de Informações sobre o Saneamento (SNIS) <br> 2 – Instituto Brasileiro de Geografia e Estatística (IBGE)<br> 3 – Instituto Mauro Borges de Estatísticas e Estudos Socioeconômicos (IMB) |
| **O quê? (_What?_):** Quais os objetivos com essa análise?     | Desenvolver uma metodologia, baseada em dados, que possa criar critérios de priorização. Desenvolver alguma ferramenta que permita a consulta da atual situação de cada município.                    |
| **Por quê? (_Why?_):** Por que esse problema é importante?   | Considerando que o estado não possui recursos suficientes para ser destinado a todos os municipios, é necessário estabelecer critérios objetivos de prioridade.            |
| **Onde? (_Where?_):** Quais os aspectos geográficos e/ou logísticos?   | Este projeto tratará especificamente do estado de Goiás e seus municípios.                                                                                                                                                         |
| **Quando? (_When?_):** Qual o período está sendo analisado?   | Os dados utilizados neste projeto contemplarão o ano de 2021, ou seja, os últimos dados coletados de cada município.                                                  |

**Objetivos**
- Com base nos dados, desenvolver metodologia de priorização.
- Desenvolver ferramenta que permita a consulta situacional e histórica de cada município.


### Metodologia de Priorização

Após intenso debate, a secretaria desenvolveu a seguinte metodologia para definir quais os municípios teriam prioridade no recebimento de recursos:

* **Para novas obras**

Com base no ano de 2021, os municípios com a menor relação entre o volume de esgotos tratado e o volume de esgotos coletado (RTC) terão maior prioridade.
<p align="center"><b>RTC = volume tratado / volume produzido</b></p>

O primeiro critério de desempate, caso haja, será a menor relação entre o volume de esgotos coletado e o volume de esgotos produzido (RCP).
<p align="center"><b>RCP = volume coletado / volume produzido</b></p>

O segundo critério de desempate, caso haja, será a menor relação entre o volume de esgotos tratado e o volume de esgotos produzido (RTP).
<p align="center"><b>RTP = volume tratado / volume produzido</b></p>

O terceiro critério de desempate, caso haja, será o maior número de habitantes.


* **Para melhoria da infraestrutura**

Com base no ano de 2021, os municípios com a menor relação entre o volume de esgotos coletados e o volume de esgotos produzidos (RCP) terão maior prioridade.
<p align="center"><b>RCP = volume coletado / volume produzido</b></p>

O primeiro critério de desempate, caso haja, será a menor relação entre o volume de esgotos tratado e o volume de esgotos produzido (RTP).
<p align="center"><b>RTP = volume tratado / volume produzido</b></p>

O segundo critério de desempate, caso haja, será a menor relação entre o volume de esgotos tratado e o volume de esgotos coletado (RTC).
<p align="center"><b>RTC = volume tratado / volume produzido</b></p>

O terceiro critério de desempate, caso haja, será o maior número de habitantes.

Esta metodologia poderá ser revista conforme a secretaria julgue necessário.

### Ferramenta de consulta situacional e histórica de cada município

Para que fosse possível atender ao pedido de criação de ferramenta de consulta situacional e histórica de cada município, a secretaria solicitou que a empresa de consultoria desenvolvesse um painel. Nesse painel deveria conter minimamente os seguintes elementos:

- Gráficos que monstrassem a evolução histórica de cada município.
- Informação acerca da taxa de tratamento e coleta de esgotos.
- Classificação do desempenho anual de cada município, considerando o cálculo do coeficiente de desempenho (CD).
   <p align="center"><b>CD = ((3*RTP) + (2*RTC) + (RCP)) / 6</b></p>

   Onde:

<table align="center">
  <tr>
    <th style="text-align:center;">Classificação</th>
    <th style="text-align:center;">Condição de CD</th>
    <th style="text-align:center;">Número de Habitantes</th>
  </tr>
  <tr>
    <td style="text-align:center;"><b>Ruim</b></td>
    <td style="text-align:center;">Menor que 0.25</td>
    <td style="text-align:center;">Maior que 0</td>
  </tr>
  <tr>
    <td style="text-align:center;"><b>Regular</b></td>
    <td style="text-align:center;">Entre 0.25 e 0.5</td>
    <td style="text-align:center;">Maior que 0</td>
  </tr>
  <tr>
    <td style="text-align:center;"><b>Bom</b></td>
    <td style="text-align:center;">Entre 0.5 e 0.75</td>
    <td style="text-align:center;">Maior que 0</td>
  </tr>
  <tr>
    <td style="text-align:center;"><b>Ótimo</b></td>
    <td style="text-align:center;">Igual ou maior que 0.75</td>
    <td style="text-align:center;">Maior que 0</td>
  </tr>
  <tr>
    <td style="text-align:center;"><b>Indefinido</b></td>
    <td style="text-align:center;">-</td>
    <td style="text-align:center;">Igual a 0 (município ainda não criado)</td>
  </tr>
</table>


Este critério de classificação também poderá ser revisto conforme a secretaria julgue necessário.

Além dos dados relativos à situação de cada munícipio, também deverá ser desenvolvido um painel para apresentação dos dados relativos à priorização do munícipios no que tange o recebimento de recursos.

## Tecnologias utilizadas
- Python
- PostgreSQL
- PowerBI
- Trello


## Quem é o Autor?
Leia meu resumo e me envie uma mensagem: https://www.linkedin.com/in/adenilson-silva/

Vamos conversar...
