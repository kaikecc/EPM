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

Para criar uma nova conexão com um servidor OPC UA, basta clicar no botão Edit.

![alt-text](https://github.com/kaikecc/EPM/blob/main/Coleta%20de%20dados/img/opc-ua.png)


Em seguida, clicar em Custom Discovery, a porta é a mesma que o EPM utiliza.

* Discovery Server URL: opc:tcp://endereco:porta
* Escolher a maneira de comunicar: None
* Colocar as credenciais de acesso e realizar o Test Connection.







