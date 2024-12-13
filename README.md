# Prevendo Desistências na Faculdade
O projeto teve como objetivo prever quais alunos estão mais propensos a desistir da faculdade, para que ações possam ser planejadas para incentivá-los a permanecer na universidade.

# Análise Inicial dos Dados
Primeiramente, foi realizada uma análise exploratória dos atributos (colunas) do dataset, verificando como eles impactam a variável-alvo (target), que possui três categorias:

Matriculados: Alunos atualmente matriculados.
Desistentes: Alunos que abandonaram o curso.
Graduados: Alunos que concluíram a graduação.
Essa análise ajudou a identificar padrões e possíveis relações entre os atributos e o comportamento dos alunos.

# Divisão dos Dados
Os dados foram divididos em três partes:

Treinamento: Para construir o modelo.
Validação: Para ajustar hiperparâmetros e avaliar o modelo durante o desenvolvimento.
Teste: Reservados para uma avaliação final com dados nunca vistos, garantindo que o modelo generalize bem.

# Treinamento do Modelo
Com os dados de treino e validação, dois modelos foram testados:

Random Forest: Utilizado inicialmente para prever as categorias.
Gradient Boosting: Aplicado para comparar o desempenho em relação ao Random Forest.
Os modelos foram avaliados com base em:

Matriz de Confusão: Para observar a distribuição das previsões.
Métricas de Desempenho:
Precisão: Proporção de previsões corretas em relação ao total de previsões.
Recall: Capacidade de encontrar todos os casos relevantes.
F1 Score: Média harmônica entre precisão e recall.
# Problema de Desempenho
Durante a análise dos resultados, observou-se que a última linha da matriz de confusão (relativa aos "desistentes") apresentava um recall de apenas 26%, com a maioria dos casos sendo erroneamente classificados como "graduados". Esse problema foi atribuído ao desbalanceamento dos dados, onde as classes "graduados" e "matriculados" tinham muito mais exemplos do que a classe "desistentes".

Como o objetivo principal era identificar os alunos propensos a desistir, esse desempenho foi considerado insatisfatório.

# Rebalanceamento dos Dados
Para resolver o problema, foi aplicado o método SMOTE (Synthetic Minority Oversampling Technique), que realiza oversampling para equilibrar a quantidade de dados entre as classes. Após o rebalanceamento, o modelo foi treinado novamente.

# Novos Resultados
Com os dados balanceados, o modelo apresentou uma melhora significativa na previsão da classe "desistentes", conforme observado na nova matriz de confusão e nas métricas de recall e precisão.

# Validação Cruzada
Para garantir que o modelo não estava superajustado aos dados de treinamento, foi aplicada uma validação cruzada utilizando:

Pipeline: Para organizar as etapas do processo de treinamento.
StratifiedKFold: Para preservar a proporção das classes em cada divisão da validação cruzada.
# Teste Final
Finalmente, o modelo foi avaliado utilizando os dados de teste (que não haviam sido usados durante o treinamento). Isso permitiu verificar a capacidade do modelo de generalizar para dados nunca vistos, evitando problemas como superajuste.

# Principais Conclusões
Com as melhorias implementadas, o modelo demonstrou ser eficaz em identificar alunos propensos a desistir, o que possibilita:

Implementar estratégias preventivas para alunos "matriculados" em risco.
Agir proativamente com os "desistentes" para tentar reverter a decisão.
