---
layout: page
title: DNF
excerpt: "Aprendendo o DNF."
---

![jekyll Image](http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/02/1424055625jekyll.png)
{: .image-pull-right}

<center><b>O Gerenciador de Pacotes DNF</b> aprenda aqui a usar.</center>

##Modo de usar:

{% highlight text %}
 dnf [options] <command> [<args>...] 
{% endhighlight %}   

##Descrição:

O DNF é a próxima versão principal do YUM, um gerenciador de pacotes para distribuições Linux baseadas em RPM. Ele mantém a compatibilidade CLI com YUM e define uma API rigorosa para extensões e plugins.

Os plugins podem modificar ou ampliar recursos do DNF ou fornecer comandos CLI adicionais em cima dos mencionados abaixo. Se você conhece o nome desse comando (incluindo os comandos mencionados abaixo), você pode encontrar/instalar o pacote que o fornece usando o fornecimento virtual apropriado sob a forma de dnf-command(<alias>) , onde <alias> é o nome do comando. Esta abordagem também se aplica à especificação de dependências de pacotes que requerem um comando DNF particular. 

Comandos disponíveis;

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

