## Resumo

Este projeto implementa um pipeline completo de processamento de dados sobre um dataset de E-commerce, contemplando desde a análise exploratória dos dados até a implementação de uma Arquitetura Lambda para processamento em lote e em tempo real.

A solução é composta por uma etapa de análise dos dados, uma camada de processamento em lote responsável pela geração de vistas agregadas e mecanismos de gerenciamento, além de uma camada de velocidade que simula a chegada contínua de novos registros utilizando múltiplas threads.

O projeto foi desenvolvido como atividade da disciplina de Arquitetura de Grande Volume de Dados, no 5º semestre do curso de Ciência de Dados e Inteligência Artificial.

## Tecnologias utilizadas
- Python;
- Pandas e NumPy para manipulação dos dados;
- Matplotlib e Seaborn para visualização;
- Threading para execução de múltiplas tarefas simultâneas.

## Como executar
1. Clone o repositório;
2. Instale as dependências;
3. Análise de dados: execute célula por célula o Analise_Dados.ipynb.
4. Arquitetura Lambda (Camada de Lote/Velocidade): execute célula por célula o Arquitetura_Lambda.ipynb.

## Funcionalidades
- Análise exploratória completa do dataset;
- Identificação de inconsistências e valores ausentes;
- Particionamento automático dos dados;
- Geração de vistas em lote com diferentes métricas agregadas (Média, Contagem, Máximo, Mínimo, Mediana, Moda, Variância e Desvio-padrão);
- Geração automática de logs de processamento;
- Encaminhamento de registros inválidos para arquivos de quarentena;
- Simulação de streaming utilizando múltiplas threads;
- Atualização contínua da vista em tempo real.

## Resultados
A etapa de análise exploratória foi fundamental para compreender a estrutura e a qualidade do dataset, permitindo identificar valores ausentes, validar as especificações dos atributos e justificar a necessidade de uma arquitetura capaz de processar grandes volumes de dados.

A implementação da camada de processamento em lote evidenciou a importância do particionamento dos dados para o processamento eficiente das agregações. Além disso, foram incorporados mecanismos de controle e garantia da qualidade, como o log de processamento e os arquivos de quarentena, permitindo rastrear falhas e identificar registros inconsistentes. A **Figura 1** mostra um exemplo de vista de lote gerado para esse dataframe (apenas para algumas variáveis), onde para cada data obtivemos suas métricas.

<p align="center">
  <img src="imgs/Exemplo de Vista de Lote.png" width="650">
</p>

<p align="center">
  <em>Figura 1 – Exemplo da vista de lote. </em>
</p>

A **Figura 2** mostra um exemplo do arquivo log_processamento, o arquivo evidencia quais arquivos foram processados ou não, e em caso de erro o evidencia.

<p align="center">
  <img src="imgs/Exemplo log_processamento.png" width="650">
</p>

<p align="center">
  <em>Figura 2 – Exemplo de Log de Processamento. </em>
</p>

A implementação da camada de velocidade representou o maior desafio do projeto. A utilização de múltiplas threads para simular o fluxo contínuo de dados exigiu a sincronização entre a geração dos registros e a atualização da vista em tempo real, reproduzindo o comportamento esperado de uma camada de streaming. A **Figura 3** demonstra uma fração da vista rápida durante seu processamento. 

<p align="center">
  <img src="imgs/Vista Rapida.gif" width="850">
</p>

<p align="center">
  <em>Figura 3 – Exemplo de Vista Rápida. </em>
</p>

## Relatório

O relatório completo contendo a fundamentação teórica, metodologia, implementação e análise dos resultados pode ser acessado no [Link](https://docs.google.com/document/d/1tnZhDi3xWFQTnJHlx99Bic-8YNLbcabU/edit?usp=sharing&ouid=111431313917294270595&rtpof=true&sd=true). 

## Estrutura do Projeto
```text
📦T1-BigData
 ┣ 📂dados_brutos
 ┃ ┣ 📜2017-03-14.csv
 ┃ ┣ 📜2017-03-15.csv
 ┃ ┣ 📜2017-03-16.csv
 ┃ ┣ 📜2017-03-17.csv
 ┃ ┣ 📜2017-03-18.csv
 ┃ ┣ 📜2017-03-19.csv
 ┃ ┣ 📜2017-03-20.csv
 ┃ ┗ 📜2017-03-21.csv
 ┣ 📂dados_novos
 ┃ ┗ 📜fluxo.log
 ┣ 📂gerenciamento
 ┃ ┣ 📜log_processamento.csv
 ┃ ┣ 📜quarentena_linhas_brutas.csv
 ┃ ┗ 📜quarentena_linhas_por_arquivo.csv
 ┣ 📂imgs
 ┣ 📂vistas_lote
 ┃ ┣ 📜vistas_de_lote copy.csv
 ┃ ┗ 📜vistas_de_lote.csv
 ┣ 📂vistas_tempo_real
 ┃ ┗ 📜contagem_incremental.csv
 ┣ 📜Analise_Dados.ipynb
 ┣ 📜Arquitetura_Lambda.ipynb
 ┗ 📜E-commerce Website Logs.csv
```

## Equipe

Projeto desenvolvido em grupo para a disciplina de Arquitetura de Grande Volume de Dados.

**Integrantes:**
- Edson Eduardo Ferreira - 23908965
- Gabriel Batista Chiezo - 23028678
- Yan Yoshida Luz - 23911118