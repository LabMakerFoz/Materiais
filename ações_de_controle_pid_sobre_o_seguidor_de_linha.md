# Ações de Controle PID sobre o Seguidor de Linha

Ações de Controle PID sobre o Seguidor de Linha
===============================================

Ação de Controle Proporcional
-----------------------------

A ação de **controle proporcional** do Seguidor de Linha vai corrigir a trajetória do robô, ajustando a velocidades dos motores a partir de um **ganho Kp**, proporcional ao **erro**:

```
        C
        o
        n
        t
        r
        o
        l
        e
        P
        =
        K
        p
        ∗
        e
        r
        r
        o
      
    
    {\displaystyle ControleP=Kp*erro}
  
![{\displaystyle ControleP=Kp*erro}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e962e6c332e5f14ba311d5abf068e713e1b497cb)
```

Caso o robô derive para esquerda, a velocidade dos motores é ajustada para que o robô volte para a linha:

* a **velocidade do motor esquerdo** é **acrescida** do valor **K
  p
  ∗
  e
  r
  r
  o
  {\displaystyle Kp\*erro}
  ![{\displaystyle Kp*erro}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e1c6aa5f32683c95eebc18be10087379f60e00d)**;
* a **velocidade do motor direito** é **diminuída** do valor **K
  p
  ∗
  e
  r
  r
  o
  {\displaystyle Kp\*erro}
  ![{\displaystyle Kp*erro}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e1c6aa5f32683c95eebc18be10087379f60e00d)**.

Caso o robô derive para direita, a ação de controle ajusta a velocidade dos motores para corrigir a trajetória para o outro lado.

Ação de Controle Proporcional Integral
--------------------------------------

A ação de **controle proporcional integral** do vai corrigir a trajetória do robô combinando a ação proporcional e a integral.

O **controle integral** ajusta a ação de controle em função ao **somatório do erro** em um dado intervalo de tempo, chamado **tempo integral**.

#### Hipótese I: Análise sobre a ação do controle integral

Algumas hipóteses de análise do controle integral sobre o robô Seguidor de Linha:

Caso de uma RETA
:   Algumas situações possíveis são:

1. O robô **segue a linha** com **erro zero**.
2. O robô **deriva aleatoriamente para um lado e para outro** resultando, provavelmente, em **somatório de erro** também **zero**.

   :   Nestes dois casos, portanto, como o **somatório de erro** é **zero**, **controle integral** tem **ação nula**.
3. O robô **deriva sistematicamente para um lado** devido a possíveis **desequilíbrios de velocidades dos motores**, levando com o passar do tempo a um **somatório de erro diferente de zero** para um dos lados.

   :   Neste caso, inicialmente somente o controle proporcional atua, ajustando a trajetória do robô em função do desequilíbrio de velocidades. Entretanto, **a medida que o somatório do erro cresce**, o **controle integral** passa a atuar. Quando o robô passar a **seguir linha** com **erro instantâneo zero**, o **controle integral** continua agindo equilibrando as velocidades a partir do **somatório de erro acumulado**.
   :   Vemos esta ação como equivalente a eliminação do **erro residual**[[1]](#cite_note-OGATA-1) existente em alguns controles de ação proporcional.

Caso de uma CURVA
:   O **somatório de erros** será **diferente de zero** em função do lado da curva.
:   Inicialmente somente o controle proporcional atua, ajustando a trajetória do robô à curva. Entretanto, **a medida que o somatório do erro cresce**, o **controle integral** passa a atuar. A partir de um dado momento, o **controle integral** passa a prevalecer, fazendo o robô **acompanhar a curva** com **erro instantâneo zero**, portanto, sem ação proporcional.

```
        C
        o
        n
        t
        r
        o
        l
        e
        P
        I
        =
        K
        p
        ∗
        e
        r
        r
        o
        +
        K
        i
        ∗
        ∑
        e
        r
        r
        o
      
    
    {\displaystyle ControlePI=Kp*erro+Ki*\sum erro}
  
![{\displaystyle ControlePI=Kp*erro+Ki*\sum erro}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce303d2fed7cdef6c2f3952a7ba14da6cb2bfb56)
```

#### Problema I: Verificação da ação do controle integral

Construir protótipo Seguidor de Linha e experimentações para verificar a validade destas hipóteses sobre a **ação do controle integral**.

### Tempo integral

O tempo integral é o tempo da ação do controle integral.

#### Hipótese II: Delimitação do tempo integral na pista do Seguidor de Linha

Para os casos relatados acima, seria interessante **reiniciar** o **tempo de integração** a cada **início de reta** e a cada **início de curva**.

Marcações de pista do seguidor de linha
:   No caso da **pista** para o Seguidor de Linha, as **marcações de início e fim de curva** poderiam ser utilizadas como delimitadores dos **tempos integração**. Neste caso, a **cada marcação** encontrada, se poderia **zerar** o **somatório de erros**, iniciando, portanto, um novo **tempo de integração**.

#### Problema II: Teste do tempo integral

Construir protótipo Seguidor de Linha e experimentações para verificar a validade da hipótese sobre **reiniciar o tempo integral a cada início de reta ou curva**a.

Ação de Controle Proporcional Derivativa
----------------------------------------

A ação do **controle derivativo** é proporcional a **taxa de variação do erro** atuante. Vai ter ação, portanto, nos **períodos transitórios** quando o **erro cresce ou diminui**.

```
        C
        o
        n
        t
        r
        o
        l
        e
        P
        D
        =
        K
        p
        ∗
        e
        r
        r
        o
        +
        K
        d
        ∗
        Δ
        e
        r
        r
        o
      
    
    {\displaystyle ControlePD=Kp*erro+Kd*\Delta erro}
  
![{\displaystyle ControlePD=Kp*erro+Kd*\Delta erro}](https://wikimedia.org/api/rest_v1/media/math/render/svg/310041b8879920533d5ea8ec8117c9615df4da6c)
```

No caso do robô Seguidor de Linha, quando o **erro cresce**, o **controle derivativo** atua **reforçando** a ação do **controle proporcional**.

Quando o **erro diminiu**, o **controle derivativo** atua **atenuando** a ação do **controle proporcional**.

#### Hipótese III: Análise sobre a ação do controle derivativo

Algumas hipóteses de análise do controle derivativo sobre o robô Seguidor de Linha:

1. Quando o **erro estabiliza**, isto é, permanece constante, o **controle derivativo** passa a ter **ação nula** e somente o controle proporcional atua levando o robô de volta a linha.
2. Quando a ação do controle proporcional corrigir a trajetória, fazendo o **erro diminuir**, o controle proporcional também diminui, e o **controle derivativo** atua em **sentido inverso**, atenuando o controle proporcional e evitando que saia para fora do outro lado da linha.

   :   Esta última ação do controle derivativo visa diminuir a ação do controle proporcional a medida nos aproximamos do ponto de referência.

#### Problema III: Verificação da ação do controle derivativo

Construir protótipo Seguidor de Linha e experimentações para verificar a validade destas hipóteses sobre a **ação do controle derivativo**.

### Tempo Derivativo

Segundo [[2]](#cite_note-LabGaragem-2), o **tempo derivativo** está relacionado a **taxa de amostragem** dos **sensores**, que corresponde ao *loop* de execução do programa.

Acelerar ou retardar o tempo derivativo pode fazer uma diferença significativa no desempenho do robô. Isso é definido pelas declarações de ***delay*** presentes no código [[2]](#cite_note-LabGaragem-2).

#### Problema IV: Verificação da ação do tempo derivativo

Construir protótipo e experimentações para **verificar a ação do tempo derivativo** na estabilidade do Seguidor de Linha.

Ajuste dos parâmetros do controlador PID
----------------------------------------

Um dos pontos chaves do bom funcionamento de **controladores PID** está no **ajuste dos parâmetros** do controlador, ou seja, os ganhos **Kp**, **Ki** e **Kd**.

Em muitos controladores PID industriais, o ajuste dos parâmetros fica a cargo do operador especialista na planta a ser controlada.

### Regras de sintonia de Ziegler-Nichols

Ziegler e Nichols sugeriram **regras de sintonia para controladores PID**, através dos valores de **Kp**, **Ti** e **Td**, baseadas em respostas experimentais.

Estas regras devem ser testadas e experimentadas para o caso do Seguidor de Linha.

#### Problema V: Pesquisa e teste da sintonia de Ziegler-Nichols

**Pesquisar a sintonia de Ziegler-Nichols** e construir protótipo Seguidor de Linha e experimentações **testar a sintonia de Ziegler-Nichols**, assim como formas de obter o **tempo integral** e o **tempo derivativo**.

Referências
-----------

1. [↑](#cite_ref-OGATA_1-0) OGATA, Katsuhiko. Engenharia de Controle Moderno, LTC, 2011.
2. ↑  <http://labdegaragem.com/profiles/blogs/tutorial-rob-seguidor-de-linha-com-controle-pid-e-ajustes-por>

---

--[Evandro.cantu](/wiki/index.php/Usu%C3%A1rio:Evandro.cantu "Usuário:Evandro.cantu") ([discussão](/wiki/index.php?title=Usu%C3%A1rio_Discuss%C3%A3o:Evandro.cantu&action=edit&redlink=1 "Usuário Discussão:Evandro.cantu (página inexistente)")) 22h04min de 18 de outubro de 2018 (BRT)

---
