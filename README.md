# analise-de-vendas
Estudando Análise de dados com Python

Análise de Vendas e Tendências
Relatório gerado com Python e Pandas
Este notebook contém uma análise exploratória de dados de vendas, onde investigamos os produtos mais vendidos, tendências de preços e receitas.

Definir Escopo do Projeto
Objetivo: Analisar um conjunto de dados de vendas para encontrar insights sobre o desempenho dos produtos
Linguagem: Python(com Pandas, Matplotlib e Seaborn)
Saída do Projeto: Relatório com gráficos e insights, que pode ser salvo em um Jupyter Notebook ou em um dashboard interativo(Streamlit)
Importar bibliotecas e carregar dados

[5]
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns 

# carregar o arquivo CSV
df = pd.read_csv('/content/vendas.csv')

# Ver as primeiras linhas
print(df.head())




Explorar os dados

[ ]
# Verificar informações do dataset
print(df.info())

# Verificar estatísticas descritivas
print(df.describe())

Analisar e Limpar os Dados
Remover dados ausentes, corrigir formatos e garantir que tudo esteja pronto para a análise.
Clique duas vezes (ou pressione "Enter") para editar


[16]
0s
# Verificar valores nulos
print(df.isnull().sum())

# Preencher ou remover valores nulos, se necessário
df.dropna(inplace = True)


Criar Análises e Gráficos
Aqui, podemos gerar insights visuais
Produtos mais vendidos

# Produtos mais vendidos
top_produtos = df.groupby("produto")["quantidade"].sum().sort_values(ascending = False).head(10)
plt.figure(figsize = (10,5))
sns.barplot(x = top_produtos.index, y = top_produtos.values, palette = "viridis")
plt.xticks(rotation = 45)
plt.title("Top 10 Produtos Mais Vendidos")
plt.xlabel("Produto")
plt.ylabel("Quantidade Vendida")
plt.show()

Distribuição dos Preços

plt.figure(figsize = (8,5))
sns.histplot(df["preco"], bins = 20, kde = True)
plt.title("Distribuição dos Preços")
plt.xlabel("Preço")
plt.ylabel("Frequência")
plt.show()

Faturamento por categoria

faturamento_categoria = df.groupby("categoria")["receita"].sum()
plt.figure(figsize = (8,5))  
sns.barplot(x = faturamento_categoria.index, y = faturamento_categoria.values, palette = "viridis")
plt.title("Faturamento por Categoria")
plt.xlabel("Categoria")
plt.ylabel("receita")
plt.show()

Conclusão do Relatório
O produto mais vendido foi: Mouse Pad
A categoria que gerou mais receita foi: Utensílios
A variação dos preços sugere que: A maioria dos produtos tem um preço semelhante
A loja pode investir mais em: Materiais de escritório
Com base nesses dados, é possível tomar decisões estratégicas para aumentar as vendas.



