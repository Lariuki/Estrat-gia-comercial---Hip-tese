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

<https://miro.medium.com/v2/resize:fit:1400/format:webp/0*9L4FYwf-pCqbGNta>


