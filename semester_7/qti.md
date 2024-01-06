# Quantum Technologies and Information
Transcript and summary of the lecture given by Prof Dr. Ulrich Margull at the Ingolstadt University of Applied Sciences. All rights reserved by the original author(s). 

## Contents
- [Quantum Technologies and Information](#quantum-technologies-and-information)
  - [Contents](#contents)
- [Classical Bits and Gates](#classical-bits-and-gates)
- [Single Qubits](#single-qubits)
  - [Single Qubit Gates](#single-qubit-gates)
    - [Pauli Gates](#pauli-gates)
    - [Hadamard Gate](#hadamard-gate)
- [Quantum Registers (and Entanglement)](#quantum-registers-and-entanglement)
  - [CNOT (controlled Pauli-X)](#cnot-controlled-pauli-x)
  - [Entanglement](#entanglement)
  - [SWAP-Gate](#swap-gate)
  - [Toffoli-Gate](#toffoli-gate)
  - [Multiple Hadamard Gates](#multiple-hadamard-gates)

# Classical Bits and Gates
One bit is represented by an vector $0 = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$ or $1 = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$. The boolean `NOT` gate is represented by the matrix $\begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$.

**AND-Gate** <br>
The AND-Gate has `2` input bits, therefore two bits are represented by a 4-dimensional vector. 

$`00 = \begin{pmatrix} 1 \\ 0 \\ 0 \\ 0 \end{pmatrix}`$, $01 = \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix}$, $10 = \begin{pmatrix} 0 \\ 0 \\ 1 \\ 0 \end{pmatrix}$, $11 = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 1 \end{pmatrix}$

<details><summary>math</summary>

The related matrix has has $2 \times 4$ dimensions.

$\begin{pmatrix} q_1 \\ q_2 \end{pmatrix} = \begin{pmatrix} x_{11} & x_{12} & x_{13} & x_{14} \\ x_{21} & x_{22} & x_{23} & x_{24} \end{pmatrix} \begin{pmatrix} a_1 \\ a_2 \\ b_1 \\ b_2 \end{pmatrix}$ 

</details> <br>

And the `boolean-AND` therefore is represented by following matrix

$AND = \begin{pmatrix} 1 & 1 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$

**NAND-Gate** <br>
The NAND-Gate is the negation of the AND-Gate. Therefore the matrix is the negation of the AND-Gate matrix.

$`NAND = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \cdot \begin{pmatrix} 1 & 1 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix} = \begin{pmatrix} 0 & 0 & 0 & 1 \\ 1 & 1 & 1 & 0 \end{pmatrix}`$

**Parralel Gates** <br>
The most simple case are two `NOT` gates in parralel. 

<img src="resources/qti/00_X_AND.png" width="200"/>

Now we have two inputs and two outputs, both are 4-dimensional vectors. 

$`a= \begin{pmatrix} a_0 \\ a_1 \end{pmatrix}$, $b= \begin{pmatrix} b_0 \\ b_1 \end{pmatrix}$ and the input then is $a \otimes b = \begin{pmatrix} a_0 b_0 \\ a_0 b_1 \\ a_1 b_0 \\ a_1 b_1 \end{pmatrix}`$

<details><summary>example</summary>

$`|01\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix} \otimes \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 \cdot \begin{pmatrix} 0 \\ 1 \end{pmatrix} \\ 0 \cdot \begin{pmatrix} 0 \\ 1 \end{pmatrix} \end{pmatrix} = \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix}`$.

</details> <br>

The same applies to the gates - the combination of both parallel gates is the tensor product of the infdividual gates.

$`X = NOT \otimes NOT = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \otimes \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} = \begin{pmatrix} 0 \cdot \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} & 1 \cdot \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \\ 1 \cdot \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} & 0 \cdot \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \end{pmatrix} = \begin{pmatrix} 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{pmatrix}`$

<details><summary>example</summary>

For example, the input $|01\rangle$ yields the output $|10\rangle$.

$`\begin{pmatrix} 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{pmatrix} |01\rangle = X \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 1 \\ 0 \end{pmatrix} = |10\rangle`$

</details> <br>

The concatenation of the two steps $x$ and $AND$ is the normal product of the matrices (in reverse order).

$`|e\rangle = AND \cdot X = \begin{pmatrix} 1 & 1 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix} \cdot X = \begin{pmatrix} 0 & 1 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{pmatrix}|ab\rangle`$

<details><summary>example</summary>

For example, the input $|01\rangle$ yields $|0\rangle$ as output.

$`\begin{pmatrix} 0 & 1 & 1 & 1 \\ 1 & 0 & 0 & 0 \end{pmatrix} |01\rangle = \begin{pmatrix} 0 & 1 & 1 & 1 \\ 1 & 0 & 0 & 0 \end{pmatrix} \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 \\ 0 \end{pmatrix} = |0\rangle`$

</details> <br>

# Single Qubits
A single qubit is represented by a 2-dimensional vector.

$`| \psi \rangle = \alpha |0\rangle + \beta |1\rangle = \alpha \begin{pmatrix} 1 \\ 0 \end{pmatrix} + \beta \begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} \alpha \\ \beta \end{pmatrix}`$

The qubit is normalized, therefore $|\alpha|^2 + |\beta|^2 = 1$ and $\alpha, \beta \in \mathbb{C}$. The fact  that a qubit is partly in state $|0\rangle$ and $|1\rangle$ is called _superposition_.

When we measure the qubit, the probability of the measured state is given by

$`P(|0\rangle) = |\alpha|^2$ and $P(|1\rangle) = |\beta|^2`$

and the sum of both will be $1$.

<!-- 
https://moodle.thi.de/pluginfile.php/703143/mod_resource/content/20/QCI_script.pdf

S. 19
-->

**Special Qubits** <br>
There are two common special qubits, the $|+\rangle$ and $|-\rangle$ qubit.

$`|+\rangle = \frac{1}{\sqrt{2}} (|0\rangle + |1\rangle)`$ <br>
$`|-\rangle = \frac{1}{\sqrt{2}} (|0\rangle - |1\rangle)`$ <br>

In this case, the probability of measuring $|0\rangle$ or $|1\rangle$ is the same. 

**Measurement** <br>
When doing a measurement, we cannot directly find out the state of the qubit - we cannot measure the amplitudes $\alpha$ and $\beta$ of the states, so we need to repeat the measurement multiple times to get a histogram of the results. 

<img src="resources/qti/01_measurement.png" width="400"/>

In this case, a qubit in _superposition_ is measured twice - the first time produces a random qubit, where the second measurement produces the same result. Thus, `00` is common and `01` and `10` do not occur.

<!--
4.1.3 Polar Form
4.1.4 Bloch Sphere
-->

## Single Qubit Gates
A quantum gate is an operator that acts on the state of one (or more) qubits. This operators are represented by unitary matrices.

### Pauli Gates
The Pauli gates are the most common gates. 

**Pauli-X** <br>
The Pauli-X gate exchanges the amplitudes of the qubit. 

$`X|\psi\rangle = X(|\alpha|0\rangle + \beta|1\rangle) = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \begin{pmatrix} \alpha \\ \beta \end{pmatrix} = \begin{pmatrix} \beta \\ \alpha \end{pmatrix} = \beta|0\rangle + \alpha|1\rangle`$

It is also caled a `bit-flip` gate - when applying to the base states $|0\rangle$ and $|1\rangle$, the result is the opposite state.

**Pauli-Z** <br>
The Pauli-Z gate changes the sign of the $\beta$ amplitude.

$`Z|\psi\rangle = Z(|\alpha|0\rangle + \beta|1\rangle) = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix} \begin{pmatrix} \alpha \\ \beta \end{pmatrix} = \begin{pmatrix} \alpha \\ -\beta \end{pmatrix} = \alpha|0\rangle - \beta|1\rangle`$

It is also called a `phase-flip` gate - when applying to the base state $Z|1\rangle$, the result is $-|1\rangle$.

**Pauli-Y** <br>
The Pauli-Y gate is a bit more complicated gate, it has an imaginary factor. 

$`Y|\psi\rangle = Y(|\alpha|0\rangle + \beta|1\rangle) = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix} \begin{pmatrix} \alpha \\ \beta \end{pmatrix} = i \begin{pmatrix} -\beta \\ \alpha \end{pmatrix} = -i\beta|0\rangle + i\alpha|1\rangle`$

**Information** <br>
When two of the same gates are applied, the result is the identity matrix.

$`X \cdot X = Y \cdot Y = Z \cdot Z = I_2 = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}`$

### Hadamard Gate
The Hadamard gate is a very common gate, it is used to create superposition - it applies to the base states like this. 

$`H|0\rangle = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix} \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ 1 \end{pmatrix} = \frac{1}{\sqrt{2}} (|0\rangle + |1\rangle) = |+\rangle`$ <br>

$`H|1\rangle = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix} \begin{pmatrix} 0 \\ 1 \end{pmatrix} = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ -1 \end{pmatrix} = \frac{1}{\sqrt{2}} (|0\rangle - |1\rangle) = |-\rangle`$

These are superposition states, the probability of measuring both states is equal. Hadamard is also it's own inverse, so $`H \cdot H = 1`$.

# Quantum Registers (and Entanglement)
<!-- 2 Qubit Register 5.1.1 -->

## CNOT (controlled Pauli-X)
The CNOT, `CX`-gate or controlledd Pauli-X is a 2-qubit gate with a control qubit, which remains unchanged and the qubit it operates on. 

- If the control-qubit is `0`, the second qubit is not changed. 
- If the control-qubit is `1`, the second qubit is flipped.

Let $q_1$ be the control-gate and $q_0$ the controlled gate, then CNOT has the following form. 

$`CNOT = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}`$ 

In `Qiskit`, the CNOT gate is defined as 

```python
qc.cx(q[0], q[1])
```

and it looks like this.

<img src="resources/qti/02_cnot.png" width="100"/>

Applied on the base states the qubit corresponds to a classical `XOR`-gate.

| input | output |
| ----- | ------ |
| 00    | 00     |
| 01    | 01     |
| 10    | 11     |
| 11    | 10     |

## Entanglement
Two or more qubits are called _entangled_, if their state cannot be described as the tensor product of some individual qubits.

## SWAP-Gate
The SWAP-Gate swaps the two qubits - as simple as that. 

| input | output |
| ----- | ------ |
| 00    | 00     |
| 01    | 10     |
| 10    | 01     |
| 11    | 11     |

The SWAP-Gate is defined as

$`SWAP = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}`$

and in `Qiskit` code it looks like this

```python
qc.swap(q[0], q[1])
```

and the visual representation is as follows.

<img src="resources/qti/03_swap.png" width="100"/>

## Toffoli-Gate
The Toffoli-Gate is a 3-qubit gate, with two control qubits and one target qubit. The target qubit is flipped, if both control qubits are `1`.

| input | output |
| ----- | ------ |
| 000   | 000    |
| 001   | 001    |
| 010   | 010    |
| 011   | 011    |
| 100   | 100    |
| 101   | 101    |
| **110**   | **111**    |
| **111**   | **110**    |

The Toffoli-Gate is defined as

$`CNOT = \begin{pmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \end{pmatrix}`$

and in `Qiskit` code it looks like this

```python
qc.ccx(q[0], q[1], q[2])
```

and the visual representation is as follows.

<img src="resources/qti/04_toffoli.png" width="100"/>

## Multiple Hadamard Gates
Note that hadamard operates on each qubit seperately, so we do not get entanglement from it.

$H^{\otimes 2} =
	{1\over\sqrt{2}}\begin{pmatrix}1&1\\1&-1\end{pmatrix} \otimes 
	{1\over\sqrt{2}}\begin{pmatrix}1&1\\1&-1\end{pmatrix} =
	{{1}\over{2}}\begin{pmatrix}
		1&1&1&1\\1&-1&1&-1\\
		1&1&-1&-1\\1&-1&-1&1
	\end{pmatrix}$

The visual representation is as follows.

<img src="resources/qti/05_hadamard.png" width="100"/>

When applying a Hadamard on a base vector $|u\rangle$, we get this

$H\ket{u}={1\over\sqrt{2^1}}(\ket{0}+(-1)^u\ket{1})$

where $u$ is in $\{0,1\}$ using summation, we can write this as

$H\ket{u}={1\over\sqrt{2}}\sum_{\nu\in \{0,1\} }(-1)^{\nu\cdot u}\ket{\nu}$

where $\nu\cdot u$ is the dot product of the two vectors.

# Quantum Algorithms
## Deutsch-Jozsa Algorithm
Let's assume we have a binary function with one input and one output and let's ask the question if the function is **constant** or **balanced** - balanced means that teh function produces different values as the input changes. 

- the output is always `0` (constant)
- the output is always `1` (constant)
- identity function `f(x) = x` (balanced)
- negation function `f(x) = !x` (balanced)

The classical approach would be to evaluate the function for all possible inputs and check if the output values. This is not possible with only **one function call** - two are needed. 

But with quantum computing, we can do this with only **one function call**! The problem is that the constant functions are **not** reversible - the solution is quite simple, we add a qubit. 

- one qubit is the input of the function and remains unchanged 
- the second qubit (initial `0`) is the output of the function

<img src="resources/qti/06_deutsch_jozsa.png" width="500" alt="Deutsch-Jozsa Algorithm - source unknown or possibly the lecturer"/>

