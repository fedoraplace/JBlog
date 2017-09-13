---
layout: page
title: DNF
excerpt: "Aprendendo o DNF."
---

![jekyll Image](http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/02/1424055625jekyll.png)
{: .image-pull-right}

<center><b>O Gerenciador de Pacotes DNF</b><br> Aprenda a usar aqui.</center>



<br><br><br>
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
