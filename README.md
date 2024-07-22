# 6-exercicios-estagiarios-perl
>> Noções Básicas de Perl


### Definindo variáveis de ambiente

1- **HOME**

Usado por funções *chdir* por exemplo.

2- **LOGDIR**

Usado por funções *chdir* has no argument and HOME is not set.

3- **PATH**

Usado em *subprocessos* em execução, e localização de programas se -S é usado.

4- **PERL5LIB**

Uma lista de diretórios nos quais procurar arquivos de biblioteca Perl antes de procurar na biblioteca padrão e no diretório atual. Quaisquer diretórios específicos da arquitetura nos locais especificados são incluídos automaticamente, se existirem (essa pesquisa é feita no momento da inicialização do intérprete).

Se PERL5LIB não estiver definido, PERLLIB será usado. Os diretórios são separados (como em PATH ) por dois pontos em plataformas unixish e por um ponto e vírgula no Windows (o separador de caminho adequado é fornecido pelo comando "perl -V:path_sep").
Ao executar verificações de taint (seja porque o programa estava executando setuid ou setgid, ou porque a opção -T ou -t foi especificada), nenhuma variável é usada. Em vez disso, o programa deveria dizer:

```perl
use lib "/my/directory";
```

5- **PERL5OPT**

Opções de linha de comando (switches). As opções nesta variável são usadas como se estivessem em cada linha de comando Perl. Somente as opções -[CDIMUdmtw] são permitidas. Ao executar verificações de taint (porque o programa estava executando setuid ou setgid, ou a opção -T foi usada), esta variável é ignorada. Se PERL5OPT começar com -T, a contaminação será habilitada e quaisquer opções subsequentes serão ignoradas.

6- **PERLIO**

Uma lista separada por espaço (ou dois pontos) de camadas PerlIO. Se o perl for construído para usar o sistema PerlIO para IO (o padrão), essas camadas afetarão o IO do perl.

É convencional iniciar os nomes das camadas com dois pontos, por ex. ":perlio" para enfatizar sua semelhança com "atributos" variáveis. Mas o código que analisa strings de especificação de camada (que também é usado para decodificar a variável de ambiente PERLIO) trata os dois pontos como um separador.
Um PERLIO não definido ou vazio é equivalente ao conjunto padrão de camadas para sua plataforma, por exemplo ":unix:perlio" em sistemas do tipo UNIX e ":unix:crlf" no Windows e outros sistemas do tipo DOS.

A lista se torna o padrão para todos os IO do Perl. Conseqüentemente, apenas as camadas internas podem aparecer nesta lista, pois as camadas externas (como :encoding()) precisam de IO para carregá-las!. Consulte "pragma aberto" para saber como adicionar codificações externas como padrão.

```perl
#!/usr/bin/perl 
	
# Módulos usados/carregados
use strict; 
use warnings; 
	
# Escreva na tela
print("Teste de perl\n");
```
