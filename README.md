# Case Técnico de Data Analysis - iFood

Este repositório contém a solução desenvolvida por mim para o case técnico do processo seletivo de Analista de Dados Sênior no iFood. O objetivo foi avaliar o impacto de uma campanha de cupons através de um experimento A/B, identificar os segmentos com melhor retorno e propor estratégias baseadas em dados.

---

## Estrutura da Análise

- Carregamento e tratamento dos dados (PySpark + Spark SQL)
- Análise exploratória e definição de métricas principais
- Cálculo de ROI por grupo e por segmento
- Segmentações: intensidade de uso, ticket médio, UF e plataforma
- Geração de insights e recomendações estratégicas
- Projeção de impacto financeiro com base em simulações

---

## Principais Resultados

- **ROI total estimado:** +160,9%
- **Melhor desempenho:** heavy users, ticket alto, iOS, estados como SP e RJ
- **Grupos com ROI negativo (ou muito baixo):** usuários com baixo uso, estados como SC e PI, Windows Phone
- **Economia potencial:** R$ 1,5 milhão ao eliminar cupons ineficientes
- **ROI potencial com foco em perfis de alto valor:** acima de 200%

---

## Recomendações Estratégicas

- Direcionar cupons para perfis com alto engajamento e ticket médio
- Eliminar ou reavaliar incentivos em segmentos com baixo retorno
- Incluir novas variáveis de segmentação (ex: tipo de restaurante)
- Executar testes multivariados por canal, valor e público

---

## Tecnologias Utilizadas

- **Ambiente:** Databricks + AWS S3
- **Linguagens:** Python, PySpark, SQL (Spark SQL)
- **Visualizações:** Plotly
- **Armazenamento:** S3 (formato `.parquet`)
- **Bibliotecas auxiliares:** Loguru, Kaleido, nbformat

---

## Organização do Repositório

```
notebooks/
├── 0-download-arquivos.ipynb
├── 1-analise-teste-ab.ipynb
apresentacao/
├── analise-campanha-cupons.pdf
README.md
```

---

## Como rodar este projeto

### 1. Criar ambiente no Databricks
- Crie uma conta gratuita no [Databricks](https://www.databricks.com/try-databricks) ativando o **free trial**
- Conecte sua conta Databricks a uma **nova conta AWS**
- Crie um **cluster interativo** com as seguintes configurações:
  - Runtime: **16.4 LTS (Spark 3.5.2, Scala 2.13)**
  - Tipo: **r5d.large** (16 GB RAM, 2 cores)
  - Instale as seguintes bibliotecas via PyPI na aba "Libraries" do cluster:
    - `kaleido==0.2.1`
    - `loguru==0.7.3`
    - `nbformat==5.10.4`

### 2. Preparar os dados no S3
- No bucket S3 criado automaticamente pela Databricks, crie o diretório:
  - `case-tecnico-analise-dados-ifood/dados/`
  - Dentro dele, adicione duas subpastas: `brutos/` e `processados/`
- Faça o upload dos **4 datasets fornecidos** para a pasta `brutos/`
  - ⚠️ Descompacte previamente o `.tar.gz` do teste A/B

### 3. Clonar o projeto
- Conecte sua conta GitHub ao Databricks
- Clone este repositório diretamente para seu workspace

### 4. Executar os notebooks
- Abra e execute `0-download-arquivos.ipynb`
  - Altere o caminho para refletir o diretório correto do seu bucket S3
- Em seguida, execute `1-analise-teste-ab.ipynb`
  - Também atualize o caminho do S3 onde os dados foram gravados
- Visualize as análises, segmentações, métricas e projeções geradas

---

## Autor

**Henrique Marques Turqueti**  
[LinkedIn](https://www.linkedin.com/in/henriqueturqueti)

---

Para dúvidas ou sugestões, fique à vontade para abrir uma issue ou entrar em contato.