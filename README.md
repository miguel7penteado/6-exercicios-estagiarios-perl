# 6-exercicios-estagiarios-perl
>> Noções Básicas de Perl

## 1- Instalação

### Definindo variáveis de ambiente

#### Linux
As variáveis de ambiente já vem configuradas após a instalação dos pacotes em praticamente todas as distribuições Linux.

#### windows

No windows, indico você utilizar o arquivo zipado ("instalador zip") e configurar as variáveis de ambiente no braço:
Crie uma pasta chamada **Perl** e uma subpasta chamada **5.32** dentro do diretório **C:\Program Files**.
Descompacte o conteúdo do pacote zip dentro de **C:\Program Files\Perl\5.32**
Supondo que você tenha desempacotado o conteúdo do seu "instalador perl" no diretório **C:\Program Files\Perl\5.32**, comece a definir as variáveis de ambiente:

```cmd
SET HOME=%USERPROFILE%
SET PATH=C:\Progra~1\Perl\5.32\perl\bin;C:\Progra~1\Perl\5.32\c\bin;C:\Progra~1\Perl\5.32\c\x86_64-w64-mingw32\bin;C:\Progra~1\Perl\5.32\c\libexec\gcc\x86_64-w64-mingw32\8.3.0;C:\Progra~1\Perl\5.32\c\libexec\gcc\x86_64-w64-mingw32\8.3.0\install-tools;%PATH%

SET PERLLIB=C:\Progra~1\Perl\5.32\perl\lib
SET PERL5LIB=%PERLLIB%
SET LOGDIR=%TMP%
```
#### Qual a funcionalidade de cada uma dessas variáveis no windows
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

## 2- Exemplos

### 2.1- operadores aritiméticos e lógicos

```perl

# Variáveis
$variavel1 = 10;
$variavel2 = 4; 
$variavel3 = true;
$variavel4 = false;
    
# Operações aritiméticas simples:
print "O resultado da soma é:",      $variavel1 + $variavel2, "\n";
print "O resultado da subtração é:", $variavel1 - $variavel2, "\n";
  
# Operações relacionais e seus operadores:
if ($variavel1 == $variavel2)
{
   print "Operador de igualdade retornando Verdadeiro\n";
}
else
{
   print "Operador de igualdade retornando Falso\n";
}
 
# Operações de lógica booleana:
$resultado = $variavel1 && $variavel2;
print "Operador AND: ", $resultado, "\n";

# Usando o operador unário AND:
$resultado = $variavel1 & $variavel2;
print "Operador unário AND: ", $resulto, "\n";

# Usando operadores de atribuição:
print "Usando o operador de atribuição de soma: ", $variavel1 += $variavel2, "\n";

```
### 2.2- representações de números
```perl
#!/usr/bin/perl

# Programa Perl para ilustrar o uso de números

# Número Inteiro
$NumeroInteiro = 20;

# Número Real
$NumeroReal = 20.5647;

# Notação Científica
$NumeroCientifico = 123.5e-10;

# Notação Hexadecimal 
$NumeroHexadecimal = 0xc;

# Notação Octal
$NumeroOcatl = 074; 

# Notação Binária 
$NumeroBinario = 0b1010; 

# IMprimindo os Valores
print("Este é um número inteiro: ",    $NumeroInteiro,     "\n");
print("Este é um número real: ",       $NumeroReal,        "\n");
print("Este é um número científico: ", $NumeroCientifico,  "\n");
print("Este é um número Hexadecimal:", $NumeroHexadecimal, "\n");
print("Este é um número Octal:",       $NumeroOcatl,       "\n");
print("Este é um número Binário: ",    $NumeroBinario,     "\n");
```

Escrevendo caracteres unicode no console do windows:
```perl
use utf8; 

my $codificacao = $^O eq 'MSWin32' ? 'cp850' : 'utf8';
binmode(STDOUT, ":encoding($codificacao)" );

print "$_ " for qw/á Á à À ã Ã â Â é É ê Ê í Í ó Ó õ Õ ô Ô ú Ú ç Ç/;

```



Fonte: [https://www.geeksforgeeks.org/perl-tutorial-learn-perl-with-examples/](https://www.geeksforgeeks.org/perl-tutorial-learn-perl-with-examples/)
