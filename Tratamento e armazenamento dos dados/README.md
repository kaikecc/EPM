## DataObjects

1. Basic Variables

São objetos criados pelo EPM para receber os dados dos processos. Cada Basic Variable criada pode-se associar a um endereço de uma fonte de dados. Por padrão, não são carregados nenhuma basic variable, porém pode-se aplicar os filtros no Nome e Desrição, além disso ao clicar em Filter carrega todas as variáveis.

Há duas formas de inserção de variávies: clicando no **Add** ou no **Import**. Ao utilizar a opção Import, abre-se o EPM Browser que permite realizar uma busca um endereço de interesse no servidor. Nesse servidor são mostradas todas as interfaces de comunicação e cada uma dessas interfaces possuem uma pasta chamada EPM Interface Statistics que retornam endereços sobre o funcionamento daquela interface.

* Name: não necessariamente tem que ser igual ao da fonte de dados, mas um nome que melhor indetifica essa variável na base de dados do EPM.
* Description: Descrição da variável.
* EU (Enginneering Unit): Unidade de Engenharia.
* Data Type: Tipo de dado do valor que última leitura trouxe.
* Active: Faz com que receba atualização dessa variável.
* RT: Tempo Real.
* REC: Gravação.
* Compression: Compressão dos dados.
* RT-Value: Valor em Tempo Real (Caso a variável esteja habilitada para RT).
* RT-Timestamp: Tempo Real do Timestamp.

Na Figura abaixa mostra as propriedades da variável.

* Domain: Continuos - representa a medida que a variável irá retornar para casos analógicos. Discrete - representa a medida booleana da variável 0 ou 1.
* Cast Type: Como se deseja tratar o valor recebido dessa variável.
* Enable Realtime: Caso necessite que a variável chegue ao EPM no tempo real (Não é aconselhado deixar habilidade sem a necessidade).
* Clamping: Como deve tratar o **Low Limit** e **High Limit** None - Não faz nada com os valores fora dos limites, Discard - Exclui os valores fora dos limites e Clamp Range - Coloca os valores que utrapassarem dentro do limite.

Na aba de **Processing**, pode-se configurar a escala original dos dados de Input Low Limit e Input High Limit independente do **Clamping**. Pode-se configurar o **Dead Band**

Na aba de **IO Data** mostra de qual fonte de dados está vindo essa variável.

![alt-text](https://github.com/kaikecc/EPM/blob/main/Tratamento%20e%20armazenamento%20dos%20dados/img/basic-edit.png)

