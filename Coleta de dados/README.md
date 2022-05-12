# Coleta de dados


## Interface de Comunicação OPC-DA

> OPC Data Access é um grupo de padrões cliente-servidor que fornece especificações para comunicação de dados em tempo real de dispositivos de aquisição de dados , como PLCs , para dispositivos de exibição e interface, como Interfaces Homem-Máquina (IHM), sistemas SCADA [2] e também ERP / Sistemas MES . [3] As especificações centram-se na comunicação contínua de dados. 

Fonte: [OPC Data Access](https://en.wikipedia.org/wiki/OPC_Data_Access)

1. Timestamp:

2. Redundancy Options:

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








