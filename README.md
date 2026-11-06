# Informática Aplicada à Logística

Repositório com as atividades da disciplina de **Informática Aplicada à Logística**, organizadas por sequência. As atividades trabalham com **dados abertos governamentais**, usando fórmulas e gráficos no **Excel** e dashboards no **Power BI**.

## Sumário

| # | Atividade | Status | Ferramenta | Arquivo |
|---|-----------|--------|------------|---------|
| 1 | Apresentação em equipe – 13/08 | Concluído | — | — |
| 2 | Aula 28 de agosto | Concluído | — | — |
| 3 | Planilhas eletrônicas e dados abertos | Concluído | Excel | `Atividade_2.xlsx` |
| 4 | Empresas Multimodais e Perguntas | Concluído | Excel | `Atividade_1.xlsx` |
| 5 | Dados_abertos_5_perguntas | Concluído | Power BI | `Atividade_3.pbix` |

---

## 1. Apresentação em equipe – 13/08

<img width="948" height="527" alt="image" src="https://github.com/user-attachments/assets/f4b17d46-65b1-45e7-9e5e-f22eac26554e" />


**Status:** Concluído

Apresentação pessoal sobre minha trajetória, experiências, interesses e perspectivas profissionais.

### Conteúdo apresentado

---

## 2. Aula 28 de agosto

<img width="1919" height="1021" alt="image" src="https://github.com/user-attachments/assets/f71aa3cd-117c-48bd-84a4-28372047b95b" />


**Status:** Concluído

---

## 3. Planilhas eletrônicas e dados abertos

<img width="1919" height="1007" alt="image" src="https://github.com/user-attachments/assets/be29b2f5-e52d-4048-b752-e36b6cbe5447" />


**Status:** Concluído

**Enunciado:** acessar dados abertos governamentais, coletar um conjunto de dados de preferência (`.csv`) e elaborar e responder, via fórmulas ou gráficos, 5 perguntas sobre os dados.

**Fonte dos dados:** Autos de Infração Ambiental, do [Portal de Dados Abertos do Estado de São Paulo](https://dadosabertos.sp.gov.br/).

**Base:** 147.051 autos de infração, entre 2019 e 2026 (2026 é ano parcial), com as colunas `NIS`, `Sigla`, `Número Auto`, `Ano Processo`, `Número Processo`, `Situacao`, `Status`, `Classe Infração`, `Data Infração`, `Dia`, `Mês`, `Ano` e `Municipio`.

> **Atenção:** na base original, a coluna `Dia` guarda o número do **mês** (01 a 12) e a coluna `Mês` guarda o **dia**. Por isso, as contagens por mês usam a coluna `Dia`.

### Perguntas e respostas

| Pergunta | Resposta | Gráfico |
|----------|----------|---------|
| **P1:** Qual classe de infração aparece com maior frequência? | **FLORA**, com 68.720 autos (cerca de 46,7% do total). | Barras horizontais |
| **P2:** Quais municípios concentram mais autos? | **São Paulo** lidera (6.678), seguido por Ubatuba (3.059) e Itanhaém (2.669). | Top 10 municípios, barras horizontais |
| **P3:** Em quais meses há maior quantidade de autos? | **Março** é o maior (13.859) e **dezembro** o menor (9.151). | Colunas |
| **P4:** Quais são os 10 status mais frequentes e qual é o maior? | O maior é **AIA pago**, com 20.959 autos. | Top 10 status, barras horizontais |
| **P5:** Quantos municípios tiveram infrações? | **649 municípios** (veja a observação abaixo). | Caixa de texto |

> **Observação sobre a P5:** a fórmula com `[#Tudo]` inclui o cabeçalho da coluna na contagem e resulta em 650. Sem o `[#Tudo]`, o resultado correto é **649**.

### Fórmulas utilizadas

| Uso | Fórmula |
|-----|---------|
| Autos por classe de infração | `=COUNTIF(Tabela1[[#All];[Classe Infração]]; A2)` |
| Autos por ano | `=SUMPRODUCT(--(Tabela1[Ano]=AA4))` |
| Autos por município | `=COUNTIF(Tabela1[Municipio]; AD4)` |
| Autos por status | `=COUNTIF(Tabela1[Status]; AG4)` |
| Autos por mês | `=SUMPRODUCT(--(Tabela1[Dia]=AJ4))` |
| Total de municípios | `=CONT.VALORES(Tabela3[Municipio])` |

### Resumo das funções

- **COUNTIF (CONT.SE):** conta quantas células são iguais a um valor ou atendem a uma condição.
- **COUNTA (CONT.VALORES):** conta quantas células não estão vazias, sem olhar o conteúdo.
- **SUMPRODUCT (SOMARPRODUTO):** multiplica e soma listas ao mesmo tempo. Com `--(condição)`, vira uma contagem de texto exato, por exemplo quantos autos têm o ano "2020".

As tabelas de apoio dos gráficos ficam nas colunas **AA a AL** da aba **Gráficos**.

---

## 4. Empresas Multimodais e Perguntas

<img width="1353" height="922" alt="image" src="https://github.com/user-attachments/assets/4fbc60a1-34f1-4dd3-9fa8-d224797837c1" />


**Status:** Concluído

**Base de dados:** [Dados abertos da ANTT: Operador de Transporte Multimodal](https://dados.antt.gov.br/dataset/operador-transporte-multimodal/resource/9f76aca6-0e8d-4c13-8851-0ad8ced5c5b7)

### Ferramenta utilizada

Excel.

**Arquivo:** `Atividade_1.xlsx`

**Base:** 1.382 empresas, com as colunas `pais_de_origem`, `razao_social`, `cnpj`, `logradouro`, `cidade`, `uf`, `cep`, `e_mail`, `cotm`, `adesao_ao_decreto_1563_95`, `dia`, `mês` e `ano`.

### Perguntas e respostas

| Pergunta | Resposta | Fórmula |
|----------|----------|---------|
| **P1:** Qual estado tem a maior quantidade de empresas? | **São Paulo**, com 569 empresas. | `=COUNTIF(operador_transporte_multimodal!F:F; A2)` |
| **P2:** Qual(is) país(es) tem(têm) a menor contagem de empresas? | **Paraguai, Alemanha e Suíça**, com 1 empresa cada. | `=COUNTIF(operador_transporte_multimodal!A:A; O2)` |
| **P3:** Quantas empresas cumprem e quantas não cumprem a adesão ao decreto 1.563/95? | **Cumprem: 275**; **não cumprem: 1.107**. | `=COUNTIF(operador_transporte_multimodal!J:J; S2)` |

Também foi criada a coluna auxiliar **Data**, que monta a data a partir das colunas de dia, mês e ano: `=DATE(M2;L2;K2)`.

Os gráficos de cada pergunta estão na aba **Gráficos** do arquivo.

---

## 5. Dados_abertos_5_perguntas

<img width="1352" height="911" alt="image" src="https://github.com/user-attachments/assets/56f719cd-2388-41fa-8386-e7b624e55727" />


**Status:** Concluído

**Enunciado:** acessar dados abertos governamentais, considerando o que foi coletado na atividade anterior, e elaborar e responder, por meio de **dashboards no Power BI**, 5 perguntas sobre os dados.

**Fonte dos dados:** os mesmos Autos de Infração Ambiental da atividade 3.

### Dashboard "Auto Inflação"

| Pergunta | Visual | Campos |
|----------|--------|--------|
| Como evoluiu a quantidade de autos por ano? | Gráfico de linhas | `Ano` e `Total Autos` |
| Qual classe de infração aparece com maior frequência? | Colunas agrupadas | `Classe Infração` e `Total Autos` |
| Quais municípios concentram mais autos? | Barras agrupadas, filtro dos 5 primeiros | `Municipio` e `Total Autos` |
| Quais são os status mais frequentes? | Pizza, filtro dos 5 primeiros | `Status` e `Total Autos` |
| Em quais meses há maior quantidade de autos? | Colunas agrupadas | `Mes nome` e `Total Autos` |

### Fórmulas utilizadas

**Medida em DAX (`Total Autos`):** conta as linhas da tabela dentro do filtro de cada visual.

```dax
Total Autos = COUNTROWS('Autos-de-Infracao-Ambiental-a-p')
```

**Coluna no Power Query, linguagem M (`Mes nome`):** converte o número do mês (coluna `Dia`) no nome abreviado.

```powerquery
{"Jan","Fev","Mar","Abr","Mai","Jun","Jul","Ago","Set","Out","Nov","Dez"}{[Dia]-1}
```

### Principais resultados

- **2020** foi o ano com mais autos (22.636). A quantidade cai a cada ano depois disso, chegando a 15.602 em 2025.
- **FLORA** é a classe mais frequente, com 68.720 autos.
- **São Paulo** é o município com mais autos (6.678).
- **AIA pago** é o status mais frequente (20.959).
- **Março** é o mês com mais autos.

> Para abrir o arquivo `.pbix`, é necessário o **Power BI Desktop**.

---

## Repositório

[https://github.com/hemillyfreitas/Informatica-Aplicada-a-Logistica](https://github.com/hemillyfreitas/Informatica-Aplicada-a-Logistica)
