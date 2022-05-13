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



![alt-text](https://github.com/kaikecc/EPM/blob/main/Tratamento%20e%20armazenamento%20dos%20dados/img/basic-edit.png)

Na aba de **Processing**, pode-se configurar a escala original dos dados de Input Low Limit e Input High Limit independente do **Clamping**. Pode-se configurar o **Dead Band**

Na aba de **IO Data** mostra de qual fonte de dados está vindo essa variável.

Na aba de **Storage** cuida do armazenamento da variável. Onde o **Record** habilita a gravação que é útil para visualização em gráfico e consulta via API dessa variável.

**NOTAS**:

* Todas as alterações efetuadas nas abas de propriedades, seja para qual item for, só
são efetivamente utilizadas pelo Sistema EPM quando salvas. A operação de
salvamento do conteúdo editado consiste em enviar ao EPM Server as novas
informações, tornando-as disponíveis para todo o sistema.

* Os Tags que não estiverem vinculados a uma fonte de dados são apresentados na
tabela com a cor do texto em vermelho.

* A coluna RT-Timestamp, que mostra a estampa de tempo do último valor recebido
pela via de tempo real, possui o formato Ano-Mês-DiaTHora:Minuto:Segundo. Este
formato é utilizado pois suporta ordenação, ou seja, é uma coluna do tipo Sortable.

* O nome de um Tag deve ser único entre os Data Objects, ou seja, tanto entre as Basic
Variables quanto nas Expression Variables.

* A configuração correta das propriedades Domain e Cast Type é fundamental na aba
General.

* A propriedade Domain pode interferir no resultado de consultas processadas,
portanto configure-a corretamente desde o início.

* Sempre que possível configure a propriedade Cast Type para o tipo de dados mais
apropriado, pois este interfere diretamente no espaço de armazenamento. Por
exemplo, um tipo de dados Float ocupa metade do espaço de um tipo de dados
Double, e o primeiro costuma atender a maioria dos casos. Da mesma forma que um
tipo de dados Int ocupa apenas o espaço necessário para representar o valor em
questão.

* Não é recomendável mudar o valor da propriedade Cast Type ao longo da vida de
uma Basic Variable. Configure-a corretamente desde o início.

* Em geral, todos os Tags que pertencem a um mesmo tipo de variável de processo
(temperatura, pressão, vazão, etc.) compartilham um mesmo Storage Set.

* Se um Storage Set em uso por algum Tag é removido, os dados do Tag continuam a
ser armazenados, porém sem passar pelo algoritmo de compressão, até que um novo
Storage Set seja atribuído.

* A opção de armazenar os dados com precisão de milissegundos na estampa de
tempo consome mais espaço em disco. Portanto, se não é necessária esta precisão,
recomenda-se desmarcá-la.

## Eventos

1. Schedule: Dispara um evento dentro de um momento programado (horário do servidor UTC).
2. Period: Dispara eventos ciclícos.
3. Advanced: Dispara de acordo com uma fonte, uma variável. Ocorre de acordo com a condição em Filter.
4. AckEvents: Mesma funcionalidade do Advanced, porém pode-se selecionado o evento ocorrido no Monitor pode reconhecer o evento adicionando um comentário.

## Expression Variables

Serve para criar cálculos de indicadores, KPIs dentro EPM baseado nas variáveis que ele está recebendo. Na opção Test é possível avaliar a sintáxe do cálculo que é feito em Python.

Na aba de Execution Trigger pode-se escolher o momento do cálculo, sendo por mudança de alguma variável ou através de um evento.


