# Análise da Relação entre Acidentes Rodoviários e Radares no Brasil 

## Visão Geral

Este projeto de análise de dados explora a complexa relação entre a ocorrência de acidentes de trânsito nas rodovias federais brasileiras e o posicionamento dos radares de fiscalização. Utilizando dados públicos da Polícia Rodoviária Federal (PRF) e da Agência Nacional de Transportes Terrestres (ANTT), buscamos identificar padrões, zonas de alto risco e avaliar o potencial impacto dos radares na segurança viária. O objetivo final é gerar insights que possam subsidiar discussões e ações para tornar as estradas mais seguras e eficientes para todos.

## Problema de Negócio

A segurança no trânsito é um desafio constante nas rodovias brasileiras. Compreender os fatores que contribuem para os acidentes e avaliar a eficácia das medidas de prevenção, como a instalação de radares, é fundamental para a tomada de decisões estratégicas por parte dos órgãos responsáveis e concessionárias. Este projeto busca responder a perguntas como:

*   Onde ocorrem os acidentes mais graves?
*   Quais são as principais causas de acidentes em áreas com e sem radares?
*   Existem padrões temporais (horários, dias, meses) na ocorrência de acidentes?
*   Os radares estão posicionados nos locais de maior criticidade?

## Dados

Foram utilizados dois conjuntos de dados públicos:

1.  **Dados de Acidentes Rodoviários (PRF):** Obtidos da base pública da Polícia Rodoviária Federal (disponível em [https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf)), contendo registros detalhados de todos os acidentes ocorridos nas rodovias federais em 2023. As informações incluem: data, hora, UF, BR, KM, município, causa e tipo de acidente, classificação (com/sem vítimas, fatal), fase do dia, condições meteorológicas, tipo de pista, traçado, uso do solo, número de pessoas envolvidas (mortos, feridos, ilesos, ignorados), veículos envolvidos e coordenadas geográficas.

2.  **Dados de Radares (ANTT):** Obtidos do portal Dados.gov.br (disponível em [https://dados.gov.br/dados/conjuntos-dados/radar](https://dados.gov.br/dados/conjuntos-dados/radar)), fornecidos pela Agência Nacional de Transportes Terrestres (ANTT). Este conjunto de dados contém a localização, tipo, velocidade permitida (para veículos leves e pesados) e situação (ativo/inativo) dos radares nas rodovias federais.

## Metodologia

O projeto seguiu as seguintes etapas principais:

1.  **Entendimento do Problema e dos Dados:** Análise inicial dos requisitos de negócio e exploração da estrutura e conteúdo dos conjuntos de dados.
2.  **Coleta e Tratamento dos Dados:** Importação dos arquivos CSV, tratamento de valores ausentes, correção de formatos de dados (datas, horários, coordenadas, KM) e criação de colunas derivadas relevantes.
3.  **Análise Exploratória de Dados (EDA):**
    *   Visualização geográfica da distribuição de acidentes e radares utilizando `folium`.
    *   Análise da frequência de acidentes por rodovia e por categoria de gravidade.
    *   Exploração da distribuição de acidentes por mês e hora do dia.
    *   Análise da distribuição de variáveis categóricas importantes (tipo de acidente, causa, condições meteorológicas, etc.).
4.  **Identificação de Zonas de Alto Risco:** Agrupamento de acidentes por rodovia e quilômetro para identificar os trechos com maior concentração de acidentes graves.
5.  **Análise de Proximidade:** Cálculo da distância do acidente até o radar mais próximo utilizando `scipy.spatial.cKDTree` para determinar se a proximidade com radares influencia a frequência e as causas dos acidentes.
6.  **Análise Comparativa:** Comparação das características dos acidentes (causas, tipos, severidade) em áreas próximas e distantes de radares.
7.  ** analise temporal:** identificação de meses e horarios com o maior numero de acidentes
8.  **Conclusões e Insights:** Síntese dos principais achados da análise e formulação de insights relevantes para o problema de negócio.

## Estrutura do Projeto

O repositório contém os seguintes arquivos principais:

*   `Nome_do_Seu_Notebook.ipynb`: O notebook Jupyter contendo todo o código da análise, visualizações e explicações. (Recomendado renomear para algo descritivo como `analise_acidentes_radares.ipynb`)
*   `datatran2023.csv`: Arquivo com os dados de acidentes da PRF (ano 2023).
*   `dados_dos_radares (1).csv`: Arquivo com os dados de radares da ANTT. (Recomendado renomear para algo mais simples como `dados_radares.csv`)
*   `README.md`: Este arquivo.

## Tecnologias Utilizadas

*   Python 3.x
*   Pandas: Manipulação e análise de dados.
*   NumPy: Suporte a operações numéricas.
*   Matplotlib: Geração de gráficos estáticos.
*   Seaborn: Visualizações estatísticas mais atraentes.
*   Folium: Criação de mapas interativos.
*   SciPy: Funções científicas e técnicas (utilizado para `cKDTree`).
*   Jupyter Notebook: Ambiente interativo para desenvolvimento e apresentação.

## Insights
<img width="1489" height="590" alt="image" src="https://github.com/user-attachments/assets/3b054772-10e5-4d5d-9b1d-5cc7a3bf8d4f" />
* A partir do gráfico, fica clara a necessidade de uma analise mais precisa sobre as rodovias BR-101 e BR-116, onde vem ocorrendo diversos acidentes e com pouco ou nenhum radar na regiao. Os quilômetros exatos, como "km-66", "km-68", "km-229" e "km-212", também são indicativos de áreas específicas propensas a acidentes.

* 115 rodovias federais têm registros de acidentes na base de dados analisada.

* A BR-101 é a rodovia com o maior número de registros de acidentes, totalizando 11.634 registros.

* A quantidade de acidentes registrados nas BR-101 e BR-116 representa 33,11% do total de acidentes.

* Dentre essas rodovias, os motivos mais presentes são: acessar a via sem observar a presença de outro condutor e reação tardia ou ineficiente do condutor.

* Necessidade de Fiscalização: a ausência de radares em muitos trechos críticos destaca a necessidade de medidas de fiscalização e controle de velocidade nessas áreas, para reduzir o número de acidentes com vítimas.

* Os acidentes com vítimas representam 76,7%; os acidentes sem vítimas, 14%; e os acidentes com vítimas fatais, 7,2%.

* 42.754 acidentes ocorrem a menos de 1 km de um radar.

* Em média, os acidentes ocorrem a 2,56 km de distância de um radar.

* Os motivos que mais causam acidentes a menos de 1 km de um radar são:

* Reação tardia ou ineficiente do condutor: 7.002 ocorrências

* Ausência de reação do condutor: 6.479 ocorrências

* Acessar a via sem observar a presença dos outros veículos: 3.688 ocorrências

* Velocidade incompatível: 3.101 ocorrências

* Apesar de uma grande quantidade de acidentes ocorrer a menos de 1 km de um radar, as principais causas nesses locais parecem estar mais relacionadas a falhas humanas na reação ou atenção, e não diretamente à velocidade incompatível, embora esta última ainda seja uma causa relevante. Isso pode indicar que a presença do radar influencia a velocidade, mas outros fatores de comportamento do motorista ainda contribuem para acidentes próximos.

* Em acidentes distantes de radares, há uma proporção maior de ocorrências com vítimas fatais, podendo estar relacionado com a velocidade.

* Em acidentes próximos a radares, “Dupla” é o tipo mais comum; enquanto em acidentes distantes, “Simples” lidera.

* A regional SPRF-MG é a mais comum em acidentes próximos a radares, enquanto a SPRF-BA lidera em acidentes distantes.

* MG, SC, PR, RJ, RS e SP são os estados com maior número de acidentes.

* Colisão traseira, saída do leito carroçável e colisão transversal são os tipos mais frequentes de acidentes em geral.

* A maior parte dos acidentes ocorre durante o dia e com céu claro.

* As principais causas de acidentes nas rodovias envolvem falhas humanas.

* durante o ano, o maior numero de acidentes ocorreu no mes de dezembro

* o maior numero de acidentes ocorre entre as 5 e 10 da manha e entre as 15 e 20 horas, principalmente as 7 horas e as 18 horas. esses horarios estao ligados com os famosos 'horarios de pico' nas cidades.




---
