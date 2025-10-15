## **Componente: Memória RAM com Registradores e Multiplexadores**

---

### **1. Descrição do Componente**

- **Descrição Geral:**
  Este componente é uma memória RAM funcional composta por 8 registradores de 8 bits cada. Ele permite realizar operações de leitura e escrita de dados utilizando sinais de controle e endereçamento. Um multiplexador 8x1 é utilizado para selecionar qual registrador será lido. A escrita em um registrador é controlada por um demultiplexador derivado do sinal de controle e do endereço fornecido.

### Componentes do Registrador:

- **Registrador de 1 Bit**
- *Captura de Tela do Circuito em Logisim:*
  
  ![Componentes do Registrador](Imagens/FlipFlopRS.png)
  *Legenda:* Circuito básico para armazenar 1 bit utilizando flip-flop tipo SR.

- **Registrador de 1 Bit**

![Componentes do Registrador](Imagens/Reg1Bit.png)
*Legenda:* Um registrador de 1 byte formado por 8 flip-flops conectados.

- **Enable no Registrador**
  
  ![Componentes do Registrador](Imagens/Enable.png)
  *Legenda:* Circuito com controle de habilitação (`Enable`) para decidir se o dado será armazenado ou mantido.


- **Registrador Completo**

  ![Componentes do Registrador](Imagens/RegComp.png)
  *Legenda:* Registrador completo com suporte a múltiplos bytes, controlado por sinais de habilitação.

---

- Funcionamento Geral:

1. **Entrada de Dados:**  
   - Dados são fornecidos ao registrador por meio das entradas de bits.
   - O número de bits depende do tipo de registrador (1 bit, 1 byte, ou múltiplos bytes).

2. **Habilitação (`Enable`):**  
   - Controla se os dados de entrada serão armazenados no registrador.
   - Se desativado, o registrador mantém seu valor atual.

3. **Armazenamento:**  
   - Os flip-flops mantêm os valores armazenados até que sejam sobrescritos ou redefinidos.


- Aplicações dos Registradores: 

   - Armazenamento Temporário:** Mantém dados intermediários em operações digitais.
   - Controle em Sistemas Digitais:** Usado para armazenar sinais de controle.
   - Operações em Unidade Lógica e Aritmética (ULA):** Registradores são essenciais para o processamento de dados.
  
---
### Esquema dos Multiplexadores:
  
  ![Componentes do Registrador](Imagens/Mux8x1.png)
  *Legenda:* Multiplexador de 8x1 utilizado para selecionar o registrador que será lido na sáida de 8 bits.
- **Descrição do Esquema:**
  Para o desenvolvimento do banco de registradores foi necessário criar um multiplexador de 8x1, no entanto para cria-lo é preciso desenvolver primeiramente os multiplexadores abaixo.
  
- **Multiplexador 2x1:**

  ![Componentes do Registrador](Imagens/Mux2x1.png)

  *Legenda:* Multiplexador de 2x1 com duas entradas 1 bit que será usado para criar o multiplexador com duas entradas de 8 bits cada.
  
- **Multiplexador 2x1 8 bits:**
  
  ![Componentes do Registrador](Imagens/Mux2x1x8.png)
  *Legenda:* Incrementa a entrada e saída de 8 bits utilizando o mux 2x1.
  
- **Multiplexador 4x1:**
  
  ![Componentes do Registrador](Imagens/Mux4x1.png)
  *Legenda:* Último mux necessário para desenvolver o mux 8x1.
  
---

- **Pinos e Lógica do Componente:**
  | Pino                  | Nome/Função               | Descrição                                             |
  |-----------------------|---------------------------|-----------------------------------------------------|
  | Entrada \(D[7:0]\)    | Dados                    | Entrada dos dados a serem escritos.                |
  | Entrada \(WRITE\)     | Sinal de Escrita         | Habilita a escrita no registrador selecionado.     |
  | Entrada \(READ\)      | Sinal de Leitura         | Habilita a leitura do registrador selecionado.     |
  | Entrada \(ADDR[2:0]\) | Endereço de Escrita      | Seleciona qual registrador receberá os dados.      |
  | Entrada \(ADDR\_READ\) | Endereço de Leitura     | Seleciona qual registrador será lido.              |
  | Saída \(Q[7:0]\)      | Dados de Saída           | Exibe os dados do registrador selecionado para leitura. |

- **Função Lógica:**
  - **Escrita:** Quando \(WRITE = 1\), os dados presentes na entrada \(D\) são armazenados no registrador selecionado por \(ADDR\).
  - **Leitura:** Quando \(READ = 1\), o valor armazenado no registrador selecionado por \(ADDR\_READ\) é enviado para \(Q\).
  - **Controle via Multiplexadores:**
    - Um multiplexador 8x1 seleciona a saída do registrador para a operação de leitura.
    - O demultiplexador distribui o sinal \(WRITE\) para habilitar apenas o registrador correto.

---

### **2. Esquema do Circuito**

- **Captura de Tela do Circuito no Logisim:**
  <img src="Imagens/MemoriaRam.png" alt="memoria-ram-completo" />
  *Legenda: Circuito da memória RAM com 8 registradores e multiplexador implementado no Logisim.*

- **Descrição do Esquema:**
  1. **Registradores:** O circuito utiliza 8 registradores de 8 bits. Cada registrador possui entrada de dados (\(D\)), saída de dados (\(Q\)), e habilitação de escrita (\(W\)).
  2. **Demultiplexador:** O demultiplexador recebe o sinal \(WRITE\) e o endereço \(ADDR[2:0]\), ativando apenas o registrador selecionado.
  3. **Multiplexador:** O multiplexador 8x1 coleta as saídas dos 8 registradores e seleciona qual será enviada para a saída geral \(Q\), controlado pelo endereço \(ADDR\_READ\).

---

### **3. Testes Realizados**

#### **Configuração do Teste**

- **Objetivo:**
  Verificar a correta funcionalidade da memória RAM para operações de leitura e escrita nos registradores específicos.

- **Entradas, Conexões e Saídas Esperadas:**
  | Pino de Entrada | Sinal Aplicado   | Pino de Saída | Resultado Esperado |
  |-----------------|------------------|---------------|---------------------|
  | \(D = 10101001\), \(ADDR = 011\), \(WRITE = 1\) | Escrever no registrador 3 | Não aplicável | Valor \(10101001\) armazenado no registrador 3 |
  | \(ADDR\_READ = 011\), \(READ = 1\)             | Ler do registrador 3      | \(Q\)         | \(10101001\)                         |
  | \(ADDR\_READ = 101\), \(READ = 1\)             | Ler do registrador 5      | \(Q\)         | \(00000000\)                         |

---

#### **Configuração do Logisim**

- **Configurações Utilizadas:**
  - Frequência do clock: Simulado manualmente, utilizando botões para os sinais de controle.
  - Utilização de probes para verificar os valores armazenados nos registradores e na saída.

---

### **4. Resultados dos Testes**

#### **Resultados Obtidos no Logisim**
| Pino de Entrada | Sinal Aplicado   | Pino de Saída | Resultado Obtido |
|-----------------|------------------|---------------|------------------|
| \(D = 10101001\), \(ADDR = 011\), \(WRITE = 1\) | Escrever no registrador 3 | Não aplicável | Valor \(10101001\) armazenado no registrador 3 |
| \(ADDR\_READ = 011\), \(READ = 1\)             | Ler do registrador 3      | \(Q\)         | \(10101001\)                         |
| \(ADDR\_READ = 101\), \(READ = 1\)             | Ler do registrador 5     | \(Q\)         | \(00000000\)                         |

#### **Captura de Tela do Resultado**
<img src="Imagens/TesteEscritaRam.png" alt="teste-de-escrita-na-memoria-ram" />

  *Legenda: Testes realizados no circuito para escrita no registrador 3 no Logisim.*

<img src="Imagens/TesteLeituraRam.png" alt="teste-de-leitura-na-memoria-ram" />

  *Legenda: Teste realizado no circuito para leitura do registrador 3 no Logisim.*
  
<img src="Imagens/TesteIsolamentoRam.png" alt="teste-de-isolamento-na-memoria-ram" />

  *Legenda: Teste realizado no circuito para leitura do registrador 5 no Logisim.*
#### **Análise dos Resultados**
- **Escrita:** O valor \(10101001\) foi armazenado corretamente no registrador 3 quando \(WRITE = 1\).
- **Leitura:** O valor armazenado no registrador 3 foi lido corretamente com \(READ = 1\) e \(ADDR\_READ = 010\).
- **Isolamento:** O registrador 5 (não afetado pela escrita) retornou \(00000000\), confirmando o isolamento entre registradores.

---
