---
title: Circuítos para Operações Aritméticas
description: Grupo 13
---



## Soma e Subtração
### Meio Somador

O **meio somador** (Half-Adder) é um circuito digital básico projetado para realizar a soma de dois números binários de 1 bit cada. Ele é fundamental para operações aritméticas simples e serve como base para circuitos mais complexos, como o somador completo.

#### Estrutura do Meio Somador
- **Entradas:**
  - `A`: Primeiro bit a ser somado.
  - `B`: Segundo bit a ser somado.

- **Saídas:**
  - **S** (soma): Representa o resultado da soma dos bits `A` e `B`, sem considerar um "vai um" (carry). É calculada utilizando a operação lógica `A ⊕ B` (XOR), que resulta em:
    - `S = 0`, quando `A` e `B` são iguais.
    - `S = 1`, quando `A` e `B` são diferentes.
  - **Cout** (carry): Indica se há um "vai um", ou seja, se a soma ultrapassa 1. É calculado com `A ⋅ B` (AND), sendo:
    - `Cout = 1`, quando `A = 1` e `B = 1`.
    - `Cout = 0` nos outros casos.

#### Funcionamento
O meio somador realiza a soma de dois bits de forma simples:
- Se ambos os bits são `0`, a soma (`S`) é `0` e não há carry (`Cout`).
- Se apenas um dos bits é `1`, a soma (`S`) é `1` e `Cout` continua `0`.
- Quando ambos os bits são `1`, a soma (`S`) é `0` e o carry (`Cout`) é `1`.

#### Tabela Verdade

| `A` | `B` | `S` (Soma) | `Cout` (Carry) |
|:---:|:---:|:----------:|:--------------:|
|  0  |  0  |     0      |       0        |
|  0  |  1  |     1      |       0        |
|  1  |  0  |     1      |       0        |
|  1  |  1  |     0      |       1        |

#### Aplicações
O meio somador é utilizado em circuitos aritméticos para somar bits individuais, como no cálculo de somas parciais em somadores de múltiplos bits. Para operações mais completas, como a soma de números binários maiores, é necessário o uso de **somadores completos**, que consideram o "carry in" de somas anteriores.

![image](https://github.com/user-attachments/assets/fd231611-653a-4c06-a697-fd2709e283ea)

### Somador Completo

O **somador completo** (Full-Adder) é um circuito digital capaz de somar dois números binários de 1 bit cada e considerar um "carry in" (Cin) vindo de uma soma anterior. Ele é fundamental para operações de soma em números binários maiores.

#### Estrutura do Somador Completo
- **Entradas:**
  - `A`: Primeiro bit a ser somado.
  - `B`: Segundo bit a ser somado.
  - `Cin`: Carry in (resultado de um "vai um" vindo da soma anterior).

- **Saídas:**
  - **S** (soma): Representa o resultado da soma dos bits `A`, `B` e `Cin`. É calculada com a operação lógica:
    - `S = A ⊕ B ⊕ Cin` (XOR).
  - **Cout** (carry out): Indica se há um "vai um" gerado pela soma, calculado como:
    - `Cout = (A ⋅ B) + (A ⋅ Cin) + (B ⋅ Cin)`.

#### Funcionamento
O somador completo realiza a soma considerando três valores de entrada (`A`, `B` e `Cin`):
- Se a soma dos três bits for menor que 2, `Cout = 0`.
- Se a soma dos três bits for maior ou igual a 2, `Cout = 1`.
- O bit menos significativo do resultado é representado por `S`.

#### Tabela Verdade

| `A` | `B` | `Cin` | `S` (Soma) | `Cout` (Carry) |
|:---:|:---:|:-----:|:----------:|:--------------:|
|  0  |  0  |   0   |     0      |       0        |
|  0  |  0  |   1   |     1      |       0        |
|  0  |  1  |   0   |     1      |       0        |
|  0  |  1  |   1   |     0      |       1        |
|  1  |  0  |   0   |     1      |       0        |
|  1  |  0  |   1   |     0      |       1        |
|  1  |  1  |   0   |     0      |       1        |
|  1  |  1  |   1   |     1      |       1        |

#### Aplicações
O somador completo é utilizado em circuitos de somadores de múltiplos bits, como os somadores de 4, 8 ou mais bits. Para isso, os "carry out" de cada somador são conectados ao "carry in" do próximo bit. Ele é essencial para operações em processadores e sistemas digitais que demandam cálculos binários complexos.

![image](https://github.com/user-attachments/assets/b227e80b-79cb-4d4e-852b-793999dc3101)
### Meio Subtrator

O **meio subtrator** (Half-Subtractor) é um circuito digital básico projetado para realizar a subtração de dois números binários de 1 bit. Ele é essencial para operações aritméticas simples e serve como base para circuitos subtratores mais complexos.

#### Estrutura do Meio Subtrator
- **Entradas:**
  - `A`: Minuendo (valor do qual será subtraído).
  - `B`: Subtraendo (valor a ser subtraído).

- **Saídas:**
  - **S** (subtração): Representa o resultado da subtração dos bits `A` e `B`. É calculada com a operação lógica:
    - `S = A ⊕ B` (XOR).
  - **Bout** (borrow out): Indica se foi necessário "emprestar" um bit para realizar a subtração, calculado como:
    - `Bout = ¬A ⋅ B` (NOT de A AND B).

#### Funcionamento
O meio subtrator realiza a subtração de dois bits binários:
- Se `A` for maior ou igual a `B`, a subtração (`S`) reflete a diferença, e `Bout` é `0`.
- Se `B` for maior que `A`, o resultado (`S`) considera o empréstimo, e `Bout` será `1`.

#### Tabela Verdade

| `A` | `B` | `S` (Subtração) | `Bout` (Borrow) |
|:---:|:---:|:---------------:|:---------------:|
|  0  |  0  |        0        |        0        |
|  0  |  1  |        1        |        1        |
|  1  |  0  |        1        |        0        |
|  1  |  1  |        0        |        0        |

#### Aplicações
O meio subtrator é usado em circuitos que realizam subtrações simples entre dois bits individuais. No entanto, para subtrações envolvendo números binários maiores ou operações que exigem o controle de "borrow in", é necessário o uso de subtratores completos.

![image](https://github.com/user-attachments/assets/6b8f653f-3e4b-4353-822b-080f77878e92)
### Subtrator Completo

O **subtrator completo** (Full-Subtractor) é um circuito digital que realiza a subtração de dois números binários de 1 bit, considerando um "borrow in" (Bin) proveniente de uma subtração anterior. Ele é essencial para operações de subtração em números binários maiores.

#### Estrutura do Subtrator Completo
- **Entradas:**
  - `A`: Minuendo (valor do qual será subtraído).
  - `B`: Subtraendo (valor a ser subtraído).
  - `Bin`: Borrow in (empréstimo de uma subtração anterior).

- **Saídas:**
  - **S** (subtração): Representa o resultado da subtração de `A`, `B` e `Bin`. É calculada com a operação lógica:
    - `S = A ⊕ B ⊕ Bin` (XOR).
  - **Bout** (borrow out): Indica se foi necessário "emprestar" um bit para realizar a subtração, calculado como:
    - `Bout = (¬A ⋅ B) + (¬A ⋅ Bin) + (B ⋅ Bin)`.

#### Funcionamento
O subtrator completo realiza a subtração considerando as três entradas (`A`, `B` e `Bin`):
- Se `A` for suficientemente grande para subtrair `B` e `Bin`, `Bout = 0`.
- Caso contrário, `Bout = 1`, indicando que foi necessário "emprestar" um bit de uma subtração mais significativa.

#### Tabela Verdade

| `A` | `B` | `Bin` | `S` (Subtração) | `Bout` (Borrow) |
|:---:|:---:|:-----:|:---------------:|:---------------:|
|  0  |  0  |   0   |        0        |        0        |
|  0  |  0  |   1   |        1        |        1        |
|  0  |  1  |   0   |        1        |        1        |
|  0  |  1  |   1   |        0        |        1        |
|  1  |  0  |   0   |        1        |        0        |
|  1  |  0  |   1   |        0        |        1        |
|  1  |  1  |   0   |        0        |        0        |
|  1  |  1  |   1   |        1        |        1        |

#### Aplicações
O subtrator completo é usado em circuitos que realizam subtrações entre números binários de múltiplos bits. Para isso, os "borrow out" de cada subtrator são conectados ao "borrow in" do próximo bit. Ele é amplamente utilizado em sistemas digitais e processadores para operações aritméticas mais complexas.

![image](https://github.com/user-attachments/assets/b8bb1432-cecc-48f9-9d97-5b6520917f2e)



## Multiplicação

### Multiplicação em Circuitos Digitais

A **multiplicação** em circuitos digitais segue princípios semelhantes à multiplicação manual de números decimais, adaptados para números binários. O objetivo é obter o produto de dois números binários (multiplicando e multiplicador) por meio de adições e deslocamentos.

#### **Conceitos Básicos**
1. **Deslocamento de Bits**:
   - Um número binário pode ser multiplicado por 2 simplesmente deslocando todos os bits para a esquerda e adicionando um zero no bit menos significativo. Por exemplo:
     - `B = 0110` (6 em decimal), deslocado uma posição para a esquerda, torna-se `B = 1100` (12 em decimal).
   - Multiplicações por `2^k` podem ser realizadas deslocando os bits `k` vezes.

2. **Multiplicação Manual**:
   - Cada bit do multiplicador é analisado da direita para a esquerda.
   - Se o bit é `1`, uma versão deslocada do multiplicando é somada ao resultado parcial.
   - Se o bit é `0`, nada é adicionado.
   - O processo se repete até que todos os bits do multiplicador tenham sido processados.

#### **Implementação de Circuitos de Multiplicação**
1. **Multiplicador Array** (para números não assinados):
   - A multiplicação é realizada por meio de somadores e portas lógicas, organizados em uma estrutura matricial.
   - Cada linha da matriz representa um **produto parcial** gerado pela operação lógica AND entre os bits do multiplicador e os do multiplicando.
   - Os produtos parciais são deslocados e somados para formar o produto final.
   - Exemplo:
     - Multiplicando (`M`) = `1011` (11 em decimal).
     - Multiplicador (`Q`) = `1101` (13 em decimal).
     - O produto (`P`) = `10001111` (143 em decimal).

2. **Circuito para Multiplicação de 4×4 Bits**:
   - Usa portas **AND** para gerar os produtos parciais.
   - Utiliza **somadores completos** (Full-Adders) conectados em série para calcular as somas dos produtos parciais, formando o resultado final.
   - Esse tipo de multiplicador pode ser estendido para números maiores.

3. **Multiplicação de Números Assinados**:
   - Quando os números têm sinal (positivo ou negativo), é necessário utilizar **extensão de sinal** para garantir que os cálculos sejam corretos.
   - Para multiplicadores negativos, os números podem ser convertidos para **complemento de dois** antes da multiplicação, garantindo a precisão.

#### **Exemplo de Circuito**
No caso de um multiplicador de 4×4 bits:
- Multiplicando (`M`) e multiplicador (`Q`) têm 4 bits.
- O resultado (`P`) ocupa 8 bits.
- Produtos parciais são gerados por **AND** entre `Q[i]` e cada bit de `M`.
- Os produtos parciais são deslocados e somados por **somadores completos**.

#### **Vantagens e Aplicações**
1. **Simplicidade**:
   - A multiplicação binária segue padrões simples de deslocamento e soma, facilmente implementados com circuitos lógicos básicos.
2. **Eficiência**:
   - O uso de multiplicadores em hardware acelera cálculos em processadores e sistemas digitais.
3. **Aplicações**:
   - Processadores e microcontroladores.
   - Sistemas de processamento de sinais.
   - Algoritmos de gráficos e aprendizado de máquina.

Esse processo de multiplicação forma a base para cálculos aritméticos complexos em sistemas digitais e computação moderna.
![image](https://github.com/user-attachments/assets/9febfe06-bd07-4808-8577-7da5486e8cc4)






## OBS: AINDA VAMOS LAPIDAR A MULTIPLICAÇÃO E TERMINAR A DIVISÃO
## Divisão

## Exercícios
:::note TODO
Grupo 17
:::
