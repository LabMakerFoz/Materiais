# Arduino

Índice
------

* [1 Arduíno](#Arduíno)
  + [1.1 Algumas placas Arduino](#Algumas_placas_Arduino)
  + [1.2 Hardware do Arduíno UNO [1]](#Hardware_do_Arduíno_UNO_[1])
    - [1.2.1 Voltagens de alimentação](#Voltagens_de_alimentação)
    - [1.2.2 Entradas e Saídas](#Entradas_e_Saídas)
  + [1.3 Ambiente de desenvolvimento do Arduíno](#Ambiente_de_desenvolvimento_do_Arduíno)
  + [1.4 SimulIDE: Ambiente de simulação para Arduíno](#SimulIDE:_Ambiente_de_simulação_para_Arduíno)
    - [1.4.1 Programação do Arduíno no SimulIDE](#Programação_do_Arduíno_no_SimulIDE)
      * [1.4.1.1 Uso do compilador no próprio SimulIDE](#Uso_do_compilador_no_próprio_SimulIDE)
    - [1.4.2 Binários compilados](#Binários_compilados)
  + [1.5 Referências](#Referências)

Arduíno
=======

Descrição
:   O Arduino é um microcontrolador montado em uma plataforma de prototipagem eletrônica de hardware livre que pode ser utilizado em múltiplas aplicações. O **Arduino** é facilmente programável através de uma **interface de programação** (**IDE**) e pode ser utilizado para automação de dispositivos eletrônicos, acionamento de motores e leds, monitoramento de sensores, construção de protótipos de soluções tecnológicas e um mundo de possibilidades.

Links e referências

* [Site oficial do Arduíno](http://www.arduino.cc/)
  + [Referência da Linguagem](https://www.arduino.cc/reference/pt/)
  + [Exemplos prontos](https://www.arduino.cc/en/Tutorial/BuiltInExamples)
  + [Exemplos usando Bibliotecas](https://www.arduino.cc/en/Tutorial/LibraryExamples)

Algumas placas Arduino
----------------------

Arduino UNO

[![](./img/300px-PinosArduinoUno.png)](/wiki/index.php/Arquivo:PinosArduinoUno.png)

Arduino Micro

[![](./img/375px-PinosArduinoMicro.png)](/wiki/index.php/Arquivo:PinosArduinoMicro.png)

Arduino Mega

[![](./img/500px-PinosArduinoMega.png)](/wiki/index.php/Arquivo:PinosArduinoMega.png)

Hardware do Arduíno UNO [[1]](#cite_note-1)
-------------------------------------------

* Microcontrolador ATmega328P
* Voltagem de operação 5V
* Alimentação recomendada 7-12V
* Entradas/saídas digitais 14 (6 podem ser saídas PWM)
* Saídas PWM "analógicas" 6
* Entradas analógicas 6
* Corrente DC por pino 20 mA
* Corrente DC pino 3.3V 50 mA
* Memória Flash 32 KB
* Memória SRAM 2 KB
* Memória EEPROM 1 KB
* Velocidade do Clock 16 MHz

### Voltagens de alimentação

O Arduíno pode ser alimentado pelo **cabo USB** ou por **fonte externa**.

A alimentação com **fonte externa** recomendada é 7-12V.

Pinos de voltagem

* **5V** Tensão regulada de **5V** (independente de alimentado pelo cabo UBS ou fonte externa).
* **3,3V** Tensão regulada de **3,3V**.
* **GND** Pinos de **terra**.
* **Vin** Quando utilizado **fonte externa** a tensão da mesma pode ser obtida aqui.
* **IOref** Fornece a tensão de referência que o microcontrolador opera, por exemplo, o UNO opera com 5V, mas o DUE opera em 3,3V.

### Entradas e Saídas

14 Entradas/Saídas Digitais
:   Operam com valores digitais **LOW** (**0V**) e **HIGH** (**5V**). Fornecem corrente de até **20 mA**. Qualquer corrente solicitada acima de **40 mA** pode danificar o Arduíno.

6 Entradas Analógicas
:   Nomeadas de **A0** até **A5**. Por default recebem **valores analógicos entre 0V e 5V** e convertem para digital com **10 bits de resolução** (valores de **0** a **1023**).
:   **Aref** Usada para mudar a referência para a **conversão analógico-digital**, deve ser usada em conjunto com a função **analogReference**(). Por exemplo, se quisermos converter sinal analógico entre 0 e 1,5V, colocamos esta tensão em Aref.

6 Saídas PWM
:   Identificadas pelo sinal **~**. Fornecem **saídas analógicas** através de **pulsos PWM** (*Pulse Width Modulation*) de **8 bits** (valores de **0** a **255**).
:   O sinal PWM é uma onda quadrada, com frequência constante, mas a fração de tempo em que o sinal é HIGH (5V) (*duty cycle*) pode variar entre 0 e 100%, fornecedo uma média de tensão variável na saída [[2]](#cite_note-2).

[![](./img/PWM.gif)](/wiki/index.php/Arquivo:PWM.gif)

Led pino 13
:   O pino 13 tem um **led montado na placa**. Quando o pino for HIGH o led acende, quando for LOW o led apaga.

Serial 0 (RX) e 1 (TX)
:   Os pinos 0 e 1 podem ser usados para **transmitir (TX) e receber (RX) serialmente** dados TTL.
:   Dados digitais **TTL** operam valores LOW (0V) e HIGH (5V).

Interrupções externas
:   Os pinos 2 e 3 podem ser utilizados para dispararem **interrupções externas** com a função **attachInterrupt()**.

Ambiente de desenvolvimento do Arduíno
--------------------------------------

O ambiente de desenvolvimento de software do Arduíno usa uma linguagem de programação própria, baseada na **linguagem C**.

Instalação
:   Para instalação no Ubuntu 20.04:

```
sudo apt update
sudo apt install arduino
```

Os programas fonte são identificados pela extensão **.ino**.

A própria IDE do Arduíno apresenta vários exemplos de aplicações e programas que ajudam quem está iniciando a programá-lo.

[![](./img/400px-ArduinoIDE.png)](/wiki/index.php/Arquivo:ArduinoIDE.png)

SimulIDE: Ambiente de simulação para Arduíno
--------------------------------------------

Existem diversos **ambientes de simulação** para o Arduíno, como o **[SimulIDE](https://www.simulide.com)** e o **[TinkerCAD](https://www.tinkercad.com)**.

O **SimulIDE** é um simulador para **Arduíno** e **circuitos eletrônicos** que pode ser instalado em diferentes sistemas operacionais, sendo um sistema leve e fácil de utilizar.

Instalação do SimulIDE no Ubuntu 20.04
:   Baixar a versão compatível com o sistema operacional de extrair o conteúdo do arquivo .tar.gz.
:   Instalar dependências que precisam para o programa e estão descritas no arquivo README.md.
:   Podem ser instaladas com o comando:

```
sudo apt-get install libqt5core5a libqt5gui5 libqt5xml5 libqt5svg5 libqt5widgets5 libqt5concurrent5 libqt5multimedia5 libqt5multimedia5-plugins libqt5serialport5 libqt5script5 libelf1
```

:   O diretório "SimulIDE\_x.x.x" tem tudo o que precisa para rodar o programa, ir até ele e executar:

```
./simulide
```

### Programação do Arduíno no SimulIDE

A programação do Arduíno no **SimulIDE** pode ser realizada utilizando a própria **IDE do Arduíno**, o que é interessante pelo fato de dispor de todos os exemplos prontos de programas.

IDE Arduíno
:   Procedimentos:

* **Compilar** o programa;
* **Exportar binário compilado** (.hex)

```
/sketch/Exportar Binário compilado
```

SimulIDE
:   Procedimentos:

* Clicar com o botão direito do mouse sobre o Arduíno e selecionar **Load firmware**;
* Selecionar arquivo **binário compilado** (.hex).

#### Uso do compilador no próprio SimulIDE

O **SimulIDE** também apresenta uma área para **edição de programa**, a qual pode ser utilizada para **edição**, **compilação** e **carga do programa** no módulo de simulação.

Para utilizar esta facilidade do SimulIDE deve-se clicar com o botão direito do mouse na área de **edição de programas** e configurar o parâmetro **Compiler path**. O compilador o simulador utiliza o próprio compilador da IDE do Arduíno, portanto, deve-se configurar o caminho onde o programa está localizado.

Para descobrir o caminho onde está rodando a **IDE do Arduíno**, pode habilitar as mensagens do compilador na IDE em

```
Arquivo/Preferências/Mostrar mensagens de saída durante compilação
```

Depois compilar um arquivo e verificar caminho onde o programa está instalado.

### Binários compilados

Quando exportamos o **binário compilado** são gerados dois arquivos **.hex**:

```
ino.standard.hex

ino.with_bootloader.standard.hex
```

Como o nome indica, o primeiro não inclui o ***bootloader***. Quando fazemos um **carga normal** de programa no Arduíno via **USB**, o ***bootloader*** instalado no módulo recebe os dados pela **comunicação serial** e escreve o programa na **memória *flash***.

O binário `ino.with_bootloader.standard.hex` é utilizado quando se usa um **programador externo**, conectado aos pinos ICSP da placa, para gravar o programa na **memória *flash*** do **microcontrolador**. Neste caso, o programador externo sobre-escreve o *bootloader* instalado no módulo, portanto, é necessário incluir a parte do *bootloader* para o módulo funcionar.

Referências
-----------

1. [↑](#cite_ref-1) <https://www.arduino.cc/en/Main/ArduinoBoardUno>
2. [↑](#cite_ref-2) <https://www.arduino.cc/en/Tutorial/SecretsOfArduinoPWM>

---

Disponível em “<http://wiki.foz.ifpr.edu.br/wiki/index.php?title=Arduino&oldid=30291>”
