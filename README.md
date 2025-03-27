# Análise, Engenharia e Visualização de Dados
##  Uso de dados para otimizar a alocação de recursos destinados ao saneamento básico de Goiás
<div align="center">
  <img src="https://drive.google.com/uc?export=view&id=1a98lYwnDTbwElQLKGG5bvBI0VYLEdx-x" width="500">
</div>

## Sobre este Projeto 
Os dados utilizados neste projeto são oficiais; no entanto, o cenário descrito na contextualização é fictício.

Este projeto é uma ramificação do projeto desenvolvido <a href="https://github.com/Adenilson-silva/wastewater-goias-projeto-1/tree/main" target="_blank"> Aqui </a>.

## Contextualização
Após a entrega dos resultados da <a href="https://github.com/Adenilson-silva/wastewater-goias-projeto-1/tree/main" target="_blank" target="_blank"> Análise Descritiva e Preditiva da Gestão de Esgotos em Goiás </a>, o governo decidiu que o estado proativamente destinaria recursos às prefeituras para melhoria dos sistemas de esgotamento sanitário dos municípios. Entretanto, o governo sabia que não seria possível destinar imediatamente recursos a todos os munícipios, pois isso dependeria do orçamento do estado. 

Em busca de uma solução, o governador soliciou que a Secretaria de Meio Ambiente do Estado desenvolvesse uma metodologia que permitisse definir quais os munícipios teriam prioridade no recebimento desses recursos. Vale destacar que os recursos seriam distribuídos em dois lotes: o primeiro voltado para novas obras e o segundo destinado à melhoria da infraestrutura existente.


Ademais, foi solicitada que a secretaria desenvolvesse alguma ferramenta que permitisse a consulta do atual situação de cada município.


#### Definição das responsabilidades
Ao tomar ciência da solicitação do governador, o secretário estadual de meio ambiente decidiu utilizar a  <a href="https://www.gov.br/transportes/pt-br/assuntos/portal-da-estrategia/artigos-gestao-estrategica/como-implementar-a-matriz-raci" target="_blank">Matriz RACI</a> para organizar a gestão de elaboração do estudo, definindo assim os papéis e responsabilidades das partes envolvidas. A seguir, é apresentada a matriz de inicio do projeto:
| Etapa  | Diagnóstico geral da situação do esgotamento sanitário em Goiás |
|-----------|-----------------------------------------------------------------------------------|
| **_Responsible_** | Será criado um Grupo de Trabalho (GT) composto por dois (2) analistas ambientais da Secretaria de Meio Ambiente do Estado, responsáveis pelo desenvolvimento do estudo. Este estudo utilizará como subsídio o projeto elaborado por uma empresa contratada por meio de licitação, especializada em consultoria de ciência de dados. A empresa será encarregada de estruturar e desenvolver um projeto que empregue técnicas de análise e modelagem de dados, com o intuito de embasar o estudo solicitado. O objetivo principal é transformar os dados coletados em informações concretas, que auxiliem na formulação de políticas públicas mais eficientes. |
| **_Accountable_**  | Secretário de Meio Ambiente do Estado de Goiás. |
| **_Consulted_** | Considerando a urgência na elaboração do estudo, os demais analistas ambientais da Secretaria poderão ser consultados para apoiar as atividades em desenvolvimento. Além disso, as secretarias municipais de Meio Ambiente estarão à disposição para colaborar no suporte e na execução do estudo. |
| **_Informed_**  | Governador, prefeitos e a população do estado de Goiás. |


#### Definição do fluxo de trabalho
Após definir as responsabilidades dos envolvidos, o secretario, juntamente com os analistas responsáveis pela elaboração do estudo, definiram o fluxo de trabalho por meio do <a href="https://medium.com/@gelsonm/pace-framework-a-beginners-guide-to-structured-ml-projects-7089b6001615" target="_blank">Método PACE</a>. A seguir, é apresentada a matriz:
| Etapa        | Descrição | Responsável | Prazo | Ações/Observações |
|--------------|-----------|-------------|-------|-------------------|
| **_Plan_**     | Planejamento e definição de metas e objetivos.  <a href="https://github.com/Adenilson-silva/wastewater-goias/blob/main/A%20-%20Coleta%20de%20dados.ipynb" target="_blank">Coleta dos dados</a>. | Analistas Ambientais e empresa de consultoria. | 5 dias | - |
| **_Analyse_**       |  <a href="https://github.com/Adenilson-silva/wastewater-goias/blob/main/B%20-%20Processamento%20e%20Tratamento%20dos%20Dados.ipynb" target="_blank">Processamento e tratamento dos dados</a>.  <a href="https://github.com/Adenilson-silva/wastewater-goias/blob/main/C%20-%20An%C3%A1lise%20e%20Explora%C3%A7%C3%A3o%20do%20Dados.ipynb" target="_blank">Análise exploratória dos dados.</a> | Empresa de consultoria. | 15 dias | Durante esta etapa, poderá ser necessária a solicitação de esclarecimentos pela empresa de consultoria. |
| **_Construct_**    |  <a href="https://github.com/Adenilson-silva/wastewater-goias/blob/main/D%20-%20Cria%C3%A7%C3%A3o%20de%20Modelos%20de%20Machine%20Learning.ipynb" target="_blank">Construção do modelo de _Machine Learning_</a>. | Empresa de consultoria. | 30 dias | - |
| **_Execute_**      | <a href="https://github.com/Adenilson-silva/wastewater-goias/blob/main/E%20-%20Conclus%C3%A3o.md" target="_blank">Entrega dos resultados</a>. | Analistas ambientais e empresa de consultoria. | 10 dias | Nesta etapa, os analistas ambientais deverão coletar o projeto entregue pela a empresa de consultoria e estruturar o estudo] |

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
| **O quê? (_What?_):** Quais os objetivos com essa análise?     | Este projeto realizará a análise descritiva e preditiva dos dados relativos ao volume de esgoto produzido, volume de esgoto tratado e volume de esgoto tratado em todos os 246 municípios do estado de Goiás.                    |
| **Por quê? (_Why?_):** Por que esse problema é importante?   | Dada a importância do assunto “saneamento básico”, este projeto motiva-se pela necessidade de verificar a efetividade das políticas públicas de tratamento de esgotos que estão sendo desenvolvidas no estado de Goiás.            |
| **Onde? (_Where?_):** Quais os aspectos geográficos e/ou logísticos?   | Este projeto tratará especificamente do estado de Goiás e seus municípios.                                                                                                                                                         |
| **Quando? (_When?_):** Qual o período está sendo analisado?   | Os dados utilizados neste projeto contemplarão a seguinte faixa de tempo: <br> • Análise Descritiva: do ano 1992 ao ano 2021; <br> • Análise Preditiva: do ano 2022 ao ano 2032.                                                 |

**Objetivos**
- Coletar e tratar dados relativos aos volumes de esgotos produzidos, coletados e tra-tados nos munícipios do estado de Goiás;
- Descrever os dados coletados, a fim de averiguar possíveis comportamentos e/ou tendências entre o período de 1992 a 2021;
- Prever comportamentos e/ou tendências futuras (para o período compreendido en-tre 2022 e 2032); e
- Constatar se, por meio de modelos preditivos, é possível inferir se a atual ação do poder público no estado de Goiás garantirá ou não a melhoria dos serviços de coleta e tratamento na região.


## Tecnologias utilizadas
- Python
- Trello


## Quem é o Autor?
Leia meu resumo e me envie uma mensagem: https://www.linkedin.com/in/adenilson-silva/

Vamos conversar...
