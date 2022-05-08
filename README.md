# EPM
Elipse Plant Manager - (PIMS)

O Elipse Plant Manager (EPM) é um software Plant Information Management System (PIMS) que possui ferramentas que coletam dados de todos os processos da empresa e transmite para uma base única (historiador). Através do EPM, é possível observar e analisar os dados para que possa realizar as melhores decisões sobre o processo. 

## Estrutura e Arquitetura do EPM


1. Coleta
2. Armazenamento e Tratamento dos Dados
3. Visualização e Análise dos Dados


Na camada da coleta dos dados possui o **EPM Interface Server** (1) que o software EPM responsável pela aquisição dos dados sendo instalado junto a origem do dado através de algum interface de comunicação OPC, DB, E3Gtw entre outros. O EPM Interface Server possui um buffer (espaço de memória) que caso aconteça algum problema no envio dos dados para o **EPM Server** (2) fique guardado temporariamente até que seja restabelecido o envio. O EPM Server fica conectado a base de dados definitiva em SQL Server em um servidor diferente do EPM Interface Server. Na Figura abaixo mostra o fluxo de dados desde fonte até o EPM Server, perceba que do Interface Server até o Server existe a forma real time data sem nenhum tratamento, mas existe a opção de ser tratado e armazenado no buffer e transmitido de forma assíncrona.  

![alt-text](https://github.com/kaikecc/EPM/blob/main/img/Fluxo%20de%20Dados.png "Fluxo de Dados")


Na Figura abaixo mostra duas opções de configurações do fluxo de dados do Interface Server até o EPM Server seja em real time ou assíncrona.

![alt-text](https://github.com/kaikecc/EPM/blob/main/img/Interface-Server-Page-2.drawio.png "Interface - Server")

O EPM Studio (3) é a ferramenta para configuração do sistema EPM e também para visualização e análise dos dados e o EPM Add-in (3) é uma extensão para o Excel para fazer a consulta e visualização dos dados para ser tratado. O EPM Portal (3) é uma ferramenta para visualização dos dados em dashboards, além de outros como o Elipse Mobile Server e E3 Viewer.

### Ordem de Instação das ferramentas EPM

1. SQL Server;
2. EPM Server;
3. EPM Interface Server (para cada fonte de dados);
4. EPM Studio (máquina de gestão do sistema);
   