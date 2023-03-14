# Comunicação entre MVNs

## Introdução

Este projeto é uma introdução a Redes, disciplina muito relevante no
contexto de Sistemas de Programação. Para entender corretamente o que
deve ser feito deve-se entender quais os princípios e processos
utilizados para realizar troca de informações entre duas máquinas, tudo
isso será aprofundado na disciplina "Redes de Computadores" em algum
momento no futuro.

## Base de Segurança

Com o surgimento da possibilidade de interligar computadores de forma
que eles pudessem trocar informações, apareceu a necessidade de fazer
com que as mensagens enviadas chegassem completas aos destinos corretos.
Originalmente as redes eram pequenas e restritas a pequenos grupos de
computadores, de forma que cada rede implementava sua forma própria de
realizar essa verificação, mas, com o crescimento das redes, houve a
necessidade de definição de protocolos universais para que todos
conseguissem se comunicar.

Atualmente existem diversos protocolos que realizam a comunicação
divididos entre várias camadas de abstração, desde os modelos físicos
que definem os cabos a serem utilizados até modelos de aplicação, que
definem como utilizar os serviços nos softwares. Cada tipo de protocolo
em cada uma das camadas tem uma finalidade específica e propriedades das
mais variadas, que devem ser analisadas com cautela (existe até um
protocolo para comunicação de internet por pombos-correio, chamado
[IPoAC](https://en.wikipedia.org/wiki/IP_over_Avian_Carriers)).

Os protocolos de Internet são muito complexos pois definem uma
quantidade grande de parâmetros importantes para que seja possibilitada
uma boa transmissão das informações. Porém, para um caso simples, em que
poucas máquinas estão se comunicando, apenas remetente, destinatário e
mensagem são informações necessárias.

## O que será fornecido

Para a execução do trabalho, é necessário que hajam funções de operações
adicionais que possam ser executadas. Por isso é fornecido na própria
implementação da MVN alguns métodos de realizar mais operações sobre
dispositivos e timers. Para atualizar os valores lidos em um dispositivo
(caso tenham aparecido novas informações em um arquivo, por exemplo)
deve-se utilizar a função `OS` com operação `0x0D`, o identificador do
dispositivo como argumento e o valor 1 no acumulador. Para interromper a
execução por um período de tempo, deve-se utilizar a função `OS` com
operação `0x71`, nenhum argumento e o número de milissegundos para esperar no
acumulador. Para definir um _timeout_ para entradas do teclado, deve-se
invocar a MVN com a flag `-t` seguida do tempo em milissegundos para
esperar o usuário entrar com um valor no teclado antes de retornar 0 no
acumulador.

## O trabalho

O trabalho consiste na implementação de um mecanismo simples para que
seja possibilitada a comunicação entre duas MVNs.

O meio de comunicação entre as duas máquinas deve ser um arquivo, de
onde as duas escrevem e leem, ou dois arquivos, de uma uma lê e outra
escreve. Você deve implementar, utilizando esse(s) arquivo(s), um código
que realize um tipo de chat entre as MVNs, ou qualquer outra
funcionalidade análoga, não necessariamente fazendo leitura do teclado,
mas isso seria legal. Pode ser interessante iniciar fazendo uma máquina
que apenas escreve e outra que apenas lê e depois unificar os códigos.

### Desafio
Uma característica comum em alguns protocolos de comunicação é
a identificação das partes quando se inicia a troca de informações.
Nestes casos, uma das máquinas manda uma mensagem de início de conversa
se identificando e a outra responde aceitando a comunicação e se
identificando também (chamado protocolo de _handshake_). Você deve
implementar como desafio um sistema desse tipo para iniciar a
comunicação das duas MVN's.

O trabalho pode ser feito em duplas ou individualmente. Definir escopo
de uso do comunicador, mensagens de erro coerentes, eventuais limitações
e funcionalidades não comentadas acima FAZEM parte do trabalho.

## Perguntas

Seguem algumas perguntas a serem respondidas depois da codificação:

1.  Os algoritmos propostos podem ser mais eficientes? Como? Se sim, por
    que a forma menos eficiente foi escolhida?

2.  Os códigos escritos podem ser mais eficientes? Como? Se sim, por que
    a forma menos eficiente foi escolhida?

3.  Qual foi a maior dificuldade em implementar as rotinas?

4.  O que teria que ser mudado no seu código para que fossem permitidas
    mais de duas máquinas conversando ao mesmo tempo?

5.  O que aconteceria com a execução do seu código se o(s) arquivo(s)
    das máquinas fosse alterado manualmente por algum usuário?

## Entrega

Dois ou mais arquivos devem ser entregues:

1.  **Comunicador:** um arquivo em ASM chamado `chat.asm` contendo a rotina
    que faz a comunicação entre as MVNs.

2.  **Relatório:** um arquivo chamado `relatorio_<NUSP1>_<NUSP2>.pdf` para
    trabalhos realizados em dupla, ou `relatorio_<NUSP>.pdf` para individuais
    contendo uma descrição resumida do problema e dos conceitos e uma descrição
    detalhada das etapas de resolução, da estratégia utilizada em cada módulo
    e outras informações que julgarem úteis. O relatório pode conter imagens
    das execuções de teste;

3.  Outros arquivos que julgar necessário.
