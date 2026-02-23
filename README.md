# Desigualdade no saneamento básico e impactos em educação e saúde no Brasil

Análise exploratória da relação entre saneamento básico, frequência escolar e disponibilidade de médicos por estado no Brasil, utilizando dados públicos do IBGE e visualização no Looker Studio.

Projeto desenvolvido de forma individual e organizado como parte do meu portfólio para atuação como Analista de Dados Pleno.

---

## 1. Problema e contexto

O acesso ao saneamento básico no Brasil ainda apresenta desigualdades significativas entre estados e regiões, afetando diretamente a qualidade de vida e o desenvolvimento social.  
Neste projeto, investigo se estados com melhor infraestrutura de saneamento básico apresentam também:

- maior frequência escolar;
- maior oferta de médicos por habitante.

**Pergunta central:**

> Como o acesso ao saneamento básico se relaciona com indicadores de educação (frequência escolar) e saúde (médicos por habitante) nos estados brasileiros?

Este tipo de análise pode apoiar decisões de políticas públicas e priorização de investimentos em infraestrutura, educação e saúde.

---

## 2. Dados utilizados

Os dados foram obtidos de bases públicas do **IBGE** e disponibilizados em formato CSV.

Principais arquivos de dados:

- `AbastAgua.csv`: percentuais de acesso a diferentes formas de abastecimento de água por estado.
- `DestLixo.csv`: percentuais de coleta de lixo por serviço de limpeza e outros destinos.
- `Esgoto.csv`: percentuais de acesso à rede geral de esgoto e demais formas de escoamento.
- `SaneamentoBasico.csv`: percentual da população com acesso simultâneo a água, esgoto e coleta de lixo (saneamento básico integrado).
- `Frequenciaescolar.csv`: frequência escolar por faixa etária (6–10, 11–14, 15–17, 18–24 anos).
- `medicoestado.csv`: número de médicos por 10.000 habitantes por estado (2010–2023).
- `Censodemografico2022.csv`: população total por município/UF (Censo Demográfico 2022).

Ferramentas e stack técnica:

- **Linguagem:** Python 3  
- **Principais bibliotecas:** `pandas`, `matplotlib`, `seaborn`  
- **Visualização interativa:** Google Looker Studio  

---

## 3. Metodologia

### 3.1. Preparação e limpeza dos dados

No notebook principal foram realizados os seguintes passos:

- Leitura dos arquivos CSV com `pandas` (água, lixo, esgoto, saneamento, frequência escolar, médicos, censo).
- Padronização da coluna de identificação dos estados (por exemplo, `Estados e Capitais` / `Estados` / `UF`).
- Verificação e tratamento de valores nulos com `fillna(0)` em colunas percentuais e numéricas.
- Ajustes de tipos de dados (`int64`, `float64`, `object`) para permitir cálculos e junções.
- Limpeza do Censo 2022, removendo colunas de códigos e mantendo apenas UF, município e população total.

### 3.2. Integração e criação de indicadores

Com os dados limpos, foram realizadas integrações e cálculos:

- Filtragem apenas dos **estados brasileiros**, removendo linhas de capitais quando necessário.
- Ordenação de estados por:
  - maior/menor acesso à rede de distribuição de água;
  - maior/menor coleta de lixo por serviço de limpeza;
  - maior/menor cobertura de rede de esgoto;
  - maior/menor acesso ao saneamento básico integrado.
- Criação de um dataset integrado com:
  - `Rede de distribuição` (água tratada);
  - `Coletado diretamente por serviço de limpeza`;
  - `Rede geral` (esgoto);
  - `Acesso ao saneamento básico`.
- Cálculo da **matriz de correlação** entre essas variáveis de infraestrutura.
- Junção dos indicadores de saneamento com:
  - frequência escolar média (a partir das faixas etárias);
  - número de médicos por 10.000 habitantes (ano de 2023);
  - população total por estado.

### 3.3. Análises exploratórias

As principais análises exploratórias conduzidas foram:

1. **Rankings por infraestrutura**
   - Estados com maior e menor acesso à água tratada.
   - Estados com maior e menor coleta de lixo por serviço de limpeza.
   - Estados com maior e menor cobertura de rede de esgoto.
   - Estados com maior e menor acesso ao saneamento básico integrado.

2. **Integração de infraestrutura**
   - Identificação dos estados com melhor e pior combinação simultânea de água, lixo, esgoto e saneamento básico.

3. **Correlação entre variáveis**
   - Correlação entre variáveis de infraestrutura (água, lixo, esgoto, saneamento básico integrado).
   - Correlação entre saneamento básico e frequência escolar média.
   - Correlação entre saneamento básico e médicos por 10.000 habitantes.
   - Correlação entre saneamento básico e população total.

4. **Visualizações**
   - Heatmap de correlação entre água, lixo, esgoto e saneamento básico.
   - Gráficos para destacar estados com maior e menor infraestrutura.
   - Visualizações interativas no dashboard (Looker Studio).

---

## 4. Principais insights

Alguns resultados relevantes da análise:

- **Forte desigualdade regional**
  - Estados do Sudeste, especialmente São Paulo, apresentam os melhores índices de saneamento básico integrado (acesso simultâneo a água, lixo e esgoto).
  - Estados do Norte e Nordeste concentram os piores indicadores de saneamento básico.

- **Esgoto é o maior gargalo**
  - A cobertura de rede de esgoto é o serviço com maior disparidade.
  - Alguns estados têm coberturas muito baixas, enquanto outros superam 90%.

- **Associação com saúde e educação**
  - Correlação positiva entre acesso ao saneamento básico e número de médicos por habitante.
  - Correlação positiva entre saneamento básico e frequência escolar média.
  - Correlação positiva entre saneamento básico e população total, sugerindo que regiões com melhor infraestrutura tendem a atrair e reter mais pessoas.

Esses resultados indicam que a infraestrutura de saneamento básico está fortemente associada a melhores indicadores de educação e saúde.

---

## 5. Conclusões e recomendações

- Saneamento básico funciona como um **fator estruturante** para outros indicadores sociais, como educação e saúde.
- A desigualdade entre estados reforça a necessidade de:
  - investimentos prioritários em infraestrutura nas regiões com menor acesso;
  - políticas integradas entre saneamento, saúde e educação;
  - incentivos para atração e retenção de médicos e professores em áreas com baixa infraestrutura.

Do ponto de vista de análise de dados, o projeto demonstra:

- capacidade de trabalhar com múltiplas fontes de dados públicas;
- integração de bases heterogêneas (saneamento, educação, saúde, demografia);
- exploração de correlações e geração de insights acionáveis para políticas públicas.

---

## 6. Dashboard no Looker Studio

Os resultados foram sintetizados em um painel interativo, permitindo explorar os indicadores por estado e região:

🔗 [Dashboard no Looker Studio](https://lookerstudio.google.com/reporting/0413c8a2-9c37-4620-b5a1-fe45e82776a9)

---

## 7. Estrutura sugerida do repositório

Exemplo de organização de pastas e arquivos:

```bash
.
├── data/
│   ├── raw/          # CSVs originais do IBGE
│   └── processed/    # Dados tratados e agregados (opcional)
├── notebooks/
│   └── eda_saneamento_escola_medicos.ipynb
├── reports/
│   └── relatorio_insights_saneamento.pdf
└── README.md
8. Sobre o projeto
Projeto desenvolvido de forma individual, baseado em dados públicos e com foco em análise exploratória, integração de múltiplas fontes e comunicação de insights por meio de visualizações e dashboard, visando atuação como Analista de Dados Pleno.

text
undefined
vamos para a segunda analise, parte da ultima tarefa da escola, transforme em um portifolio profissional seguindo os mesmos passsos acima. segue informações da tarefa: EBAC – Curso Profissão Analista de Dados
Aluna: Vivian Aline Inoue
 
Tarefa – Módulo 40
1.      Conjunto de dados:
Conjunto de dados escolhidos: IMT KAGGLE TEAM. Mental Health Dataset. Kaggle, 2022. Disponível em: https://www.kaggle.com/datasets/imtkaggleteam/mental-health.
Tabelas usadas:
·         1-mental-illnesses-prevalence
·         2-burden-disease-from-mental-illness
·         5-anxiety-disorders-treatment-gap
·         6-depressive-symptoms-across-us-population
 
2.      Análises exploratórias:
 
a)      Identificar os países com maior prevalência de transtornos mentais
b)      Observar se há crescimento ou redução ao longo dos anos da prevalência de transtornos mentais
c)      Ver quais países tem maior negligência no tratamento para transtorno de ansiedade
d)      Ver a correlação entre a prevalência de transtornos mentais e o impacto da doença mental (DALYs)
e)      Identificar países com o impacto desproporcional da doença mental (DALYs)
f)       Identificar quais sintomas depressivos são mais persistentes e quais são mais esporádicos na população dos Estados Unidos
g)      Ver quais sintomas depressivos tem maior impacto geral
h)      Identificar falhas em países com alta demanda de transtornos mentais e com baixa resposta no tratamento
 
3.      Tratamento e Preparação dos Dados:
https://colab.research.google.com/drive/1hhnlFcV1xUwMoidduKqMWpkbXhL00Tfc?usp=sharing
4.      Visualização de Dados:
https://lookerstudio.google.com/reporting/78f4f128-0fe4-4771-9ead-d83c26a265d9
 
 
5.      Relatório com os principais insights na análise exploratória: Saúde Mental Global
            Este relatório apresenta uma análise dos dados globais de saúde mental, com o objetivo de identificar padrões, desigualdade e áreas com prioridade de intervenção. A análise se concentrou na prevalência de transtornos mentais, seu impacto na sociedade, o acesso ao tratamento de ansiedade e os sintomas mais comuns da depressão.
Prevalência Global de Transtornos Mentais
            Nossa análise revela os países com maior prevalência de transtornos mentais. Países como Portugal, Brasil e EUA se destacam, com taxas acima de 14%, bem acima da média global de 10,2%. Essa concentração de casos indica a necessidade de atenção especial a esses países. Os transtornos mais comuns são a ansiedade (3,8%) e a depressão (3,4%), seguidos pela bipolaridade e esquizofrenia.
Evolução ao Longo dos Anos
A prevalência global de transtornos mentais se manteve relativamente estável entre 1990 e 2019, com pequenas oscilações. No entanto, notamos um crescimento leve e consistente nos casos de ansiedade e depressão, enquanto transtornos como a esquizofrenia mantiveram-se mais constante. Isso sugere que fatores sociais e ambientais podem estar contribuindo para o aumento desses transtornos específicos, como atentados terroristas (Torres Gêmeas 11/09/2001) e crise mundial financeira (2008).
Carga Global da Doença Mental (DALY)
O DALY (Disability-Adjusted Life Years) é uma medida que revela o impacto real dos transtornos mentais, quantificando os anos de vida perdidos devido à incapacidade ou morte prematura. Existe uma correlação positiva entre prevalência e DALY, ou seja, quanto mais casos, maior o impacto na sociedade.
Países como Mongólia, Japão e Singapura apresentam um impacto desproporcional, com altos DALYs apesar de uma prevalência moderada. A relação DALY/prevalência nesses locais é um indicador importante de que, mesmo com menos casos, o sofrimento por pessoa afetada é mais intenso.
Acesso ao Tratamento de Ansiedade
A ansiedade como vimos na prevalência de transtornos mentais, é o distúrbio mais comum em escala global. Naturalmente, o acesso ao tratamento e o nível de conscientização sobre a condição deveriam ser proporcionais a essa alta incidência. Porém, os dados revelam uma lacuna significativa entre a necessidade de cuidado e a realidade enfrentada. Países como México e Brasil, apresentam taxas elevadas de ansiedade, também apresentam índices elevados de pessoas que não recebem tratamento. Embora o número de casos tratados esteja crescendo, essa evolução é lenta e não acompanha o ritmo de crescimento dos transtornos. O cenário evidencia não apenas uma falha estrutural nos sistemas de saúde, mas também a urgência de políticas públicas que ampliem o alcance e a efetividade do cuidado em saúde mental.
Sintomas Depressivos nos Estados Unidos
            A depressão segue em segundo lugar dos transtornos mais comuns, essa análise é em cima dos sintomas mais presentes da depressão nos Estados Unidos. Observamos que os mais relatados são a baixa energia (21,5%), problemas de sono (19,1%) e a perda de interesse (16,5%). Embora sintomas graves como o pensamento suicida apareçam em menor proporção (2,9%), eles são extremamente críticos e exigem atenção. A frequência dos sintomas também varia, com a baixa energia e os problemas de sono sendo mais persistentes.
Conclusão
É possível concluir que o cenário atual é marcado por complexidade, desigualdade e urgência. A depressão se destaca como o transtorno de maior impacto, tanto em prevalência quanto em anos de vida perdidos por incapacidade (DALYs), exigindo atenção prioritária em políticas públicas e alocação de recursos. Ao mesmo tempo, os dados revelam lacunas alarmantes no acesso ao tratamento, especialmente em países de baixa e média renda, onde a cobertura é insuficiente ou inexistente.
A análise também mostra padrões geográficos muito claros: países desenvolvidos tendem a apresentar maior prevalência, mas contam com sistemas de saúde mais estruturados e maior acesso ao cuidado. Já países em desenvolvimento enfrentam não apenas limitações de infraestrutura, mas também a desinformação sobre o assunto, que dificulta qualquer ação eficaz. O impacto desproporcional observado em países como Mongólia, Singapura e Japão levanta questões importantes sobre os fatores culturais, sociais e estruturais que influenciam a severidade dos transtornos mentais, apontando para a necessidade de investigações mais profundas e soluções contextualizadas.
Diante de tudo isso, fica claro que a saúde mental é um desafio global que exige estratégias integradas, sensíveis às realidades locais e comprometidas com a redução das desigualdades. A ampliação do acesso ao tratamento, o monitoramento contínuo dos indicadores, a promoção de campanhas de conscientização e o uso estratégico dos dados de DALY para priorizar ações são passos fundamentais para transformar esse cenário. Ao agir com base em evidências e com foco na equidade, é possível avançar rumo a uma saúde mental mais acessível, eficaz e humana para todos.

4 anexos
Vou manter o mesmo padrão do primeiro projeto e já te entregar um texto pronto de portfólio para colar no README de um repositório novo, usando esses 4 CSVs e os links que você passou.

A seguir está o conteúdo limpo em Markdown para você usar direto como README.md (sem nada de [file:...]):

text
# Saúde Mental Global: prevalência, carga de doença e lacunas de tratamento

Análise exploratória de dados globais de saúde mental (prevalência, carga de doença em DALYs, tratamento de ansiedade e sintomas depressivos nos EUA), com foco em identificar padrões, desigualdades e prioridades de intervenção.

Projeto desenvolvido de forma individual e organizado como parte do meu portfólio para atuação como Analista de Dados Pleno.

---

## 1. Problema e contexto

Transtornos mentais estão entre as principais causas de perda de qualidade de vida no mundo, mas a resposta em termos de acesso a tratamento e políticas públicas ainda é desigual entre países e grupos populacionais.  
Este projeto investiga:

- quais países apresentam maior prevalência de transtornos mentais;
- como essa prevalência evolui ao longo do tempo;
- como essa prevalência se relaciona com a carga da doença (DALYs);
- onde estão as maiores lacunas de tratamento (treatment gap) para transtornos de ansiedade;
- quais sintomas depressivos são mais frequentes e persistentes na população dos Estados Unidos.

**Perguntas centrais:**

> 1. Quais países concentram maior prevalência de transtornos mentais e maior carga de doença (DALYs)?  
> 2. Onde há maior negligência no tratamento de ansiedade, dado o tamanho do problema?  
> 3. Quais sintomas depressivos têm maior impacto na população dos Estados Unidos?

---

## 2. Dados utilizados

Conjunto de dados base: **Mental Health Dataset – IMT Kaggle Team (Kaggle, 2022)**.  
Link: https://www.kaggle.com/datasets/imtkaggleteam/mental-health

Tabelas utilizadas neste projeto:

- `1-mental-illnesses-prevalence.csv`  
  - Prevalência, por país e ano, de:
    - esquizofrenia  
    - depressão  
    - ansiedade  
    - transtorno bipolar  
    - transtornos alimentares  

- `2-burden-disease-from-mental-illness.csv`  
  - Taxas de DALYs (Disability-Adjusted Life Years) por 100 mil habitantes, por país e ano, para:
    - depressão  
    - esquizofrenia  
    - transtorno bipolar  
    - transtornos alimentares  
    - ansiedade  

- `5-anxiety-disorders-treatment-gap.csv`  
  - Lacuna de tratamento para transtornos de ansiedade (treatment gap), por país:
    - percentual de pessoas com transtorno de ansiedade que **não recebem tratamento**.

- `6-depressive-symptoms-across-us-population.csv`  
  - Sintomas depressivos autorrelatados na população dos Estados Unidos:
    - tipos de sintoma (baixa energia, problemas de sono, perda de interesse, ideação suicida etc.);
    - frequência / intensidade.

Ferramentas e stack técnica:

- **Linguagem:** Python 3 (Google Colab)  
- **Principais bibliotecas:** `pandas`, `numpy`, `matplotlib`, `seaborn`  
- **Visualização interativa:** Google Looker Studio  

Notebooks e código de tratamento de dados:  
- Colab: `Tratamento e Preparação de Dados`  
  - https://colab.research.google.com/drive/1hhnlFcV1xUwMoidduKqMWpkbXhL00Tfc?usp=sharing

---

## 3. Metodologia

A análise foi estruturada em quatro blocos principais:

### 3.1. Prevalência global de transtornos mentais

- Leitura da tabela de prevalência global de transtornos mentais por país e ano.  
- Cálculo da prevalência total de transtornos mentais por país (somando ou combinando as principais categorias: ansiedade, depressão, bipolaridade, esquizofrenia, alimentares).  
- Seleção dos países com maior prevalência média no período recente (por exemplo, 2017–2019).  
- Análises específicas:
  - países com maior prevalência total (Portugal, Brasil, EUA com taxas acima de ~14%, frente a uma média global em torno de 10,2%);
  - prevalência por tipo de transtorno (ansiedade, depressão, bipolaridade, esquizofrenia, alimentares);
  - evolução temporal (1990–2019) para observar tendência de crescimento ou estabilidade.

### 3.2. Carga de doença (DALYs) e impacto desproporcional

- Leitura da tabela de DALYs para transtornos mentais por país e ano.  
- Cálculo de indicadores agregados, como:
  - DALYs por 100 mil habitantes para depressão, ansiedade e transtornos mentais em geral;
  - média de DALYs no período analisado.  
- Cálculo da relação **DALYs / prevalência**, para identificar países onde:
  - a prevalência não é tão alta, mas o impacto (anos de vida perdidos por incapacidade) é elevado;
  - esses países são casos de **impacto desproporcional**, como Mongólia, Japão e Singapura.

### 3.3. Lacuna de tratamento em transtornos de ansiedade

- Leitura das taxas de **treatment gap** para transtornos de ansiedade.  
- Junção com a tabela de prevalência de ansiedade para cada país.  
- Identificação de países onde:
  - a prevalência de ansiedade é alta;
  - a proporção de pessoas sem tratamento também é alta
  - com destaque para casos como México e Brasil.  
- Análise da evolução temporal (quando disponível) para verificar se:
  - o número de pessoas tratadas está crescendo;
  - o ritmo de crescimento dos casos é maior do que o aumento do acesso ao tratamento.

### 3.4. Sintomas depressivos na população dos EUA

- Leitura da tabela de sintomas depressivos nos EUA.  
- Cálculo da frequência relativa de cada sintoma:
  - baixa energia  
  - problemas de sono  
  - perda de interesse  
  - dificuldade de concentração  
  - ideação suicida, entre outros.  
- Avaliação de:
  - quais sintomas são mais comuns;
  - quais parecem ser mais persistentes (presentes com maior frequência ou intensidade);
  - quais, mesmo aparecendo em menor proporção (como pensamento suicida), têm alta criticidade.

---

## 4. Principais insights

### 4.1. Prevalência global e países em destaque

- Países como **Portugal, Brasil e Estados Unidos** se destacam com prevalências de transtornos mentais acima de 14%, consideravelmente superiores à média global (~10,2%).  
- Os transtornos mais prevalentes são:
  - **ansiedade** (~3,8%);
  - **depressão** (~3,4%);
  - seguidos por transtorno bipolar e esquizofrenia, com prevalência menor, mas alto impacto individual.

### 4.2. Evolução ao longo do tempo (1990–2019)

- A prevalência global de transtornos mentais se manteve relativamente estável, com pequenas oscilações ao longo dos anos.  
- Observa-se, porém, um **crescimento gradual** nos casos de:
  - ansiedade;  
  - depressão;  
  - enquanto transtornos como esquizofrenia apresentam maior estabilidade.  
- Esses padrões sugerem que fatores sociais e ambientais recentes (como eventos traumáticos, crises econômicas, instabilidade global) podem estar associados ao aumento específico de ansiedade e depressão.

### 4.3. Carga da doença (DALYs) e impacto desproporcional

- Há uma **correlação positiva** entre prevalência de transtornos mentais e DALYs: quanto mais casos, maior a carga de doença.  
- Alguns países, porém, se destacam por um impacto desproporcional:
  - **Mongólia, Japão e Singapura** apresentam DALYs elevados mesmo com prevalência moderada.  
- A relação **DALY / prevalência** nesses casos indica que:
  - o sofrimento por pessoa afetada é maior;
  - há maior gravidade, cronicidade ou menor eficácia do sistema de suporte e tratamento.

### 4.4. Lacuna de tratamento em transtornos de ansiedade

- A ansiedade é o transtorno mental mais comum globalmente, mas o acesso a tratamento **não acompanha** essa alta prevalência.  
- Países como **México e Brasil** combinam:
  - taxas elevadas de ansiedade;
  - altos percentuais de pessoas com transtorno de ansiedade que **não recebem tratamento**.  
- Apesar de algum crescimento no número de casos tratados ao longo do tempo, essa evolução é:
  - lenta;
  - insuficiente frente ao ritmo de aumento da prevalência.  
- Isso evidencia:
  - falhas estruturais nos sistemas de saúde mental;
  - necessidade de políticas públicas que ampliem o acesso e reduzam o estigma.

### 4.5. Sintomas depressivos na população dos EUA

- Entre os sintomas depressivos analisados nos Estados Unidos, os mais relatados são:
  - **baixa energia** (~21,5%);
  - **problemas de sono** (~19,1%);
  - **perda de interesse** (~16,5%).  
- Sintomas como **pensamentos suicidas** aparecem em proporção menor (~2,9%), mas são extremamente críticos e demandam prioridade na atenção clínica.  
- Baixa energia e problemas de sono aparecem como sintomas mais persistentes, indicando:
  - forte impacto sobre produtividade, bem-estar diário e qualidade de vida.

---

## 5. Conclusões e recomendações

- O cenário global de saúde mental é marcado por:
  - **alta prevalência** de ansiedade e depressão;
  - **carga significativa de DALYs**, especialmente associada à depressão;
  - **desigualdades** importantes entre países em prevalência, impacto e acesso a tratamento.  

Alguns pontos se destacam para decisões e políticas:

- **Depressão** combina alta prevalência com grande carga de doença, sugerindo prioridade em políticas de prevenção, diagnóstico e tratamento.  
- Países de **baixa e média renda** apresentam:
  - lacunas relevantes no acesso a tratamento;
  - infraestrutura limitada;
  - desinformação e estigma, que dificultam a procura por ajuda.  
- Países com impacto desproporcional (como Mongólia, Singapura e Japão) indicam que:
  - fatores culturais, sociais e estruturais influenciam não apenas quantas pessoas adoecem, mas quão grave é a doença para cada pessoa.

Do ponto de vista de uso de dados, o projeto mostra:

- integração de múltiplas fontes e tabelas (prevalência, DALYs, treatment gap, sintomas);  
- uso de EDA para revelar padrões e desigualdades que não são óbvios à primeira vista;  
- apoio à tomada de decisão com base em indicadores comparáveis entre países.

Recomendações gerais:

- ampliar o acesso ao tratamento em países com alta prevalência e grande treatment gap;  
- usar indicadores de DALY para priorizar recursos onde o impacto por pessoa é maior;  
- investir em campanhas de conscientização para reduzir estigma e incentivar a busca por ajuda;  
- monitorar continuamente os indicadores para avaliar a efetividade das políticas implementadas.

---

## 6. Dashboard no Looker Studio

Os resultados foram sintetizados em um painel interativo, permitindo explorar:

- prevalência de transtornos mentais por país e ano;
- DALYs por tipo de transtorno;
- lacuna de tratamento em ansiedade;
- sintomas depressivos na população dos EUA.

🔗 [Dashboard no Looker Studio](https://lookerstudio.google.com/reporting/78f4f128-0fe4-4771-9ead-d83c26a265d9)

---

## 7. Estrutura sugerida do repositório

```bash
.
├── data/
│── raw/
│    ├── 1-mental-illnesses-prevalence.csv
│    ├── 2-burden-disease-from-mental-illness.csv
│    ├── 5-anxiety-disorders-treatment-gap.csv
│    └── 6-depressive-symptoms-across-us-population.csv
├── notebooks/
│   └── eda_saude_mental_global.ipynb
├── dashboard/
│   └── dashboard-saude-mental-global.pdf
└── README.md
