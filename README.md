# Estratégia comercial para expansão da base de clientes de uma fintech de investimentos.

Para o trabalho de conclusão de curso Data Analytics da Tera, fomos desafiados a pôr em prática todo o conteúdo aprendido durante as aulas, propondo um problema de negócio e hipóteses para serem respondidas com dados.

Neste documento consta todo o levantamento, raciocínio e estratégia utilizados para chegarmos a conclusão do problema proposto.

A escolha do tema não foi fácil, queríamos falar sobre o tema de investimentos, mas é uma área muito ampla, com muitas vertentes. Após algumas discussões, optamos por nos posicionar como uma nova fintech no mercado de investimentos, que está buscando uma estratégia comercial mais efetiva. Dessa forma, foi possível explorar uma base de dados de investidores brasileiros, de modo a traçar um perfil e buscar padrões relevantes para este público.

## Cenário de investimentos no Brasil

Porque os brasileiros não tem costume de guardar dinheiro e investir?

Segundo reportagem da Creditas, embora exista uma correlação entre renda e o percentual de pessoas que fazem reservas, também é importante considerar o contexto histórico da economia brasileira.

A reportagem traz contextos históricos que ajudam a compreender a falta de cultura do planejamento financeiro no Brasil. Os reflexos do baixo número de investidores podem ser justificados pelo resquício da recessão causada pela ditadura militar, somado aos efeitos da hiperinflação que assolou o país durante o governo de Fernando Collor, período lembrado até hoje pelo confisco pelas cadernetas de poupança:

“Nos anos 1980 e 1990, quando o Brasil passava por um período de hiperinflação, a preocupação das pessoas não era poupar. Era comer. A inflação era absurda, girava em torno de 80% ao mês. E quais consequências isso trazia? As famílias iam aos supermercados de manhã e, à tarde, os preços já haviam subido. Poupar era um luxo.”

Após esse período, os governos seguintes conseguiram retomar o crescimento e com o plano real veio o poder de compra, as pessoas que tiveram seus desejos reprimidos durante anos, podiam comprar bens de desejos como TVs, geladeira, fogão. Nesse momento, de novo, poupar também não era uma prioridade.

Segundo Thales Becker, chefe de marketing da empresa Acordo Certo, “existe um pensamento muito enraizado de que produtos como cartão de crédito e cheque especial são uma extensão da renda, e isso leva as pessoas a não terem consciência de que estão gastando mais do que ganham”.

Esses são alguns dados que mostram o quão difícil é para o brasileiro guardar e investir seu dinheiro pensando a longo prazo.

Porém, dados recentes mostram o que pode ser o início de uma mudança no comportamento dos brasileiros em relação ao mercado de investimentos. Segundo o último Raio-X do investidor brasileiro, realizado pela Anbima em 2020, os reflexos da pandemia provocaram redução do consumo.

A redução forçada de alguns gastos como: viagens, festas, idas a bares e restaurantes, fizeram com que mais pessoas tivessem economias, mesmo que involuntariamente. Enquanto que em 2019, 12 milhões de brasileiros disseram economizar, em 2020 esse total saltou para 20 milhões. Pela primeira vez a poupança perdeu força e outros produtos financeiros foram mais utilizados. Os rendimentos baixíssimos oferecidos pela poupança podem ter sido o principal motivo desta queda neste produto de investimento.

## Problema de Negócio

Nossa fintech é nova no mercado de investimentos brasileiro, e está completando seu primeiro ano de operação. Embora tenha tido um faturamento de acordo com o esperado no período, o plano de longo prazo prevê um aumento de 10% no faturamento no segundo ano de operação e com base em todo esse contexto, acreditamos que podemos oferecer nossos serviços para um novo público e crescer ainda mais em market share.

Para atingir os objetivos estratégicos, estamos investindo na criação de uma área de data analytics, cuja principal missão será apoiar na criação de dashboards e análises que ajudem em uma tomada de decisões mais assertiva (data informed).

E é com base nesses dados que o primeiro desafio da nova equipe de dados é apoiar a Diretoria Comercial na criação de uma estratégia mais eficiente para a conversão de novos clientes. Espera-se que uma estratégia baseada em análise de dados contribua para o atingimento da meta de faturamento da empresa.

Nesse momento, entendeu-se que a atual estratégia de marketing é massificada, ou seja, as mesmas peças/propagandas são enviadas para toda a base de potenciais clientes.

Após coletar os dados iniciais, uma segunda conversa com a diretoria comercial trouxe mais clareza sobre a expectativa de resultados da análise proposta: a empresa quer aumentar o percentual de conversão das campanhas de marketing, buscando atingir o valor considerado benchmark no mercado de investimentos. Com isso, a expectativa é converter mais clientes com o mesmo orçamento do primeiro ano de operação.

Diante da compreensão do problema e principal objetivo de negócio, as seguintes hipóteses foram levantadas:

- Segmentar o público das campanhas baseado apenas em variáveis sócio demográficas terá um impacto positivo no percentual de conversão das campanhas.
- Ter conhecimento sobre os produtos financeiros disponíveis no mercado influencia no investimento dos mesmos.
- Uma estratégia de segmentação de leads em clusters pode aumentar a conversão das campanhas de marketing, gerando um impacto positivo no faturamento da empresa.

A partir das hipóteses, surgiram as seguintes perguntas:

- Qual o perfil dos investidores brasileiros (sexo, localização, escolaridade, idade)?
- Algum dos dados desse perfil possui uma forte correlação com o status de investidor?

## Fonte de dados

Para nos apoiar em melhores decisões para esse case, usamos como fonte de dados a última pesquisa da Anbima, realizada em 2020. Essa base, por conta da pandemia, contou com a metodologia de pesquisa por telefone, e obteve 3.048 respostas de pessoas com 16 anos ou mais, das classes A, B e C, economicamente ativas, aposentadas ou que vivem de renda. Estima-se que esse perfil corresponda a 103,5 milhões de habitantes.

O levantamento foi realizado entre os dias 17 de novembro e 17 de dezembro de 2020. A margem de erro máxima para o total da amostra é de 2 pontos percentuais, para mais ou para menos, no nível de confiança de 95% — Anbima.

## Análise Exploratória

A fase inicial de busca por insights e respostas para as hipóteses e perguntas de negócio compreendeu a análise exploratória do nosso banco de dados (EDA). Para que fosse possível distinguir as características de quem é investidor e quem não é, primeiramente foi necessário criar uma nova coluna auxiliar em nosso DataFrame, com uma variável dummy que indicasse a qual grupo o registro da amostra pertencia, usando como referência as respostas para a pergunta “dos tipos de investimentos que você conhece, em qual deles você aplica atualmente?”. Definimos como investidores todos aqueles maiores de 18 anos que respondiam ao menos a uma das seguintes opções:

- Caderneta de poupança;
- Fundos de investimentos;
- Títulos de renda fixa privados;
- Títulos de renda fixa públicos;
- Ações na bolsa de valores;
- Plano de previdência privada;
- Moedas estrangeiras;
- Moedas digitais.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*9L4FYwf-pCqbGNta)

Os não investidores, por sua vez, são aqueles que possuem qualquer outro tipo de investimento que não faça parte do mercado financeiro, como ouro, compra e venda de imóveis, abrir o próprio negócio, consórcio, título de capitalização, compra e venda de produtos, agronegócio, agropecuária, agricultura, seguros, etc.

A partir dessa segmentação, constatou-se que 51% dos respondentes são investidores, sendo 54% homens e 46% mulheres. A média de idade dos investidores no Brasil é de 42 anos, sendo que o grau de escolaridade dessas pessoas obedece a seguinte distribuição: 24% tem pós-graduação completa, 36% tem ensino superior completo e 22% ensino médio completo. A região em que a maior parte dos investidores estão é a sudeste, com 48% do total, seguido por nordeste (17%), sul (15%), centro oeste (14%) e norte (4%). Deste total, 86% trabalham e têm atividade remunerada.

O que mais nos chamou atenção é que 27% dos investidores investem somente em Caderneta de Poupança, 5% alocam seus investimentos em Fundos de Investimentos e Títulos Privados, 3% no Tesouro Direto e, por fim, 3% na Bolsa de Valores. Ou seja, existe uma grande oportunidade de captarmos não só novos investidores, mas também pessoas que já investem em produtos como a poupança e podem passar a investir nos demais produtos que uma corretora de investimentos oferece.

Diante dessa observação, decidiu-se analisar separadamente o perfil de quem investe somente em poupança, no intuito de compará-lo com os outros dois grupos já segmentados (investidores e não-investidores). Logo, novamente foi necessário criar uma nova coluna auxiliar com variável dummy, que indicasse esta característica a partir da mesma coluna de respostas. Uma vez concluída essa etapa, foram elaborados gráficos para os principais atributos demográficos, permitindo a comparação dos três grupos de forma visual.

![](https://miro.medium.com/v2/resize:fit:1110/format:webp/0*Y2njMtd9BuTvhU6e.png)
![](https://miro.medium.com/v2/resize:fit:1182/format:webp/0*2-4QBCBhlk0c4gEd.png)
![](https://miro.medium.com/v2/resize:fit:1100/format:webp/0*N_i_NBAkyvngd2Ws.png)
![](https://miro.medium.com/v2/resize:fit:1138/format:webp/0*GLAjVj_cxlm5H_zs.png)
![](https://miro.medium.com/v2/resize:fit:1286/format:webp/0*7BY-YXpYckRgT0ng.png)

Ao analisar os gráficos, não é possível apontar alguma diferença nítida entre os grupos, pois a distribuição dos resultados acaba sendo muito semelhante em todos os casos. De maneira geral, o sexo é distribuído praticamente 50% masculino e 50% feminino, a idade tem maior concentração na faixa adulta dos 31 aos 45 anos, 80% das pessoas tem até 2 filhos, a média de renda está na faixa de 2 a 3 salários mínimos e 60% das pessoas tem escolaridade entre ensino médio completo e ensino superior completo.

No entanto, quando deixamos de lado as variáveis demográficas e analisamos outros fatores referentes ao mercado financeiro de maneira mais específica, percebemos que o conhecimento sobre produtos financeiros é o que melhor distingue os grupos. Para quem não investe, cerca de metade conhece algum produto financeiro (48%). Quando desconsideramos conhecimento apenas sobre poupança, a quantidade cai para 37%. Para quem só investe em poupança, também aproximadamente metade conhece algum outro produto financeiro além da própria poupança (52%). Já quem investe em produtos que não sejam apenas poupança, 89% tem conhecimento sobre produtos financeiros. Logo, ter conhecimento sobre os produtos financeiros disponíveis no mercado pode influenciar as pessoas a investirem neles.

![](https://miro.medium.com/v2/resize:fit:1188/format:webp/0*FPUbzMrZi8OE0CXr.png)

## Análise Clusterizada

Trabalhamos de forma mais aprofundada nas técnicas de machine learning de aprendizado não supervisionado, usada para dividir conjuntos de grupos de dados mais significativos, obtendo melhor compreensão dos dados e como as diferentes variáveis se relacionam.

Utilizamos a ferramenta do Google, o Collaboratory, como notebook sob a sintaxe da linguagem Python e o auxílio de algumas funções, módulos e bibliotecas, para formular estratégias de possíveis perfis de investidores.

Iniciamos nossas análises utilizando uma técnica de transformação de dados, que é uma prática para evitar que seu algoritmo fique enviesado para as variáveis de maiores com maior ordem de grandeza. Essas técnicas são importantes para conseguir que o modelo obtenha uma acurácia satisfatória.

Para a padronização dos dados utilizamos StandardScaler e para normalização o MinMaxScaler. Basicamente, a diferença entre eles é que padronizar as variáveis resultará em uma média igual a 0 e um desvio padrão igual a 1 e normalizar as variáveis dentro de um intervalo de 0 e 1, para aqueles que tiverem um resultado negativo -1 e 1.

![](https://miro.medium.com/v2/resize:fit:1242/format:webp/0*ycukX29QWNRFGh-g)
![](https://miro.medium.com/v2/resize:fit:1152/format:webp/0*ajXi-Biatc7iXDq2)
![](https://miro.medium.com/v2/resize:fit:1152/format:webp/0*ajXi-Biatc7iXDq2)

Criamos um dataframe com o nome ‘vet_x’, utilizando somente as colunas que vão ser clusterizadas, que serão ‘Status_investidor’, ‘P9A’, ‘RENDAF’. Cada coluna equivale:

- P9A: tipo de investimento que possuem;
- Status_investidor: coluna criada de acordo com nossa análise exploratória, separamos em investidores aqueles que possuem algum tipo de investimento, como poupança, CDB, renda fixa, … E para não investidores, aqueles que possuem investimentos em carros, imóveis, empresa própria …;
- RENDAF: soma da renda individual dos moradores do mesmo domicilio.

Para clusterização, utilizamos o algoritmo k-means que agrupa dados, tentando separar amostras em n grupos de variância igual, minimizando um critério conhecido como inércia ou soma dos quadrados dentro do cluster.

O algoritmo k-means tem como objetivo escolher centroides que minimizem a **inércia**, ou **critério de soma de quadrados dentro do cluster**:

![](https://miro.medium.com/v2/resize:fit:582/format:webp/0*xi7ByFz4vC_J98wu)

**E como saber quantos clusters podemos formar em nossa amostra?**

Quando não sabemos quantos clusters nossas amostras podem formar, nós precisamos utilizar uma forma de validar o que encontramos no lugar do “chutômetro”.

Antes de iniciarmos com o k-means, utilizamos o método Elbow, que se trata de uma técnica para encontrar o valor ideal do parâmetro k. Basicamente o método testa a variância dos dados em relação ao número de clusters.

Como o k-means calcula a distância das observações até o centro do agrupamento que ela pertence, o ideal é que essa distância seja a menor viável.

No gráfico abaixo utilizamos a função da soma de quadrados intra-clusters para nossos dados terem este resultado abaixo:

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*QMLBPvz-2i_putkr)

No gráfico acima, cada ponto representa uma quantidade de clusters. Após vários testes com as colunas ‘RENDAF’, ‘Status_investidor’, ‘P9A’, ‘SEXO’, ‘IDADE’, ‘REGIAO’ e ‘ESTADO’’, chegamos a conclusão de utilizar somente as seguintes colunas: ‘RENDAF’, Status_investidor’ e ‘P9A’, com divisão de 5 grupos e um valor de Silhueta de 0,96. As outras combinações obtidas apresentaram um valor de Silhueta muito baixo comparando a esta relação.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*V22WzyBHTqu5Iwqu)

O gráfico abaixo apresenta uma visualização mais clara dos clusters obtidos:

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*iOqdBwjChuAPzZ-T)

Analisando cada cluster gerado a partir do método k-means, obtivemos a seguinte distribuição:

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*_6OP0FNWw5DlVJwi)

A principal subdivisão foi grupos de investidores e não investidores correlacionado ao tipo de investimento que possuem. Para o grupo de investidores a principal diferença é o tipo de investimento, sendo que um grupo não possui Bitcoin e Criptomoedas. Já para o grupo de não investidores, o K-means dividiu-se em grupos que não utilizam nenhum tipo de investimento, outras respostas, não lembra/sabe e os que possuem algum tipo de investimento fora do mercado financeiro.

Como já havíamos analisado a divisão entre os fatores de sexo, idade e nível de escolaridade não são informações relevantes ao nosso contexto, se mostrando com pouca ou nenhuma diferença nos valores,

Considerando os grupos que não fazem sentido ao perfil que procuramos, o K-means foi muito eficiente na distribuição dos não investidores, pois não faz sentido termos pessoas que não investem, não declaram alguma resposta e outras respostas.

**Hipótese 1: Segmentar o público das campanhas baseado apenas em variáveis sócio demográficas terá um impacto positivo no percentual de conversão das campanhas.**

A primeira hipótese visava nos dar um direcional de segmentar a base por resultados sócio demográficos para que pudéssemos ter indícios de algum grupo mais propenso a virar investidor. Mas olhando somente para os dados demográficos de forma separada, essa hipótese foi refutada, conforme mostrou a análise exploratória. Todos os gráficos ficaram bem similares e pouca diferença foi notada nos quesitos: gênero, idade, pessoas com filho, renda e escolaridade.

**Hipótese 2: Ter conhecimento sobre os produtos financeiros disponíveis no mercado influencia no investimento dos mesmos.**

Essa hipótese se confirma com nossa análise exploratória, é verdade que quanto mais se conhece sobre produtos financeiros mais se investe. “Para quem não investe, aproximadamente metade conhece algum produto financeiro (48%). Quando desconsideramos conhecimento apenas sobre poupança, a quantidade cai para 37%. Pra quem só investe em poupança, também aproximadamente metade conhece algum outro produto financeiro além da própria poupança (52%). Já quem investe em produtos que não sejam apenas poupança, 89% tem conhecimento sobre produtos financeiros.”

Dessa forma, entendemos que aqui pode estar nossa maior direcional para a estratégia de novos clientes, pensar em estratégias para aumentar o conhecimento sobre produtos financeiros e consequentemente ter maior chance de clientes.

**Hipótese 3 — Uma estratégia de segmentação de clientes em clusters pode aumentar a conversão das campanhas de marketing, gerando um impacto positivo no faturamento da empresa.**

Esta hipótese pode ser considerada positiva quando nos referimos à aquisição de novos prospects para as campanhas de marketing. Notamos que temos 2 perfis de investidores com uma única diferença: um grupo investe em Criptomoedas e Bitcoin. Além disso, conseguimos analisar que podemos realizar campanhas para converter os perfis de não investidores que possuem algum tipo de investimento externo, levando um impacto mais positivo no faturamento da empresa.

## Conclusão

Considerando o resultado para as nossas hipóteses, podemos seguir com a nossa estratégia comercial da seguinte forma:

1. Não segmentar nosso público por perfil demográfico, mas segmentar por nível de conhecimento para investimentos financeiros;
2. O K-means se apresentou com bons resultados para 5 grupos de clusters, com um coeficiente de silhueta de 0,95, com perfis de possíveis investidores para a prospecção de novos clientes;
3. Diante dos resultados dos clusters, podemos desconsiderar os grupos de não investidores que não possuem nenhum tipo de investimento e não lembram/sabem e fazer uma nova clusterização em cima dos grupos de investidores e não investidores que possuem algum tipo de investimento, para conseguir gerar novos insights.

## Próximos Passos

Para que a Diretoria Comercial da empresa consiga tirar proveito da análise realizada, sugerimos as seguintes atividades como próximos passos:

1. **Execução de um teste A/B:** utilizando essa metodologia, será possível avaliar qual a estratégia mais eficaz para o aumento da conversão das campanhas de marketing: segmentar conforme o nível de conhecimento sobre o mercado financeiro, ou de acordo com os clusters propostos pelo método k-means. Espera-se que esse teste ajude a validar as novas propostas com um baixo orçamento, e sem causar impacto significativo na atual taxa de conversão.
2. **Criação de um dashboard para a equipe de marketing:** criar um painel onde a equipe de marketing consiga acompanhar diariamente a evolução do indicador de conversão das campanhas.
3. **Criação de um novo produto para o nosso negócio, focado em educação financeira:** com base nas análises e conclusões alinhamento com a equipe de marketing para desenvolvimento de conteúdo para educação financeira como: vídeos, ebooks, perfil social.
4. **Nova Clusterização:** Visando personalizar ainda mais a jornada do cliente e aumentar a conversão, podemos fazer uma nova clusterização e entender novos perfis.



