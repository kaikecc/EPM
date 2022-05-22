## DataObjects

1. Basic Variables

São objetos criados pelo EPM para receber os dados dos processos. Cada Basic Variable criada pode-se associar a um endereço de uma fonte de dados. Por padrão, na tela de Basic Variable não são carregados nenhuma basic variable conforme a Figura abaixo, porém pode-se aplicar os filtros no Nome e Desrição, além disso ao clicar em Filter carrega todas as variáveis.

![alt=text](https://github.com/kaikecc/EPM/blob/main/Tratamento%20e%20armazenamento%20dos%20dados/img/basic-variable.png)


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

## Compressão de dados

O algoritmo que o EPM utiliza para compressão de dados é chamado de BOX CAR BACK SLOPE ([BCBS](https://kb.elipse.com.br/en/data-compression-algorithms-in-process-historians-with-commercial-databases/)). Tem como objetivo dimunuir espaço em disco de armazenamento e torna a consulta ao dados eficiente. Cuidado na hora de configurar o valor do Deviation, pois pode acarretar em banda morta muito grande ao ponto de perder o comportamento da variável ou uma banda morta pequena que deixa anular a eficiência do algoritmo de compressão.

## Storageset

É um objeto de configuração do algoritmo BCBS para compressão de dados do EPM. Criando um storageset pode-se utilizar em diversas variáveis. É importante conhecer o comportamento das variáveis e da medida.

* Min. Time: Tempo mínimo que o algoritmo tem para verificar se excedeu o Deviation. (Ex. Quando mede-se uma vazão o ínício da leitura é instável e gravaria muitas vezes o valores até estabilizar, para isso coloca-se um tempo mínimo para executar o algoritmo BCSBS).
* Max. Time: Tempo máximo que forçaria o algotimo a ser executado. (Ex. Quando passa muito tempo sem armazenar uma variável por está constante, executa-se depois de um tempo máximo a leitura da variável).
* Slope Resolution: É o tempo que assegura que a representação da variável seja mais próxima da realidade.

## NOTA

* Em geral, todos os Data Objects que pertencem a um mesmo grupo/natureza de variável de processo (temperatura,
pressão, vazão, torque, etc.) compartilham um mesmo Storageset.
* Se é removido um Storageset que esteja sendo utilizado por algum Data Object, os dados destes Data Objects
continuam sendo armazenados, porém sem passarem pelo algoritmo de compressão, até que um novo Storageset
seja novamente atribuído a eles.
* Toda alteração efetuada em um Storageset só é efetivamente aplicada no momento em que é salva. Uma vez salva,
todos os Data Objects que compartilham o mesmo Storageset passam a utilizar as novas configurações.
* Toda vez que o valor de um Data Object mudar sua qualidade ele é armazenado, mesmo que ainda não tenha
transcorrido o tempo definido em Min. Time.



