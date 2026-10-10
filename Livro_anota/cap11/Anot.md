# Segurança de Software
> **RESUMO**,

## Questões de Segurança de Software
> A segurança de software está intimidadmente relacionada à
**qualidade e confiabilidade de software**, com leves diferenças.
Qualidade e confiabilidade de software preocupam-se com a falha 
acidental de um programa como resultado de alguma interação 
teoricametne alatória, não antecipada, com o sistema ou utilização 
incorreta de código. Segurança de software é diferente, uma vez que 
dado atacante tenta explorar uma vulnerabildiade de forma 
probabilistica aleatória, o sistema tem que ser capaz de cobrir todos 
essas possibilidades, através de  uma escrita de código cuidadoso e 
segura e que para uma boa resposta no projeto, deve ser aplicada 
desde o seu início de implementação.

> **Programação Defensiva**, é uma forma de projeto defensitvo que 
tem como objetivo assegurar o funcionamento continuado de um artefato
de software, a despeito da utilização não previsível do dito 
software. A ideia pode ser vista como a redução ou eliminação de 
possiveis efeitos da Lei de Murphy.

## Tratamento de Entradas do Programa

> O tratamento incorreto de entradas em programas é uma das falhas de 
segurança de software mais comuns. Sendo, uma entrada de programa 
qualquer fonte de dados originada fora do programa e cujo o valor não 
era explicitametne conhecido pelo programador quando o código foi 
escrito. As duas áreas fundamentais de preocupação para qualquer 
entrada são o tamanho da entrada e o significado e a interpretação da 
entrada.

### Tamanho da Entrada e Estouro de Capacidade de Buffer
> Normalmente em entradas de dados, há alocação de um buffer no qual 
o tamanho é estimado um valor onde não haverá uso completo do espaço. 
O problema é que muitas vezes não se é verificado o uso desses 
espaço, pode haver o excedimento do tamanho e acarretando em um 
buffer overflow, causando posterioremente inumeros problema na 
execução do programa. Uma forma de combater é através da verificação 
para confirmar a veracidade dos dados da forma disponível para o 
programador, normalmente, atráves do tamanho do dado recebido de 
input.


### Interpretação da entrada do programa
> Outra preocupação fundamental com entradas de programas é seu 
siginificado e interpretação. Dados de entradadde programa podem ser 
classifcados, em geral, como textuais e binários.

### Ataques de injeção
> Podem ocorrer sempre que um programa invoca serviços de outro 
programa, serviço ou função, e passa para ele informações advindas de 
fontes externas, potencialmente não confiaveis, sem inspeção e 
validação suficientes. Isso apenas reforça a necessidade de 
identificar todas as fontes de entradas, para validar quaisquer 
suposições sobre tais entradas antes de usá-las e para entender o 
significado e a interpretação dos valores fornecidos a qualquer 
programa, serviço ou função invocados.

### Validação da Sintaxe de Entrada
> É a forma de tratar possibilidade de input, através de comprovação 
dos dados a serem inseridos no sistema. Normalmente, utiliza-se de 
**expressões regulares** para um melhor filtro do tipo de sintaxe 
aceita para uma determinada entrada. Além disso, há também o cuidado 
com as multíplas representações de um único caracter e para isso é 
necessário aplicar a canonicalização da entrada, antes de efetuar o 
filtro de expeção.

### Fuzzing de Entrada
> É uma técnica de teste de software que usa dados gerados 
aleatoriamente como entradas para um programa. A intenção é 
determinar se o programa ou função trata corretamente todas essas 
entradas anormais ou se trata ou, de qualquer outro modo, não 
conseguindo responder adequadamente, accarretando em bugs visivéis 
para correção. Nota-se que os bugs encontrados, geralmente, são 
ligados a entradas longas e, problemas com entradas menores passaram 
despercebidos. Entretanto, os bugs mais perigosos estão ligados a 
entradas de maior tamanho. Portanto. o fuzzing deve ser 
disponibilizado como um componente de qualquer estratégia de testes 
razoavelmente abragentes.

## Escrever Código de Programa Seguro
> De uma perpectiva de segurança de software, as questões 
fundamentais são se o algoritmo implementado resolve corretamente o 
problema especificado, se as instruções de máquina executadas 
corretamente representam a especificação do algoritmo de alto nível 
e se a manipulação de valores de dados em variáveis, como os 
armazenados em registradoes de máquina ou na memória, é válida e 
significativa.

### Implementação do Algoritmo Correto
> O algorito pode não implementar corretamente todos os casos ou 
variantes do problema, o que poderia permitir alguma entrada de 
programa aparentemente légitima acionasse um comportamente não 
pretendido do programa, dando a um atacante capacidades adicionais. 
A consequência geral de tal deficiência no projeto e implementação 
do algoritmo é um bug no programa resultante, o qual poderia ser 
explorado maliciosamente.

### Garantir que a Ling. de Máq. Corresponde ao Algoritmo
>

### Interpretação Correta de Valores de Dados
> Todos os dados em um computador são armazenados como grupos de 
bits binários e armazenados em sequências de bytes na memória. O 
perigo nesse caso é para linguagens de fracamente tipadas, elas 
possibilitam a interpretação de um dado em uma forma antes não 
especificada, ou seja, exemplo em c, uma variavel long int (8bytes), 
pode ser interpretada como um ponteiro (endereço de memória), assim 
possibilitando uma variedade de manipulação do mesmo dado. Uma 
solução é utilizar de linguagens de programação fortemente tipadas, 
que impossibilitam essa interpretação dado de maneira extremamente 
liberal.

### Uso Correto de Memória
> Relacionado à questão da interpretação dos valores de dados, tem-
se a alocação e o gerenciamento do armazenamento dinâmico de 
memória, geralmente usando região de heap do processo. O uso 
incorreto desse espaço de memória pode acarretar em um vazamento de 
memória (memory leak) e uma finalização precosse do programa, ou 
seja, há uma possibilidade de ataque de DoS para esse casos.

### Impedir Condições de Corrida com Memória Compartilhada
> Em programas maiores, há uma execução de inúmeros processos de 
maneira simultânea e, isto pode acarretar em uma race condicion. De 
forma geral, há a possibilidade que thereads fiquem refém de um 
determinado dado ou acessem um determinado dado simultaneamente, 
isso pode acarretar em um momento que ocorra um impasse, quando 
todas a thereads fiquem esperando ociosamente. Esse problema é uma 
possibilidade de ataque de DoS há um sistema. 

## Interação com o SO e Outro Programas
> Programas são executadas sob o gerenciamento do Sistema 
Operacionaç (SO) que fa a mediação do acesso aos recursos desse 
sistema e compartilha o uso desses recusos entre todos os programas 
em execução no momento em questão.

### Variáveis de Ambiente
> São uma coleções de valores, representados por cadeias de 
caracteres herdados do por cada processo de seu pai e que podem 
afetar o comportamento de um processo em execução. 
...

### Utilização de Privelégios Mínimos Adequados
> Privilégio mínimo é uma forma de defesa de sistema, onde programas 
devem sempre executar com a quantidade mínima necessária de 
privilégio, dificultando, em caso de ataque ao mesmo, uma elevação 
de privilégio ao atacante. 

### Chamadas do Sistema e Funções de Biblio.Padrão
> 

### Impedir Condições de Corrida com Memória Compartilhada
> Há diversas arquivos dentro de um sistema que servem de base de 
dados ou são acessados inúmeras vezes e é necessário tratar essa 
gerencia de aceeso, o resposável é o SO. Um exemplo é o arquivo de 
caixa postal, compartilhados por programas de envio de e-mail. Uma 
forma de resolução e a utilização de **lockfile**, 

### Interação com Outros Programas
> 



## Tratamento de Saída de Programas
> 





