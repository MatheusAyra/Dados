from sklearn.svm import LinearSVC

#vou treinar a máquina para ela identificar a partir das informações que eu mandar pra ela se um composto é solúvel em água ou se não é

composto1 = [1, 1, 1]
composto2 = [0, 0, 0]
composto3 = [1, 0, 1]
composto4 = [0, 1, 0]
composto5 = [1, 1, 0]
composto6 = [0, 0, 1]

#se for polar vai ter o número 1 se for não polar vai ter o número 0
#estamos treinando um modelo  que estamos dando caracteristicas e a única coisa que queremos saber é se ele vai ser solúvel ou não
#quando treinamos o algoritimo não precisamos dar todos os dados para ele

dados_treino = [composto1, composto2, composto3, composto4, composto5, composto6]
rotulos_treino = ['S', 'N', 'S', 'N', 'S', 'S']

modelo = LinearSVC()
modelo.fit(dados_treino, rotulos_treino)

teste1 = [1, 0, 0]
teste2 = [0, 1, 1]
teste3 = [1, 0, 1]

dados_teste  = [teste1, teste2, teste3]
previsoes = modelo.predict(dados_teste)

mapeamento_previsoes = {'S': 'Solúvel', 'N': 'Não Solúvel'}

print("Previsões do modelo para os compostos testados:", previsoes)
for i, previsao in enumerate(previsoes):
    print(f'O composto {i+1} pode ser considerado {mapeamento_previsoes[previsao]}')
