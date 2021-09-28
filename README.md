# Repositório do Bootcamp de Data Science Aplicado
Repositório para meus notebooks e projetos do bootcamp de Data Science da Alura. Dividirei as pastas para cada módulo e neste readme focarei em falar dos aspectos gerais de cada módulo enquanto dentro de cada diretório dos módulos haverá um readme específico sobre o projeto do respectivo módulo.

# Módulo 1: Python e pandas para análise de dados reais.
* Neste módulo trabalhamos com dados do SUS, obtidos pela fonte do governo : http://tabnet.datasus.gov.br/cgi/deftohtm.exe?sih/cnv/qiuf.def onde como linha selecionamos "Unidade da Federação" e conteúdo selecionamos "Valor total", alternando os valores das colunas de acordo com nosso interesse. Pegamos esses dados para todos os meses e anos disponíveis. 
* O objetivo deste módulo foi utilizar funções básicas da biblioteca pandas para manipular o DataFrame e tratar-lo a fim de se retirar informações e até criar gráficos informativos.

# Módulo 2: Visualização de dados com Seaborn e Matplotlib.

* Neste módulo seguimos com as análises dos dados financeiros do SUS. Fomos mais detalhistas no tratamento e manipulação dos dados para análises mais complexas, utilizando recursos mais avançados do Pandas e da Linguagem Python como um todo, assim como outras bibliotecas como o própria Seaborn.

# Módulo 3: Análise de séries temporais.

* Neste módulo aprendemos a tratar séries temporais, utilizando como objeto de estudo a série tempo dos casos de covid-19 na cidade de São Paulo. Nós trabalhamos principalmente com a biblioteca Prophet e aprendemos a criar um modelo para prever o número de casos de Covid-19, modificando alguns parâmetros para além de um modelo básico, como adicionar a informação de quais dias são feriados, além de alterar o valor de algumas variáveis que definem o quão o algoritmo vai se modelar aos dados. Além disse utilizamos algumas métricas estatísticas de bibliotecas como o Scikit Learning, entre outras, para avaliar o desempenho do nosso modelo. Meu projeto final desse módulo consistiu em criar um modelo preditivo para o estado do Rio de Janeiro assim como fazer uma breve discussão sobre a adoção de medidas de distanciamento social ao combate da Covid-19, comparando ao estado de Berlim, na Alemanha.

# Módulo 4: Machine Learning e Saúde.

* Neste módulo abordamos o assunto de machine learning aplicado ao problema de previsão de uso de UTIS por pacientes internados no hospital Sírio-Libanês. Trabalhamos com modelos de Regressão linear do scikit learning básicos aliados à manipulação dos dados, onde o foco do módulo foi a manipulação e a análise explanatória para melhor compreensão do problema para assim podermos criar um algoritmo mais sofisticado que busque resolver esta questão pertinente.

# Módulo 5: Machine Learning: Modelos, métricas e validação.

* Ainda trabalhando no problema do hospital Sírio-Libanês disponibilizado no kaggle estamos agora com foco na criação de um bom algoritmo de Machine Learning, para isso, avaliamos qual seria a melhor métrica de avaliação para definirmos o melhor modelo assim como seus parâmetros, além da realização de outras prátricas estatistico-computacionais para verificar a validade dos resultados de nossos modelos.

# Módulo 6: Data Science aplicado em finanças.
* Análise exploratória ,tratamento de dados e treinamento de um modelo para o problema específico de análise de crédito bancário. Se fez necessário a discussão de novas métrias, ressaltando por exemplo a métrica de KS-Score, além de um método de tratamento de dados específico da área bancária chamado análise vintage.
