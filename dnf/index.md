---
layout: page
title: DNF
excerpt: "Aprendendo o DNF."
---

![jekyll Image](http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/02/1424055625jekyll.png)
{: .image-pull-right}

<center><b>O Gerenciador de Pacotes DNF</b><br> Aprenda a usar aqui.</center><br><br><br>
## Modo de usar:

{% highlight text %}
 dnf [options] <command> [<args>...] 
{% endhighlight %}   


<br><br><br>
## Descrição:

O DNF é o gerenciador de pacotes utilizado por padrão no sistema operacional Fedora, em conjunto com o RPM. Dá mesma forma que o seu predecessor YUM, o DNF torna possível realizar as mesmas tarefas administrativas no sistema, tais como: instalar pacotes, atualizar o sistema, apagar o cache de pacotes, remover pacotes, instalar pacotes localmente, dentre outros.<br><br>Lembrando que pacotes, são os binários empacotados, que tornam possível a instalação de um aplicativo, por exemplo, o Firefox. <br><br>O gerenciamento de pacotes no Fedora pode ser realizado com o RPM, sem o uso do DNF. Por exemplo, para remover algum pacote, no Terminal basta digitar: <rpm --erase 'pacote'>.
<br><br>
Comandos disponíveis;
<br><br>
* autoremove
* check
* check-update
* clean
* distro-sync
* downgrade
* group
* help
* history
* info
* install
* list
* makecache
* mark
* provides
* reinstall
* remove
* repoinfo
* repolist
* repoquery
* repository-packages
* search
* shell
* swap
* updateinfo
* upgrade
* upgrade-minimal
* upgrade-to

<br><br><br>
## Uso:

Nos métodos básicos, o DNF pode ser usado quase exatamente como o YUM para pesquisar, instalar ou remover pacotes: 

{% highlight text %}
# dnf search audacity 

# dnf install audacity 

# dnf remove audacity 
{% endhighlight %}   
<br><br><br>

## Atualizações automáticas:

O pacote RPM dnf-automatic como componente DNF fornece um serviço para download automático e instalação de atualizações. Ele pode monitorar e denunciar automaticamente via disponibilidade de atualizações por E-Mail ou enviar um registro sobre pacotes baixados e atualizações instaladas. 
<br><br><br>
## Upgrades do sistema:

Os produtos Fedora podem ser atualizados com o plugin de atualização do sistema DNF ou diretamente com o DNF.<br><br><br>

## Suporte de idiomas usando DNF:

O DNF pode ser usado para instalar ou remover suporte de idiomas.<br><br><br>
<hr size="5">
<br><br>

## Comando de remoção automática:

{% highlight text %}
# dnf [options] autoremove
{% endhighlight %} 

Remove todos os pacotes do sistema que foram originalmente instalados como dependências de pacotes instalados pelo usuário, mas que não são mais exigidos por nenhum desses pacotes. <br><br>

Os pacotes listados em <i>installonlypkgs</i> nunca são automaticamente removidos por este comando.<br><br>

{% highlight text %}
# dnf [options] autoremove [spec]...
{% endhighlight %} 

Ele remove os pacotes especificados do sistema, juntamente com todos os pacotes dependendo dos pacotes que estão sendo removidos. Cada [spec] pode ser um [package-spec] , que especifica um pacote diretamente, ou um @[group-spec] , que especifica um grupo (do meio) que o contém. Ele também remove quaisquer dependências que não são mais necessárias.<br><br>

Há também alguns comandos autoremove específicos: autoremove-n , autoremove-na e autoremove-nevra que permitem a especificação do formato NEVRA do argumento exato.<br><br> 

Este comando, por padrão, não força uma sincronização de metadados expirados. <br><br><br>

## Controle do comando:

{% highlight text %}
# dnf [options] check [--dependencies] [--duplicates] [--obsoleted] [--provides]
{% endhighlight %} 

Verifica o local packagedb e produz informações sobre os problemas que ele encontra. Você pode passar o comando de verificação as opções "-dependencies", "-duplicates", "-obsoleted" ou "-provides", para limitar a verificação que é executada (o padrão é "tudo" que faz tudo). <br><br><br>


## Verificar o comando de atualização:<br><br>

{% highlight text %}
# dnf [options] check-update [<package-specs>...]
{% endhighlight %}   <br><br>

Verifica não interativamente se as atualizações dos pacotes especificados estão disponíveis. Se não forem fornecidas <package-specs> , verifica se as atualizações estão disponíveis para o seu sistema. O código de saída DNF será 100 quando houver atualizações disponíveis e uma lista das atualizações será impressa, 0 se não e 1 se ocorrer um erro.<br><br>

Observe que ter uma versão mais recente específica disponível para um pacote instalado (e reportado por check-update ) não implica que a dnf upgrade subseqüente do dnf upgrade irá instalá-lo. A diferença é que a dnf upgrade também deve garantir a satisfação de todas as dependências e outras restrições.<br><br><br>

## O comando clean:<br><br>

Executa a limpeza de arquivos temporários mantidos para repositórios. Isso inclui quaisquer dados deixados atrás de repositórios desativados ou removidos, bem como para diferentes versões de lançamento de distribuição.<br><br>

{% highlight text %}
# dnf clean dbcache
Remove arquivos de cache gerados a partir dos metadados do repositório. Isso força o DNF a regenerar os arquivos de cache na próxima vez que ele for executado. 

# dnf clean expire-cache
Marca os metadados do repositório que expiraram. O DNF irá re-validar o cache para cada retomada na próxima vez que for usado. 

# dnf clean metadata
Remove metadados do repositório. Esses são os arquivos que o DNF usa para determinar a disponibilidade remota de pacotes. Usando esta opção, o DNF irá baixar todos os metadados da próxima vez que for executado. 

# dnf clean packages
Remove todos os pacotes em cache do sistema. 

# dnf clean all
Faz tudo daquilo acima. 
{% endhighlight %}   <br><br><br>

## Comando Distro-Sync:<br><br>

{% highlight text %}
# dnf distro-sync [<package-spec>...]
{% endhighlight %}<br><br>

Como atualizações necessárias, baixe ou mantenha os pacotes instalados selecionados para combinar a versão mais recente disponível de qualquer repositório habilitado. Se nenhum pacote for fornecido, todos os pacotes instalados são considerados. <br><br><br>
    
## Comando Downgrade:<br><br>

{% highlight text %}
# dnf [options] downgrade <package-installed-specs>...
{% endhighlight %} <br><br>

Baixe os pacotes especificados para o mais alto de todas as versões mais baixas conhecidas, se possível. Quando a versão é fornecida e é menor do que a versão do pacote instalado, ela baixa a versão de destino.<br><br><br> 

## Comandos de grupo:<br><br>

Os grupos são coleções virtuais de pacotes. O DNF controla os grupos que o usuário selecionou ("marcado") instalado e pode manipular os pacotes compostos com comandos simples.<br><br> 

{% highlight text %}
# dnf [options] group [summary] <group-spec>
Exibir a visão geral de quantos grupos estão instalados e disponíveis. Com uma especificação, limite a saída para os grupos correspondentes. <i>summary</i> é o subcomando de grupos padrão.

# dnf [options] group info <group-spec>
Exibir listas de pacotes de um grupo. Mostra quais pacotes estão instalados ou estão disponíveis a partir de um repo quando -v é usado.

# dnf [options] group install [--with-optional] <group-spec>...
Marque o grupo especificado instalado e instale os pacotes que ele contém. Também inclua pacotes opcionais do grupo se <i>--with-optional</i> for especificado. Todos os pacotes obrigatórios e padrão serão instalados sempre que possível. Pacotes condicionais são instalados se eles atendem seus requisitos. Se o grupo já estiver (parcialmente) instalado, o comando instala pacotes faltantes do grupo.

# dnf [options] group list <group-spec>...
Liste todos os grupos correspondentes, quer entre grupos instalados ou disponíveis. Se nada for especificado, liste todos os grupos conhecidos. As opções <i>- --available</i> e <i>- --available</i> reduzem a lista solicitada. Os registros são ordenados pela tag display_order definida no arquivo comps.xml. Fornece uma lista de todos os grupos ocultos usando a opção <i>--hidden</i>. Fornece informações mais detalhadas quando a opção <i>-v</i> é usada.

# dnf [options] group remove <group-spec>...
Marque o grupo removido e remova esses pacotes no grupo do sistema, que não compõem outro grupo instalado e não foram instalados explicitamente pelo usuário. 

# dnf [options] group upgrade <group-spec>...
Atualiza os pacotes do grupo e atualiza o próprio grupo. O último consiste em instalar pacotes que foram adicionados ao grupo pela distribuição e remoção de pacotes que foram removidos do grupo, na medida em que não foram instalados explicitamente pelo usuário. 
{% endhighlight %}   <br><br>

Os grupos também podem ser marcados como instalados ou removidos sem manipular fisicamente qualquer pacote:<br><br>

{% highlight text %}
# dnf [options] group mark install <group-spec>...
Marque o grupo especificado instalado. Nenhum pacote será instalado por este comando, mas o grupo será considerado instalado. 

# dnf [options] group mark remove <group-spec>...
Marque o grupo especificado removido. Nenhum pacote será removido por este comando. 
{% endhighlight %}   <br><br><br>

## Comando de Ajuda:<br><br>

{% highlight text %}
dnf help [<command>]
{% endhighlight %}   <br><br>

Exibe o texto de ajuda para todos os comandos. Se for dado um nome de comando, apenas exibe a ajuda para esse comando específico. <br><br><br>

## Comando History:<br><br>

O comando de histórico permite ao usuário visualizar o que aconteceu em transações passadas e atuar de acordo com essas informações (assumindo que a opção de configuração do history_record está definida).<br><br>

{% highlight text %}
# dnf history [list] [<spec>...]
{% endhighlight %}  <br><br> 

A ação padrão do histórico é listar informações sobre transações determinadas em uma tabela. Cada <spec> pode ser uma <transaction-spec>, que especifica uma transação diretamente ou uma <transaction-spec>..<transaction-spec>, que especifica um intervalo de transações ou uma <package-name-spec>, que especifica uma transação por um pacote que ele manipulou. Quando nenhuma transação é especificada, liste todas as transações conhecidas. <br><br>

{% highlight text %}
# dnf history info [<spec>...]
{% endhighlight %}  <br><br> 
    
Descreve as transações dadas. O significado de <spec> é o mesmo que no Comando da Lista de Histórico. Quando nenhuma transação for especificada, descreve o que aconteceu durante a última transação.<br><br> 

{% highlight text %}
# dnf history redo <transaction-spec>|<package-name-spec>
{% endhighlight %}  <br><br> 
    
Repete a transação especificada. Usa a última transação (com ID mais alta) se for encontrada mais de uma transação para determinado <nome do pacote-especificação>. Se não for possível refazer algumas operações devido ao estado atual do RPMDB, não irá refazer a transação. <br><br>

{% highlight text %}
# dnf history rollback <transaction-spec>|<package-name-spec>
{% endhighlight %}  <br><br> 
    
Desfazer todas as transações realizadas após a transação especificada. Usa a última transação (com ID mais alta) se for encontrada mais de uma transação para determinado <nome do pacote-especificação>. Se não for possível desfazer algumas transações devido ao estado atual do RPMDB, não irá desfazer qualquer transação. <br><br>

{% highlight text %}
# dnf history undo <transaction-spec>|<package-name-spec>
{% endhighlight %}  <br><br> 

Executa a operação oposta para todas as operações realizadas na transação especificada. Usa a última transação (com ID mais alta) se for encontrada mais de uma transação para determinado <nome do pacote-especificação>. Se não for possível desfazer algumas operações devido ao estado atual do RPMDB, não irá desfazer a transação. <br><br>

{% highlight text %}
# dnf history userinstalled
{% endhighlight %}  <br><br> 

Ele mostrará todos os pacotes <i>installonly</i>, pacotes instalados fora do DNF e pacotes não instalados como dependência. Ou seja, lista pacotes que permanecerão no sistema quando o comando Auto Remove Command ou Remove Command junto com clean_requirements_on_remove configuração definida como True for executado. Os mesmos resultados podem ser realizados com "dnf repoquery -userinstalled", mas o comando repoquery é muito mais poderoso na formatação de uma saída.<br><br> 

Este comando, por padrão, não força uma sincronização de metadados expirados. <br><br><br>

## Comando de Informação:<br><br>

{% highlight text %}
# dnf [options] info [<package-spec>...]
{% endhighlight %}  <br><br>

É usado para listar descrição e informações resumidas sobre pacotes instalados e disponíveis. <br><br><br>

## Instalar:<br><br>

{% highlight text %}
# dnf [options] install <spec>...
{% endhighlight %}  <br><br>

O DNF garante que os pacotes fornecidos e suas dependências estejam instalados no sistema. Cada [<spec>] pode ser um [<package-spec>] , ou um @[<group-spec>]. <br><br>

Quando [<package-spec>] que especifica a versão exata do pacote é fornecido, o DNF irá instalar a versão desejada, independentemente da versão do pacote já instalada. A versão anterior do pacote será removida no caso de um pacote não instalado. <br><br><br>

## Comando List: <br><br>

Baixa listas de pacotes dependendo da relação dos pacotes com o sistema. Um pacote é <i>installed</i> se estiver presente no RPMDB, e está <i>available</i> se ele não estiver instalado, mas está presente em um repositório que o DNF conhece. O comando de lista também pode limitar os pacotes exibidos de acordo com outros critérios, por exemplo, apenas para aqueles que atualizam um pacote instalado. A opção de exclusão no arquivo de configuração (.conf) pode influenciar o resultado, mas se a opção de linha de comando <i>- -disable</i> exclui é usada, ele garante que todos os pacotes instalados serão listados.<br><br>

Todos os formulários recebem um parâmetro [<package-specs>...] para limitar o resultado a apenas os pacotes correspondentes.<br><br>

{% highlight text %}
# dnf [options] list [--all] [<package-name-specs>...]
Lista todos os pacotes conhecidos por nós, presentes no RPMDB, em um repo ou em ambos. 

# dnf [options] list --installed [<package-name-specs>...]
Lista os pacotes instalados. 

# dnf [options] list --available [<package-name-specs>...]
Lista os pacotes disponíveis. 

# dnf [options] list --extras [<package-name-specs>...]
Lista os extras, que são pacotes instalados no sistema que não estão disponíveis em nenhum repositório conhecido. 

# dnf [options] list --obsoletes [<package-name-specs>...]
Liste os pacotes instalados no sistema que são obsoletos por pacotes em qualquer repositório conhecido. 

# dnf [options] list --recent [<package-name-specs>...]
Liste pacotes recentemente adicionados aos repositórios. 

# dnf [options] list --upgrades [<package-name-specs>...]
Atualizações de lista disponíveis para os pacotes instalados. 

# dnf [options] list --autoremove
Lista de pacotes que serão removidos pelo comando dnf autoremove. 
{% endhighlight %}  <br><br> 
