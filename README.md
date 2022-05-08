# EPM
Elipse Plant Manager - (PIMS)

O Elipse Plant Manager (EPM) é um software Plant Information Management System (PIMS) que possui ferramentas que coletam dados de todos os processos da empresa e transmite para uma base única (historiador). Através do EPM, é possível observar e analisar os dados para que possa realizar as melhores decisões sobre o processo. 

## Estrutura e Arquitetura do EPM


1. Coleta
2. Armazenamento e Tratamento dos Dados
3. Visualização e Análise dos Dados

### Coleta

Na camada da coleta dos dados possui o **EPM Interface Server** que o software EPM responsável pela aquisição dos dados sendo instalado junto a origem do dado através de algum interface de comunicação OPC, DB, E3Gtw entre outros. O EPM Interface Server possui um buffer (espaço de memória) que caso aconteça algum problema no envio dos dados para o **EPM Server** fique guardado temporariamente até que seja restabelecido o envio. O EPM Server fica conectado a base de dados definitiva em SQL Server em um servidor diferente do EPM Interface Server. Na Figura abaixo mostra o fluxo de dados desde fonte até o EPM Server, perceba que do Interface Server até o Server existe a forma real time data sem nenhum tratamento, mas existe a opção de ser tratado e armazenado no buffer e transmitido de forma assíncrona.  

![alt-text](https://github.com/kaikecc/EPM/blob/main/img/Fluxo%20de%20Dados.png "Fluxo de Dados")

