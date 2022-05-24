## Propriedades do EPM Server

O sistema EPM funciona todo baseado no SQL Server e através do EPM Studio é possui acessar todos os recursos necessários para manutenção do EPM Server. Na aba **Management**, em seguida **Properties** pode-se verificar o funcionamento das configurações do Database do EPM.

* Server Name;
* Status;
* EPM System;
* Log File;
* Recovery Model;
* Size.

Em **Product Key Information** pode-se verificar versão atual do EPM Server, quantidade de I/Os Points ativas e registradas, as interfaces de comunicação disponíveis para uso, quantidade de sessões e do EPM Portal.

## Notificações do EPM Server

Um recursos útil para gestão do EPM Server são as notificações que podem ser enviadas automaticamente por e-mail sempre que ocorre algum evento. Primeiramente,
na aba **E-mail Configuration**, deve-se adicionar um e-mail padrão que o EPM Server utilizará para notificação, no entanto é necessário configurar um Server Address SMTP para isso.

Em seguida, na aba **Notifications** é onde configurar quais ocasiões serão enviados os e-mails. Os usuários que receberão as notificações devem ter os seus e-mails cadastros em **UserAdministration**. Ao criar uma NewNotification, selecione a aba **Filter** onde se define uma propriedade que deseja acompanhar.

## EPM Server - Backup

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

## EPM Server - Archives

O EPM guarda os dados em um sistema de arquivos. Em **Explorer**, em seguida selecione o item **Archives** e clicando em cima com botão direito do mouse escolha **Properties** que mostra as propriedades que aparecem no EPM Server Configuration Wizard.

* Base name;
* Path;
* Growth;
* Initial size;
* Maximum size.

OBS: Pode alterar os parâmentros de configuração, porém recomenda-se acompanhar a ocupação dos valores ao longo do tempo.

Para acompanhar a evolução do crescimento dos dados, clique com o botão direito do mouse em cima de Archives, em seguida selecione **Edit Archives**, que através disso é feita uma leitura do servidor do SQL.

* State: Quando em modo **Current** mostra que o arquivo está sendo utilizado.

Pode-se fechar o arquivo clicando em **Archive**, em seguida **Close** assim o arquivo não receberá nenhum dado.
