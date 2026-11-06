Previsão de Churn de Clientes com Rede Neural

Projeto de estudo desenvolvido para praticar conceitos de Python, Machine Learning e Redes Neurais, utilizando uma rede neural MLP para prever o cancelamento de clientes (churn).

«Aviso: este projeto foi desenvolvido principalmente para fins de aprendizado e prática. Não é uma solução completa ou pronta para utilização em produção. A ideia é aplicar e compreender, na prática, as etapas de um projeto de Machine Learning.»

---

🎯 Objetivo

O objetivo do projeto é utilizar dados de clientes para tentar prever se um cliente irá cancelar ("Churn = 1") ou permanecer ("Churn = 0").

O projeto também busca praticar conceitos importantes de Machine Learning, como:

- Limpeza e preparação de dados;
- Separação entre variáveis de entrada ("X") e resposta ("y");
- Transformação de variáveis categóricas com One-Hot Encoding;
- Separação entre dados de treino e teste;
- Tratamento de valores vazios;
- Padronização dos dados;
- Balanceamento da classe de cancelamento;
- Treinamento de uma rede neural;
- Avaliação do modelo por meio de métricas de classificação.

---

🧠 Modelo utilizado

A rede neural utilizada é o "MLPClassifier", da biblioteca Scikit-learn.

A arquitetura utilizada possui duas camadas escondidas:

hidden_layer_sizes=(32, 16)

Além disso, o projeto utiliza:

- Função de ativação "ReLU";
- Taxa de aprendizado "0.001";
- Máximo de "300" épocas;
- "early_stopping=True";
- Semente aleatória "42" para facilitar a reprodução dos resultados.

---

🔄 Fluxo do projeto

O processamento segue aproximadamente este fluxo:

Carregar dados
      ↓
Limpar dados
      ↓
Separar X e y
      ↓
One-Hot Encoding
      ↓
Separar treino e teste
      ↓
Tratar valores vazios
      ↓
Padronizar os dados
      ↓
Balancear o conjunto de treino
      ↓
Treinar a rede neural
      ↓
Avaliar o modelo

---

⚖️ Balanceamento dos dados

Um dos pontos importantes do projeto é o balanceamento da classe de cancelamento.

A função "balancear()" repete clientes que cancelaram até que a quantidade de exemplos dessa classe fique equivalente à quantidade de clientes que permaneceram.

Esse balanceamento é aplicado somente aos dados de treinamento:

Treino → balanceado
Teste  → permanece original

Isso evita alterar artificialmente os dados utilizados para avaliar o desempenho do modelo.

---

📊 Avaliação

O modelo é avaliado utilizando:

Acurácia

Indica a proporção geral de previsões corretas.

Matriz de confusão

Permite visualizar quantos clientes foram classificados corretamente ou incorretamente em cada classe.

Precision

Ajuda a entender, entre as previsões de uma determinada classe, quantas realmente pertenciam àquela classe.

Recall

É especialmente importante neste projeto porque existe interesse em identificar clientes que podem cancelar.

F1-score

Combina Precision e Recall em uma única métrica.

---

🎯 Prioridade na detecção de cancelamentos

Como o objetivo principal do exercício é trabalhar com previsão de cancelamento, o projeto dá atenção especial ao desempenho da classe "cancelou".

Isso é importante porque um modelo pode apresentar uma acurácia geral razoável e, ainda assim, ter dificuldade para identificar clientes que realmente cancelam.

Por isso, a análise não deve considerar somente a acurácia, mas também métricas como Recall, Precision e F1-score da classe "cancelou".

---

🛠️ Tecnologias e ferramentas

Linguagem

- Python

Machine Learning

- Scikit-learn
- "MLPClassifier"
- "StandardScaler"
- "train_test_split"
- "classification_report"
- "confusion_matrix"

Manipulação de dados

- Pandas
- NumPy

Ambiente

- Google Colab
- Notebook Python

Ferramentas de apoio utilizadas durante o desenvolvimento

- ChatGPT (GPT) — apoio para estudo, explicação de conceitos, análise e desenvolvimento do código.
- Gemini — utilizado como ferramenta de apoio durante o desenvolvimento/estudo.

---

📁 Estrutura do projeto

Uma estrutura esperada para o projeto é:

projeto-churn/
│
├── data/
│   └── telco_churn.json
│
├── main.py
│
├── README.md
│
└── notebook/
    └── projeto_churn.ipynb

«A estrutura pode variar conforme a organização utilizada no repositório do GitHub.»

O arquivo de dados utilizado pelo código é:

data/telco_churn.json

O caminho é definido no código através de:

CAMINHO_DADOS = "data/telco_churn.json"

---

📥 Fonte dos dados

Os dados utilizados no projeto são dados de Telco Customer Churn.

No projeto, os dados são armazenados em formato JSON e carregados utilizando o Pandas:

df = pd.read_json(caminho)

A origem/API utilizada para obtenção dos dados deve ser adicionada aqui:

Fonte dos dados: [ADICIONAR URL DA API/FONTE]

---

▶️ Como executar

O projeto foi desenvolvido para ser executado em um ambiente Python, especialmente no Google Colab.

1. Abrir o notebook

Abra o arquivo ".ipynb" no Google Colab.

2. Disponibilizar os dados

Certifique-se de que o arquivo:

data/telco_churn.json

esteja disponível no ambiente de execução.

3. Executar o código

Execute as células do notebook na ordem.

O programa executará a função:

if __name__ == "__main__":
    main()

que organiza todo o fluxo do projeto.

---

🔬 Principais etapas do código

O programa é organizado em funções para separar as responsabilidades.

"carregar_dados()"

Carrega o arquivo de dados utilizando o Pandas.

"limpar_dados()"

Realiza algumas etapas de limpeza, como:

- remoção de "customerID";
- conversão de "TotalCharges" para valores numéricos;
- transformação de "Churn" em "0" ou "1".

"separar_x_y()"

Separa:

X → características dos clientes
y → resposta que queremos prever

Também realiza o One-Hot Encoding das variáveis categóricas.

"preparar_para_rede()"

Realiza:

- divisão entre treino e teste;
- tratamento de valores vazios;
- padronização dos dados.

"balancear()"

Balanceia a classe de cancelamento somente no conjunto de treinamento.

"treinar_rede()"

Cria e treina a rede neural "MLPClassifier".

"avaliar()"

Realiza a avaliação utilizando:

- acurácia;
- matriz de confusão;
- relatório de classificação.

---

📌 Exemplo da arquitetura da rede

A configuração utilizada no projeto é:

MLPClassifier(
    hidden_layer_sizes=(32, 16),
    activation="relu",
    learning_rate_init=0.001,
    max_iter=300,
    early_stopping=True,
    random_state=42
)

---

📚 Objetivo de aprendizado

Este projeto foi criado como uma forma prática de estudar e consolidar conhecimentos sobre:

- Python aplicado a dados;
- NumPy e Pandas;
- preparação de dados;
- Machine Learning;
- classificação binária;
- redes neurais;
- "MLPClassifier";
- balanceamento de classes;
- métricas de avaliação;
- interpretação de resultados.

A intenção principal é aprender como as diferentes etapas de um projeto de Machine Learning se conectam, e não desenvolver um sistema comercial completo.

---

🚧 Limitações

Por ser um projeto de estudo, ele possui algumas limitações e pode ser aprimorado futuramente.

Possíveis melhorias incluem:

- testar outros modelos;
- realizar ajuste de hiperparâmetros;
- comparar diferentes arquiteturas de redes neurais;
- explorar outras técnicas de balanceamento;
- analisar mais profundamente as características dos clientes;
- criar visualizações dos dados;
- melhorar a organização do projeto;
- criar uma interface para realizar previsões;
- desenvolver uma etapa de deploy.

---

📈 Próximos passos

Este projeto pode servir como base para estudos futuros de Machine Learning e Inteligência Artificial, permitindo evoluir gradualmente de um notebook de treinamento para uma aplicação mais completa.

---

👨‍💻 Projeto

Projeto desenvolvido com finalidade educacional e de prática em Python, Machine Learning e Redes Neurais.

Status: Projeto de estudo / treinamento.