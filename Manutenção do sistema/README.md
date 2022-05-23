## Propriedades do EPM Server

O sistema EPM funciona todo baseado no SQL Server e através do EPM Studio é possui acessar todos os recursos necessários para manutenção do EPM Server. Na aba **Management**, em seguida **Properties** pode-se verificar o funcionamento das configurações do Database do EPM.

* Server Name;
* Status;
* EPM System;
* Log File;
* Recovery Model;
* Size.

Em **Product Key Information** pode-se verificar versão atual do EPM Server, quantidade de I/Os Points ativas e registradas, as interfaces de comunicação disponíveis para uso, quantidade de sessões e do EPM Portal.

## Fazer backup do EPM

> Para garantir a disponibilidade do Sistema EPM, este fornece uma estrutura de cópias de
segurança, que podem ser utilizadas nos casos de problemas onde ocorreu perda de
informações. Assim, é possível realizar operações de backup de forma manual ou
automática, em que sempre recomendamos criar cópias de segurança de toda a estrutura
operacional (Interfaces de Comunicação, configurações de Tags e políticas de segurança,
entre outras) acrescida dos dados de processo, ou seja, o backup no modo Structure and
Data.


1. Clique em Configuration na aba Management da Faixa de Opções para abrir a aba
de configuração do backup.
2. O campo Path define o local onde está instalado o servidor de banco de dados do EPM,
para salvar o arquivo de backup. Mantenha o caminho padrão do SQL Server ou, se
desejar, selecione outra pasta.
3. No campo Backup type, selecione a opção Structure And Data. Este é o modo
recomendado para os backups do EPM.
4. Salve as alterações e clique em Execute na Faixa de Opções para gerar o arquivo de
backup no local informado. Sempre que esta opção é usada, o backup é executado,
mesmo que a opção Auto backup esteja selecionada.
5. Sempre que possível, verifique se o arquivo foi realmente gerado no caminho
especificado, como no caso da pasta padrão configurada na figura a seguir. Caso a pasta
tenha sido alterada, confirme se o arquivo de backup do EPM de treinamento foi gerado
no local selecionado.

NOTAS:

1. Os arquivos de backup que são gerados não devem ser guardados apenas na própria
máquina do SQL Server! O objetivo é justamente criar alternativas de recuperação em
caso de falha. Portanto é recomendável que o arquivo seja armazenado em pelo
menos uma máquina diferente de onde se encontra a base de dados original.
2. Quando um arquivo de backup é gerado, o nome é baseado na concatenação do nome
do banco de dados e das informações de data e hora de início do procedimento. O
formato do nome do arquivo é nomebancodedados_yyyymmdd_hhnnss.bak.
3. Só é possível selecionar um caminho de backup diferente do padrão se o usuário que o
EPM Server estiver usando para conexão com o banco é o usuário SA do SQL Server
ou algum outro com permissões de SysAdmin. Por uma questão de segurança, o SQL
Server não permite que seja realizada a varredura no sistema de arquivos da máquina
sem as condições citadas.
