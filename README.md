## Sobre o problema

<pre>
O problema trata-se de uma empresa/setor de telemarketing que tem como desafio entender,
dentro de sua base de contatos, qual a melhor forma de investir recursos para abordagens
mais assertivas. É necessário o contato telefônico com a pessoa de interesse afim de
oferecer produtos que posssam ser adquiridos. O desafio é fazer com que as ligações não
sejam um motivo de estresse oferecendo produtos que o cliente precisa/tem interesse.

Eu entendo que ligar para pessoas que não têm interesse no(s) produto(s) tem um custo
mais elevado que não ligar para um pessoa que tenha interesse no(s) produto(s), tanto
pelo custo financeiro (telefone, operador) quanto pelo custo da reputação já que um
cliente que foi contatado sem ter interesse pode ser um influenciador e propagar uma
reputação ruim da empresa.

Partindo dessa premissa a Recall é uma boa escolha para a métrica de avaliação já que
ela penaliza o falso positivo (ligar para o cliente que não tem interesse). Por outro
lado não podemos negligenciar o cliente que pode ser um possível interessado, então
pensando também neste trade off eu considerei como métrica final a Area under the curve
para o maior valor de Recall encontrado.
</pre>

## Sobre a solução

<pre>
O framework utilizado para desenvolvimento foi o <b>CRISP</b> e foram necessárias algumas
iterações até o modelo final aqui apresentado. Durante as iterações foram testados e ou
acrescentados diversas configurações e técnicas, algumas quais apresento abaixo:

- Foi feito teste de normalização usando as classes MinMaxScaler e RobustScaler;
- Exclusão das features com muitos valores -999 (faltantes?), acima de 80%;
- Exclusão das features com baixa variância;
- Exclusão das features altamente correlacionadas, acima de .8 (pearson);
- Exclusão das features categóricas nominais;
- Trocar o tipo das variáveis nominais para category e usar LabelEncoder;
- Undersampling com RandomUnderSampler e TomekLinks;
- Oversampling com RandomOverSampler e SMOTE;
- Mix de Over/Undersampling com SMOTETomek;
- Substituir os valores (-999) pela mediana das variáveis;
- Substituir os valores (-999) pela média das variáveis;
- Adicionado modelos relevantes para o problema e para a estrutura dos dados;
- Foi realizada uma escolha mais aguçada dos parâmetros de cada modelo, menos que uma
  tunagem e mais do que um random choice;
- Etc.

Utilizei 5 algoritmos para testar o modelo e dentre eles, seguindo o princípio de Occam's
razor, a escolha do melhor coincidiu com o mais simples. A Regressão logística foi o
melhor tanto no teste simples quanto usando validação cruzada.
</pre>

![Métricas](/compass/data/imagem1.png "Resultados das métricas")

## Próximos passos

<pre>
Para melhoria do case há muitos caminhos que poderiam ser testados em outras iterações do
CRISP, sugiro algumas abaixo:

- Utilizar um feature importance como SelectKBest;
- Utilizar um algoritmo de seleção de features como o Boruta;
- Realizar tunagem de hyper parâmetros dos modelos selecionados;
- Algum tratamento para as features categóricas;
- Etc.
</pre>