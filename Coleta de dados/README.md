# Coleta de dados

## Interface de Comunicação E3

A seguir mostra as opções gerais para todas as interfaces.

1. Timestamp: É o tempo em que o dado foi gerado. Porém, pode escolher o Interface Server Machine Clock.
2. Enable Storage: Os dados coletados por meio dessa interface de comunicação poderão ser gravados pelo EPM.
3. Redundancy Options: Permite que uma interface possa ser tratada por mais de um interface server. Os interfaces server podem estar em diferentes servidores podendo selecionar o Primário e Secundário quando for **Activate** e de acordo com Failover trigger. **RECOMENDAÇÃO:** Criar uma tag watchdog no E3 para ficar sendo monitorada.


No caso da comunicação do E3:

* Read-Only: Compatibilidade dos produtos Elipse em que habilitação desse item otimiza a comunicação.
* Browse Properties: Escolhe as propriedades de interesse para serem enviados.
* Disable queue's auto adjustment: Sinaliza ao operador que a tag está em alteração como colocar a TAG em vermelho por exemplo.



## Interface de Comunicação OPC-DA

> OPC Data Access é um grupo de padrões cliente-servidor que fornece especificações para comunicação de dados em tempo real de dispositivos de aquisição de dados , como PLCs , para dispositivos de exibição e interface, como Interfaces Homem-Máquina (IHM), sistemas SCADA [2] e também ERP / Sistemas MES . [3] As especificações centram-se na comunicação contínua de dados. 

Fonte: [OPC Data Access](https://en.wikipedia.org/wiki/OPC_Data_Access)

A seguir mostra as opções de configuração da interface OPC DA.


* Local OPC Server: opcda://localhost/Nome.OPC/{id}
* Subscription: Recebe valores somente quando há alterações na variável. O E3 trabalha com essa opção. É sempre recomendado utilizar essa opção, caso exista limitação do OPC DA devida a versão, então utilizar o polling.
* Read (polling): Independente da mudança na variável, é carregado um novo valor quando ocorre a varredura no **Publishing Interval**.

![alt-text](https://github.com/kaikecc/EPM/blob/main/Coleta%20de%20dados/img/opc-da.png)

## Interface de Comunicação OPC-UA


> Um padrão de interoperabilidade para a troca de dados segura e confiável no espaço de automação industrial e em outras indústrias. É uma plataforma independente que garante o fluxo de informação contínuo entre os dispositivos de diversos fornecedores.

Fonte: [OPC UA](https://www.logiquesistemas.com.br/blog/opc-ua/)

O OPC-UA tem vantagem por comunicação sempre através de Subsciption.

Para criar uma nova conexão com um servidor OPC UA, basta clicar no botão Edit.

![alt-text](https://github.com/kaikecc/EPM/blob/main/Coleta%20de%20dados/img/opc-ua.png)


Em seguida, clicar em Custom Discovery, a porta é a mesma que o EPM utiliza.

* Discovery Server URL: opc:tcp://endereco:porta
* Escolher a maneira de comunicar: None
* Colocar as credenciais de acesso e realizar o Test Connection.

* Operation Timeout (ms): Defini um tempo limite em millisegundos de aguardo.
* Session Timeout (ns): Defini o tempo máximo de duração de uma sessão ociosa.

## MQTT

> O MQTT é um protocolo de mensagens padrão OASIS para a Internet das Coisas (IoT). Ele foi projetado como um transporte de mensagens de publicação/assinatura extremamente leve, ideal para conectar dispositivos remotos com um pequeno espaço de código e largura de banda de rede mínima.

![alt-text](https://github.com/kaikecc/EPM/blob/main/Coleta%20de%20dados/img/mqtt-publish-subscribe.png)

Fonte: [MQTT](https://mqtt.org/)

> A Interface de Comunicação MQTT permite a coleta de dados de qualquer dispositivo que opera com o protocolo
MQTT ao se conectar a um Broker, tipicamente um dispositivo de Internet das Coisas (IoT) ou Internet das Coisas da
Indústria (IIoT).

Fonte: [epmmanual](https://github.com/kaikecc/EPM/blob/main/manual/epmmanual_ptb.pdf)

Para a integração do protocolo do MQTT com a interface Elipse é necessário configurar uma conexão com Broker e definir o formato da
estampa de tempo e da qualidade, criar as consultas de tópicos e criar o mapeamento entre as inscrições nos tópicos
e endereços desta Interface de Comunicação, que podem ser posteriormente utilizados pelas Basic Variables na
Configuração de Fonte de Dados.

Clique em Edit para abrir a janela de configuração. As opções desta janela são mostradas na figura a seguir.


![alt-text](https://github.com/kaikecc/EPM/blob/main/Coleta%20de%20dados/img/mqtt-broker.png)

No [epmmanual](https://github.com/kaikecc/EPM/blob/main/manual/epmmanual_ptb.pdf) p. 70, apresenta uma tabela **Configurações do Broker** onde mostra a descrição dos itens da Figura acima.

Para o funcionamento do MQTT com o EPM é preciso formatar os dados. Todo dado no EPM possui:

* Timestamp (momento em que o dado foi gerado);
* Qualidade (definido pela padronização da norma OPC UA);
* Valor.

Em seguida, realizar um insert onde criará queries que serão executadas no Broker para solicitar os dados para o EPM.

# Interface de Comunicação Database

# Restauração da base de dados E3

Para isso, siga os passos a seguir:

1. Se você não possui o SQL Server Management Studio instalado, faça a instalação através do
link [SSMS-Setup-PTB](https://aka.ms/ssmsfullsetup).

2. Abra o SQL Server Management Studio e faça a autenticação com seu usuário e senha.
3. Execute o login no SQL Server Management Studio.
4. Clique com o botão direito do mouse no item Databases e selecione a opção Restore
Database.
5. No item Source, selecione a opção Device e localize o arquivo de backup.
6. Clique em OK para iniciar a restauração da base de dados.
7. Após executar a operação com sucesso, feche o SQL Server Management Studio.

## Redudância de Interfaces

1. Após criar um servidor para ser a redundância do servidor primário, clique na opção **Redundancy Options**. OBS: no servidor secundário foi instalado um novo interface server.

2. Insira o segundo interface server;
3. Na aplicação do E3 foi criada uma tag de monitoramento de conexão que verifica o relógio da máquina e é atualizada a cada  1 segundo.
4. Existem três maneiras de fazer a troca de interfaces server: manual, monitor interface server connection e monitor watchdog tag. Nesse caso, é indicado usar o watchdog tag.
5. Selecione as opções Assume if Bad quality, Assume if no value change e defina uma Latency.











