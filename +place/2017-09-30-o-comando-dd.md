---
layout: +place
title:  "O Comando dd"
image: "http://ap.imagensbrasil.org/images/2017/09/28/Folder.png"
date:   2017-09-30
excerpt: "Conheça mais sobre o comando dd."
---

![Comandodd.png](http://ap.imagensbrasil.org/images/2017/09/28/Comandodd.png)
{: .image-pull-right}

<center><b>Aprenda melhor a usar o comando dd</b><br> abaixo maneiras e exemplos de como aplicar</center><br><br><br>

## O Comando dd:<br><br>

O comando dd se encontra disponível no Fedora como padrão, ou seja, logo após instalar, se for do seu desejo já poderá utilizá-lo sem nenhum problema. Por ser uma ferramenta nativa, logo o seu uso se torna mais importante e também corriqueiro de acordo com a nescessidade que possuir. Por exemplo, um usuário Linux normalmente gosta de testar outros sistemas operacionais semelhantes, Debian ou CentOS por exemplo. Para tal, o indivíduo evidentemente precisa de uma mídia, seja ela um CD/DVD/Pen Drive. Ela precisará gravar o arquivo .ISO baixado pelo site oficial do projeto para poder dar boot no computador e efetuar a instalação do sistema. Para tanto, o comando dd lhe vêm bem a calhar. 
Aqui lhe será mostrado várias maneiras diferentes de se usar esse comando e de que maneira ele pode ser aplicado. <br><br>

O comando dd significa <b>data duplicator</b> e a sua função nada mais é do que copiar algo, byte a byte, de maneira completa e confiável. Devido a isso é possível realizar simples cópias de arquivos até a cópias completas de um disco rígido (HDD). Para informações mais completas, acesse o manual do comando, abrindo o seu Terminal e digitando;

{% highlight text %}
$ man dd
{% endhighlight %}   <br><br><br>

## Como usar:<br><br>

Para usar o comando dd, deve-se seguir a seguinte estrutura em seu shell.<br><br>

{% highlight text %}
# dd if=<origem> of=<destino> [opções]
{% endhighlight %}   <br><br>

<b>Atenção:</b> Como pode notar acima, o modelo começa com um "jogo da velha". Sempre que começa dessa maneira, significa que o comando deve ser executado como root ou com o 'sudo' antes. Ok? E lembre-se: <b>Esse comando é muito poderoso e caso faça algo errado, pode ter resultados <u>irreversíveis</u></b>.<br><br>

<b>Explicação:</b> [if] é o caminho de origem, o local onde o arquivo ou dispositivo se encontra.  O [of] é o caminho de destino, que pode ser outro dispositivo por exemplo. A cópia se dá da origem para o destino. Um exemplo simples disso é o que você pode ver abaixo, onde o disco rígido é clonado para o pen drive do usuário.

{% highlight text %}
# dd if=/dev/sda of=/dev/sdb 
{% endhighlight %}   <br><br><hr size="5"><br><br><br>

## Backup do disco rígido para outra mídia:<br><br>

{% highlight text %}
# dd if=/dev/sda of=/dev/sdb bs=4096 conv=noerror,sync
{% endhighlight %}   <br><br>

Preste atenção. Levando em conta o modelo de estrutura explicado mais acima, abaixo será explicado o que cada elemento significa. Então vamos a eles.<br><br>

<b>dd</b> : É o nome do comando ao qual esse artigo se trata. Sempre o use em modo root.<br><br>

<b>if</b> : É o caminho de origem. Neste caso, o caminho de origem é o /dev/sda. Note que /dev/sda é como o disco rígido é conhecido na maioria dos casos. <br><br>

<b>of</b> : Esse é o caminho de destino. O HD antes mencionado é completamente copiado para o /dev/sdb. Provavelmente algum Pen Drive. Porém, pode ser alguma outra mídia.<br><br>

<b>bs</b> : Trata-se de quantos bytes serão copiados a cada momento.<br><br>

<b>conv=noerror,sync</b> : Representa o parâmetro de conversão. A opção ‘noerror’ permite que a ferramenta continue copiando os dados mesmo que encontre erros. E a opção ‘sync’ permite usar operações de Entrada/Saída sincronizadas.<br><br><br>

## Criando uma cópia do disco rígido em forma de imagem:<br><br>

{% highlight text %}
# dd if=/dev/sda of=/tmp/sda disk.img 
{% endhighlight %}   <br><br>

Seguindo o mesmo padrão e o mesmo modelo de sempre, pelo qual a operação se inicia com o comando dd e em seguida lhe é conferido os caminhos de origem e de destino, atente-se ao destino. Levando em conta que o disco é /dev/sda, dê um caminho e um nome com a terminação <b>".img"</b>. Há vários formatos, como.iso, .jpg e .tar. Neste caso, utilize .img para definir que a cópia a ser criada deve ser um arquivo do tipo imagem.<br><br><br>

## Fazer backup da MBR:<br><br>

Master Boot Record é o setor de inicialização do sistema. É a partir deste setor que o gerenciador de boot, que tem a função de permitir o acesso a um ou mais de um sistema operacional então se encontra. Dois exemplos destes são: GRUB e LiLO. Se não me engano esse último está descontinuado. Se não estiver, postem nos comentários a informação correta por favor.<br><br>

{% highlight text %}
# dd if=/dev/sda of=/tmp/backup-sda.mbr bs=512 count=1 
{% endhighlight %}   <br><br>

Lembra que dá última vez o formato foi alterado para ".img"? Desta vez, o caminho de destino aponta para um arquivo dentro da pasta /tmp chamado backup-sda.mbr. Sim, o final é ".mbr". Onde;<br><br>

<b><bs></b> : Representa o tamanho do disco de origem a ser copiado, que é de 512 bytes. Posteriormente, <b>count</b> significa a quantidade de blocos a ser copiado nesse processo.<br><br>

Salve-o onde quiser por motivos de segurança maior. Para restaurar, efetue o movimento inverso.<br><br>

{% highlight text %}
# dd if=/tmp/backup-sda.mbr of=/dev/sda  
{% endhighlight %}   <br><br><br>

## Criar um Pen Drive de boot:<br><br>

Você usuário Fedora, sabe que existem vários aplicativos para se gravar um arquivo ".ISO" em um dispositivo físico, neste caso, um Pen Drive. No Windows há várias opções, o RUFUS por exemplo é uma delas. No Fedora e em outros sistemas operacionais baseados em kernel Linux, também. No Fedora em especial posso citar o Fedora Media Writer, que é uma aplicação própria para gravar a imagem .ISO em um Pen Drive, ou até mesmo fazer o download direto do arquivo. Porém, o assunto desse artigo é o comando dd, e a partir dele será explicado abaixo o procedimento.<br><br>

{% highlight text %}
# dd if=/home/colorado/imagem_iso_ou_img of=/dev/sdb bs=4M;sync   
{% endhighlight %}   <br><br>

Preste atenção. No caminho de origem no exemplo em questão aponta para um arquivo no diretório pessoal do usuário "colorado". Se o seu usário é diferente, modifique o caminho acima de acordo. O mesmo vale para o nome de sua ISO. Se o arquivo se chama archlinux-2017-10.iso, troque-o pelo "imagem_iso_ou_img". Exemplos a parte, o processo é exatamente o mesmo, seguindo a mesma estrutura anteriormente explicada.<br><br><br>

## Gerando arquivos com tamanho pre-determinado:<br><br>

{% highlight text %}
# dd if=/dev/zero of=arquivo bs=10485760 count=1 
{% endhighlight %}   <br><br>
 
No caso de criar um arquivo vazio em diretório "x" e com um tamanho fixo, use o comando acima. Bastando alterar o valor contido em <b>bs</b>, onde se encontra o tamanho configurado. Coloque o valor de sua nescessidade. Sempre use valores em bytes, ou seja, do menor peso e nunca o maior.<br><br><br>

## Excluir dados de um disco rígido:<br><br>

Com o comando abaixo, é possível excluir tudo o que há no disco. Suas informações pessoais e seus sistemas operacionais instalados (se houver mais de um). Para tal, lembre-se que essa operação PODE ser irreversível. Ou seja, se você o executar, Provavelmente nunca mais poderá recuperar os arquivos caso assim o queira ou precise. Por isso, faça backup deles antes para assim evitar ficar tristinho.<br><br>

{% highlight text %}
# dd if=/dev/urandom of=/dev/sda bs=1M  
{% endhighlight %}   <br><br><br>

## Recuperar dados de um disco defeituoso para uma imagem:<br><br>

Se você tiver algum problema no seu HD, uma falha grave pela qual os seus arquivos estejam em risco o dd pode lhe salvar. Com ele você pode produzir uma cópia de seus arquivos íntegros e com ainda força vital para uma imagem, para ser gravada posteriormente em outra mídia como um ato heróico.  O seu HD deixará de funcionar, porém ainda assim você terá conseguido salvar os seus arquivos mais importantes.  Isso é possível com o dd. <br><br>

{% highlight text %}
# dd if=/dev/sda of=/tmp/sda disk.img bs=4k conv=noerror,sync 
{% endhighlight %}   <br><br>

Após a imagem de seu disco ser gerada, use o mesmo comando dd para gravar a imagem em uma mídia externa de sua preferência.<br><br><br>

## Converter as letras de um arquivo para minúsculas ou maiúsculas:<br><br>

Use o parâmetro <b>conv</b> para converter as letras. Indique do seguinte modo;<br>
- <u>ucase</u> : Minúsculas para maiúsculas.<br>
- <u>Icase</u> : Maiúsculas para minúsculas.<br><br>

{% highlight text %}
# dd if=arquivo1 of=arquivo2 conv=ucase 
# dd if=arquivo1 of=arquivo2 conv=Icase 
{% endhighlight %}   <br><br><br>

## Criar uma área de swap:<br><br>

Sim! Isso é possível com o dd. Não é preciso criar uma partição só para a swap, os Linux mais recentes possuem essa possibilidade e com isso é possível criar um arquivo para a "área de troca". Enfim, para tal, é preciso primeiramente usar o dd.<br><br>

{% highlight text %}
# dd if=/dev/zero of=/swap2 bs=1024 count=524288  
{% endhighlight %}   <br><br>

Com isso o seu arquivo swap será gerado.<br><br>

{% highlight text %}
# chown root:root /swap2
# chmod 0600 /swap2 
{% endhighlight %}   <br><br>

Os comandos acima devem ser executados uma linha de cada vez, para dar a permissão correta.<br><br>

{% highlight text %}
# mkswap /swap2 
{% endhighlight %}   <br><br>

Para tornar o arquivo de swap. E por fim;<br><br>

{% highlight text %}
# swapon /swap2 
{% endhighlight %}   <br><br>

Para ativar. Finalize adicionando o arquivo de swap em sua fstab, para que as suas configurações não sejam perdidas na próxima vez que você iniciar o sistema.<br><br>

{% highlight text %}
# nano /etc/fstab  
Adicione a seguinte linha abaixo no seu arquivo fstab:
/swap2 none swap defaults 0 0
Salve com CTRL+O e saia com CTRL+X.
{% endhighlight %}   <br><br><br>

## Copie uma partição para outra partição:<br><br>

{% highlight text %}
# dd if=/dev/sda9 of=/dev/sda11
{% endhighlight %}   <br><br>

No exemplo acima, o caminho de origem leva para a partição sda9, onde Provavelmente há variados arquivos. No procedimento, todos estes arquivos foram transferidos como uma cópia para a partição sda11 que fora recém criada. <br><br><br>

## Criar uma imagem ISO de um CD ou DVD:<br><br>

{% highlight text %}
# dd if=/dev/sr0 of=/sdb1/imagem.iso bs=2048 conv=noerror, sync
{% endhighlight %}   <br><br>

<b>Atenção:</b> Antes de utilizar o procedimento acima, note que o "/dev/sr0" é o caminho do seu disco no seu computador. Ele pode variar de computador para computador e de sistema para sistema. Portanto veja as suas partições e mídias montadas antes de continuar com qualquer coisa e coloque o caminho certo dentro do if. A mesma coisa vale para o of. Indique o caminho que desejar para a criação do seu arquivo .ISO.<br><br>

O comando acima por fim, irá copiar todo o disco definido em if para o destino configurado em of, que é, /sdb1. Use o nome que desejar no lugar de imagem.iso, por exemplo, a imagem pode ser "Nightwish.iso".<br><br>

Para verificar o seu disco rígido, suas partições e suas demais mídias montadas, visualize com estes dois comandos. O <b>df</b> e o <b>fdisk</b>.<br><br>

{% highlight text %}
# df -h
e 
# fdisk -l
{% endhighlight %}   <br><br>

Mais detalhes sobre eles, talvez em um próximo artigo.<br><br>

Esse artigo foi produzido para auxiliar as pessoas com o uso do dd. Cada comando aqui postado é fruto de uma pesquisa em 3 fontes:<br><br>

▶ <a href="https://www.youtube.com/watch?v=yYKE17YuO1Q">YouTube</a>
▶ <a href="https://www.linuxdescomplicado.com.br/2016/11/alguns-exemplos-de-que-o-comando-dd-pode-ser-considerado-umas-das-ferramentas-mais-versateis-do-linux.html">Linux Descomplicado</a>
▶ <a href="http://www.dicas-l.com.br/arquivo/usando_o_comando_dd.php">Dicas-L</a><br><br>

Os comandos do dd não foram testados por mim, por não possuir um computador para testes no momento, porém asseguro que o comando dd para gravar uma ISO em um Pen Drive funciona perfeitamente.<br><br>

Até mais ver! =D<br><br>
 
