# Relatório

## Componente 01: Registrador Flip-Flop do tipo D e do tipo JK.

---

### 1. Descrição do Componente

- *Descrição Geral:* De forma geral, podemos representar o flip-flop como um bloco onde temos 2 saídas: Q e ~Q (Não Q), entradas para as variáveis e uma entrade de controle (CLOCK). A saída Q será a principal do bloco. O Flip-Flop JK e D buscam solucionar algumas limitações do Flip-Flop RS, como por exemplo o estado instável R = 1 / S = 1, que não poderá ser permitido na entrada, pois forçará o flip-flop a assumir um estado de saída, no qual a saída Q será igual à saída complementar ~Q. O Flip-Flop do tipo *D* (D), que representa a palavra data(dado), transfere o valor da entrada \(D\) para a saída \(Q\) no pulso do clock. O Flip_Flop *JK* nada mais é que um flip-flop RS realimentado com as saídas Q e ~Q. Comparado com o S-R, o flip-flop J-K é mais versátil, pois não possui estados ambíguos. A condição J = K = 1, que causa a operação de comutação da saída, é amplamente utilizada em todos os tipos de contadores binários. Em resumo, o flip-flop J-K pode realizar todas as funções do S-R, além de operar no modo de comutação.

- *Pinos e Lógica do Componente:*

  #### Flip-Flop Tipo D:
  | Pino | Nome/Função   | Descrição                                         |
  |------|---------------|---------------------------------------------------|
  | 1    | Entrada D     | Entrada de dados. Valor a ser armazenado.         |
  | 2    | Clock (CLK)   | Pulso de sincronização do Flip-Flop.              |
  | 3    | Q             | Saída do estado armazenado (1 ou 0).              |
  | 4    | Q'            | Saída complementar de \(Q\).                      |
  


  #### Flip-Flop Tipo JK:
  | Pino | Nome/Função   | Descrição                                            |
  |------|---------------|------------------------------------------------------|
  | 1    | Entrada J     | Entrada de controle para setar \( J = 1, K = 0 \).   |
  | 2    | Entrada K     | Entrada de controle para resetar \( J = 0, K = 1 \). |
  | 3    | Clock (CLK)   | Pulso de sincronização do Flip-Flop.                 |
  | 4    | Q             | Saída do estado armazenado (1 ou 0).                 |
  | 5    | Q'            | Saída complementar de \(Q\).                         |



  - *Função Lógica:*  
  #### Flip-Flop Tipo D:
  - Quando ocorre um pulso no clock \(CLK\):
    - \( Q = D \)
    - \( Q' = ~D \)

  #### Flip-Flop Tipo JK:
  - Quando ocorre um pulso no clock \(CLK\):
    - \( J = 0, K = 0 \): Sem alteração no estado.
    - \( J = 0, K = 1 \): \( Q = 0 \) (Reset).
    - \( J = 1, K = 0 \): \( Q = 1 \) (Set).
    - \( J = 1, K = 1 \): \( Q = ~Q \) (Comuta).

---

### 2. Testes Realizados

#### Configuração do Teste

- *Descrição do Teste:*  
  Testamos o comportamento dos Flip-Flops \(D\) e \(JK\) sob diferentes condições de entrada e sinais de clock para validar o armazenamento e as alterações de estado.

- *Entradas, Conexões e Saídas Esperadas:*  

  #### Flip-Flop Tipo D:
  | Entrada D | Clock (CLK)  | Q Obtido | Q' Obtido|
  |-----------|--------------|----------|----------|
  | 0         | 1            | 0        | 1        |
  | 1         | 1            | 1        | 0        |
  

  #### Flip-Flop Tipo JK:
  | Entrada J | Entrada K | Clock (CLK) | Q Esperado    | Q' Esperado   |
  |-----------|-----------|-------------|------------   |------------   |
  | 0         | 0         | 1           | Sem Alteração | Sem Alteração |
  | 0         | 1         | 1           | 0             | 1             |
  | 1         | 0         | 1           | 1             | 0             |  
  | 1         | 1         | 1           | Comuta        | Comuta        |