# Sistemas de Controle

Referência principal
:   OGATA, Katsuhiko. Engenharia de Controle Moderno, 5a Ed, Pearson, 2011.

Um **sistema de controle em malha fechada** procura manter a saída do sistema alinhada com uma **referência**. Para tal, monitora uma variável do sistema com um **sensor** e compara com a referência. O **erro** resultante é utilizado para ajustar a **ação de controle**

![](./img/SistemasControle.png)

Controle On / Off
-----------------

O **controle on/off** procura ajustar a saída do sistema com a referência ligando e desligando a ação de controle. Por exemplo, para manter uma dada temperatura em um forno, liga ou desliga a resistência de aquecimento, caso a temperatura fique abaixo ou acima do ponto de referência, respectivamente.

![](./img/ControleOnOff.png)

É interessante a ação de **controle on/off** ter um **intervalo diferencial** na referência para evitar comutações excessivas.

Gráfico da saída com controle On/Off
:   A saída de um sistema com controle On/Off oscila entre dois pontos, ligeiramente acima e abaixo da referência.

![](./img/GradicoOnOff.png)

Controle Proporcional
---------------------

O **controle proporcional** ajusta a ação de controle de forma **proporcional ao erro** gerado

![](./img/ControleProporcional.png)

```
        u(t) = Kp  e(t)
```

**Função de Transferência** (Transformada de Laplace):

```
              Us Es = Kp
```

A ação de **controle proporcional** funciona como um **amplificador com ganho variável**, proporcional ao erro.

Controle Integral
-----------------

O **controle integral** ajusta a ação de controle em função ao **somatório do erro** em um dado intervalo de tempo.

![](./img/ControleIntegral.png)

```
        u(t) = Ki ∫ 0t e(t)dt
```

**Função de Transferência** (Transformada de Laplace):

```
              Us Es = Kis
```

### Ação de controle integral

Na ação de **controle integral** a saída do controlador é igual a **área sobre a curva do erro** (**integral do erro**) atuante até aquele instante de tempo.

Quando o erro fica nulo a ação de controle permanece num estado estacionário, função do somatório dos erros anteriores.

**Gráfico do Controle Integral**:

![](./img/GraficoControleIntegral.png)

Controle Proporcional Integral
------------------------------

O controle proporcional integral combina a ação de controle proporcional e integral.

![](./img/ControlePI.png)

```
        u(t)  Kp e(t) + Kp Ti ∫ 0t e(t) dt
```

onde, Ti é o tempo integral.

**Função de Transferência** (Transformada de Laplace):

```
              Us Es = Kp (1 + 1 Tis)
```

### Erro estacionário do controle proporcional

Sem o **controle integral** há um **erro estacionário** (também chamado **erro residual**) inerente ao **controle proporcional**.

**Gráfico do Controle PI**:

![](./img/GraficoPI.png)

Controle Proporcional Derivativo
--------------------------------

O **controle proporcional derivativo** combina o controle proporcional com o controle derivativo. O **controle derivativo** procura ajustar a ação de controle em função da taxa de variação do erro.

![](./img/ControlePD.png)

```
        u(t) = Kp e(t) + Kp Td de(t) dt
```

onde, Td é o tempo derivativo.

**Função de Transferência** (Transformada de Laplace):

```
              Us Es = Kp (1 + T ds)
```

### Ação do controle derivativo

A ação do **controle derivativo** é proporcional a **taxa de variação do erro** atuante. Deve ser usada em períodos transitórios.

**Gráfico do Controle PD**:

![](./img/GraficoPD2.png)

Controle Proporcional Integral Derivativo
-----------------------------------------

O **controle proporcional integral derivativo** combina as três ações de controle, visando atingir rapidamente a referência, minimizando os transitórios e eliminando o possível erro residual.

![](./img/ControlePID.png)

```
        u(t) = Kp e(t) + Kp Ti ∫ 0t e(t) dt + Kp Td de(t) dt
```

onde, Ti é o tempo integral e Td é o tempo derivativo.

**Função de Transferência** (Transformada de Laplace):

```
              Us Es = Kp (1 + 1T is + Tds)
```

**Gráfico do Controle PID**:

![](./img/GraficoPID2.png)

Referências
-----------

1. OGATA, Katsuhiko. Engenharia de Controle Moderno,5a Ed, Pearson, 2011.
