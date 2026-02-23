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
