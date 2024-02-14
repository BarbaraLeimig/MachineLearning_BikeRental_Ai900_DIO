# Projeto de Machine Learning na Azure
Este projeto usa o Azure Machine Learning para criar e treinar um modelo de regressão que prevê o número de bicicletas alugadas em uma hora, com base em dados de clima e calendário.

## Dados
Os dados usados neste projeto são do UCI Machine Learning Repository, e consistem em 17.379 registros de horas, cada um com 16 atributos, incluindo:

- day: dia do mês (1 a 31)
- mnth: mês do ano (1 a 12)
- year: ano (0: 2011, 1: 2012)
- season: estação do ano (1: inverno, 2: primavera, 3: verão, 4: outono)
- holiday: se o dia é feriado ou não (0: não, 1: sim)
- weekday: dia da semana (0: domingo, 1: segunda-feira, …, 6: sábado)
- workingday: se o dia é dia útil ou não (0: não, 1: sim)
- weathersit: situação do tempo (1: limpo, 2: nublado, 3: chuva leve, 4: chuva forte)
- temp: temperatura em graus Celsius
- atemp: sensação térmica em graus Celsius
- hum: umidade relativa do ar
- windspeed: velocidade do vento
- cnt: número de bicicletas alugadas, incluindo as casuais e as registradas (variável alvo)

## Modelo
O modelo usado neste projeto é uma regressão linear, que é um método simples mas eficaz para modelar relações lineares entre variáveis. O modelo é treinado usando o Azure Machine Learning, que permite criar e gerenciar experimentos, recursos de computação, conjuntos de dados, ambientes e modelos de forma fácil e integrada.

## Ponto de extremidade
O ponto de extremidade criado neste projeto é um serviço web que recebe dados de entrada em formato JSON e retorna a previsão do número de bicicletas alugadas em uma hora. O serviço web é hospedado no Azure Container Instances, que é uma opção rápida e econômica para implantar contêineres sem precisar de orquestração.

## Passo a passo de criação do projeto na plataforma Azure
1 - Acesse a plataforma Azure
2 - Clique em `My Dashboard` e em seguida em `Create a resource`
3 - Busque por `Machine Learning` e clique em `create`
4 - Crie um `Resource group` com o nome LABAI-900
5 - Em `Workspace details` digite, tem Nome, laboratorioai900
6 - Deixe a região como West US
7 - Clique em `Review + create` e em seguida `Create`
8 - Aguarde o Deploy
9 - Após finalizado, clique em `Go to resource` e em seguida em `Launch studio`
10 - No menu localizado na barra lateral, clique em `ML automatizado` e em `Novo trabalho de ML automatizado`
11 - Preencha os campos: Nome do trabalho = mslearn-bike-automl, novo nome do experimento = mslearn-bike-rental, coloque uma descrição e clique em `avançar`. Em selecione o tipo de tarefa, clique em `Regressão`. Clique em `Criar`. Preencha os campos: Nome = alugueldebicicletas, coloque uma descrição, tipo = tabular e clique em `avançar`. Clique em `De arquivos da Web` e `avançar`. Insira a url = http://aka.ms/bike-rentals e `avançar`. Em cabeçalho da coluna, selecione `Somente o primeiro arquivo tem cabeçalhos` e `avançar`. Clique em `criar`.
12 - Clique em `alugueldebicicletas`. Em coluna de destino selecione `rentals`. Clique em `Limites` e tire a seleção do primeiro e terceiro item. Em modelos permitidos selecione `RandomForest` e `LightGBM`. Tipo de validação = divisão de validação de treinamento.
13 - Clique em `avançar` e em seguida em `Enviar trabalho de treinamento`. Aguarde a criação do projeto
14 - No menu localizado na barra lateral, clique em `Modelos` e selecione o nosso modelo criado e em seguida no link abaixo do título `Criado por trabalho`
15 - Clique em `Pontos de extremidades` e selecione o poto criado
16 - Vá na área `Testar` e execute o json disponível que foi produzido.
