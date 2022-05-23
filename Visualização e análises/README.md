# Model

## Contextual Model

Permite criar uma hieraquia de pastas para organizar as variáveis. Pode-se carregar a pasta toda para um gráfico que mostrará o itens dessa pasta.

## EPM Model

Em Custom Types é onde cria-se as definições de objetos que existirá no EPM Model.

1. Clique com o botão direito do mouse em CustomTypes e selecione o item Edit Items..
2. Clique em Add Type e crie o tipo Compressor, selecionando a imagem compressor.png
disponibilizada como pré-requisito.
3. Clique com o botão direito no objeto Compressor e escolha a opção Add Property.
4. Adicione a propriedade Ligado com o tipo Alias.
5. Adicione a propriedade Setpoint com o tipo Alias.
6. Crie um novo tipo chamado Room, utilizando o ícone room.png.
7. No tipo Room, insira o tipo Compressor como um placeholder. Desta forma, o tipo Room
está habilitado para ter filhos do tipo Compressor nas instâncias.
8. Adicione a propriedade Temperatura com o tipo Alias.
9. Adicione a propriedade Localidade com o tipo Simple.

## Chart Analysis

É uma ferramenta do EPM que permite que se visualise os dados em um gráfico com vários recursos que seja possível fazer uma análise exploratório dos dados. Os objetos do ChartAnalysis podem ser visíveis tanto Local como Server (para todos). Os dados apresentados nos Charts são hibrídos, isto é, real time (linha fina) e armazenado (linha grossa). Os dados mostrados no chart são otimizados para um ter um bom desempenho (para não travar na hora de carregar os dados) para ver o comportamento da variável.

## Dataset Analysis - Agregações

Os objetos datasets são conjuntos de dados que pode ser escolhidos para realizar análises mais aprofundadas. Diferentemente do ChartAnalysis, cria-se um perído no tempo que deseja ser analisados, após inserir a variável no Dataset deve definir o período de consulta seja um **Recent Period** ou no **Time Interval**, em seguida deve-se definir o tipo de agregação em **Raw**.



1. Raw:  São dados brutos (SEM AGREGAÇÃO);
2. Trend: É tipo de agregação que o ChartAnalysis utiliza para colocar os dados em gráfico;
3. Interpolative: Retorna os valores interpolados no início de cada intervalo, utilizando para o cálculo
os valores anteriores e posteriores à estampa de tempo solicitada. Permite que fixe um intervalo (Sample Interval) entre cada ponto existente;
4. Avarage: Retorna a média aritmética dos dados do intervalo solicitado, considerando apenas
os valores com qualidade boa.Média Aritmética Simples;
5. Time Avarage: Retorna a média ponderada pelo tempo em que a variável permaneceu nos valores,
usando o método Interpolated Bouding Values para calcular os dados nos limites
do intervalo solicitado. Média ponderada no Tempo. (RECOMENDADO).
6. Duration in State Zero: Retorna a quantidade de tempo, em milissegundos, em que a variável Booleana ou
numérica esteve em zero. Tempo que permaneceu em zero dentro do intervalo de amostragem. (UTILIZAR PARA MANUTENÇÃO SOBRE TAL VARIÁVEL)
7. Time Avarage 2: Retorna a média ponderada pelo tempo em que a variável permaneceu nos valores,
usando o método Simple Bouding Values para calcular os dados nos limites do
intervalo solicitado. Melhor opção para variáveis discretas.

Para mais informações consultar o padrão [OPC UA](https://reference.opcfoundation.org/v104/Core/docs/Part13/5.4.3/).

OBS: O Publish Interval é o tempo para aquisição dos dados em Real Time.





