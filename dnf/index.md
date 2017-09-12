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

O DNF é a próxima versão principal do YUM, um gerenciador de pacotes para distribuições Linux baseadas em RPM. Ele mantém a compatibilidade CLI com YUM e define uma API rigorosa para extensões e plugins.<br><br>

Os plugins podem modificar ou ampliar recursos do DNF ou fornecer comandos CLI adicionais em cima dos mencionados abaixo. Se você conhece o nome desse comando (incluindo os comandos mencionados abaixo), você pode encontrar/instalar o pacote que o fornece usando o fornecimento virtual apropriado sob a forma de dnf-command(<alias>) , onde <alias> é o nome do comando. Esta abordagem também se aplica à especificação de dependências de pacotes que requerem um comando DNF particular. 
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
## Opções:

-4
Resolva somente para endereços IPv4. 
<br><br>
-6
Resolva apenas para endereços IPv6. 
<br><br>
--advisory=<advisory>, --advisories=<advisory>
Inclui pacotes correspondentes ao ID de aviso, por exemplo. FEDORA-2201-123. Aplicável para instalação, repoquery, updateinfo e comando de atualização. 
<br><br>
--allowerasing
Permitir o apagamento de pacotes instalados para resolver dependências. Esta opção pode ser usada como uma alternativa para o comando yum swap onde os pacotes a serem removidos não são explicitamente definidos. 
<br><br>
--assumeno
Responda automaticamente para todas as perguntas 
<br><br>
-b, --best
Experimente as melhores versões de pacotes disponíveis nas transações. Especificamente durante a atualização do DNF, que por padrão, ignora as atualizações que não podem ser instaladas por motivos de dependência, a chave força o DNF a considerar apenas os pacotes mais recentes. Ao executar pacotes com dependências quebradas, o DNF falhará, dando uma razão pela qual a versão mais recente não pode ser instalada. 
<br><br>
--bugfix
Inclui pacotes que corrigem um problema de bugfix. Aplicável para instalação, repoquery, updateinfo e comando de atualização. 
<br><br>
--bz=<bugzilla>
Inclui pacotes que consertam um ID do Bugzilla, por exemplo. 123123. Aplicável para instalação, repoquery, updateinfo e comando de atualização. 
<br><br>
-C, --cacheonly
Execute inteiramente a partir do cache do sistema, não atualize o cache e use-o mesmo no caso de expirar.
<br><br>
O DNF usa um cache separado para cada usuário sob o qual ele é executado. O cache para o usuário raiz é chamado de cache do sistema. Esta opção permite um acesso regular de somente leitura do usuário ao cache do sistema, que geralmente é mais recente que o do usuário e, portanto, ele não precisa esperar a sincronização de metadados. 
<br><br>
--comment=<comment>
Adicione um comentário ao histórico de transações.
<br><br>
-c <config file>, --config=<config file>
Localização do arquivo de configuração. 
<br><br>
--cve=<cves>
Inclui pacotes que consertam uma ID CVE (Vulnerabilidades e exposições comuns) ( http://cve.mitre.org/about/ ), por exemplo. CVE-2201-0123. Aplicável para instalação, repoquery, updateinfo e comando de atualização. 
<br><br>
-d <debug level>, --debuglevel=<debug level>
Depuração do nível de saída. Este é um valor inteiro entre 0 (sem cadeias de informações adicionais) e 10 (mostra todas as informações de depuração, mesmo que não são compreensíveis para o usuário), o padrão é 2. Deprecated, use -v vez disso. 
<br><br>
--debugsolver
Descarregue dados ajudando na depuração de dependentes em depuração em ./debugdata. 
