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

## Contribuições

Contribuições são bem-vindas! Se você tiver sugestões de melhoria, novas análises ou identificar algum problema, sinta-se à vontade para abrir uma issue ou enviar um pull request.

---
