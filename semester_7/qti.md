# Quantum Technologies and Information
Prof. Dr. Ulrich Margull

## Contents
- [Quantum Technologies and Information](#quantum-technologies-and-information)
  - [Contents](#contents)
- [Classical Bits and Gates](#classical-bits-and-gates)

# Classical Bits and Gates
One bit is represented by an vector $0 = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$ or $1 = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$. The boolean `NOT` gate is represented by the matrix $\begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$.

**AND-Gate** <br>
The AND-Gate has `2` input bits, therefore two bits are represented by a 4-dimensional vector. 

$00 = \begin{pmatrix} 1 \\ 0 \\ 0 \\ 0 \end{pmatrix}$, $01 = \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix}$, $10 = \begin{pmatrix} 0 \\ 0 \\ 1 \\ 0 \end{pmatrix}$, $11 = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 1 \end{pmatrix}$

<details><summary>math</summary>

The related matrix has has $2 \times 4$ dimensions.

$\begin{pmatrix} q_1 \\ q_2 \end{pmatrix} = \begin{pmatrix} x_{11} & x_{12} & x_{13} & x_{14} \\ x_{21} & x_{22} & x_{23} & x_{24} \end{pmatrix} \begin{pmatrix} a_1 \\ a_2 \\ b_1 \\ b_2 \end{pmatrix}$ 

</details> <br>

And the `boolean-AND` therefore is represented by following matrix

$AND = \begin{pmatrix} 1 & 1 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$

**NAND-Gate** <br>
The NAND-Gate is the negation of the AND-Gate. Therefore the matrix is the negation of the AND-Gate matrix.

$NAND = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \cdot \begin{pmatrix} 1 & 1 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix} = \begin{pmatrix} 0 & 0 & 0 & 1 \\ 1 & 1 & 1 & 0 \end{pmatrix}$

**Parralel Gates** <br>
The most simple case are two `NOT` gates in parralel. 

<img src="resources/qti/00_X_AND.png" width="200"/>

Now we have two inputs and two outputs, both are 4-dimensional vectors. 

$a= \begin{pmatrix} a_0 \\ a_1 \end{pmatrix}$, $b= \begin{pmatrix} b_0 \\ b_1 \end{pmatrix}$ and the input then is $a \otimes b = \begin{pmatrix} a_0 b_0 \\ a_0 b_1 \\ a_1 b_0 \\ a_1 b_1 \end{pmatrix}$

<details><summary>example</summary>

$|01\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix} \otimes \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 \cdot \begin{pmatrix} 0 \\ 1 \end{pmatrix} \\ 0 \cdot \begin{pmatrix} 0 \\ 1 \end{pmatrix} \end{pmatrix} = \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix}$.

</details> <br>

The same applies to the gates - the combination of both parallel gates is the tensor product of the infdividual gates.

$X = NOT \otimes NOT = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \otimes \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} = \begin{pmatrix} 0 \cdot \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} & 1 \cdot \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \\ 1 \cdot \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} & 0 \cdot \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \end{pmatrix} = \begin{pmatrix} 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{pmatrix}$

<details><summary>example</summary>

For example, the input $|01\rangle$ yields the output $|10\rangle$.

$\begin{pmatrix} 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{pmatrix} |01\rangle = X \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 1 \\ 0 \end{pmatrix} = |10\rangle$

</details> <br>

The concatenation of the two steps $x$ and $AND$ is the normal product of the matrices (in reverse order).

$|e\rangle = AND \cdot X = \begin{pmatrix} 1 & 1 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix} \cdot X = \begin{pmatrix} 0 & 1 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{pmatrix}|ab\rangle$

<details><summary>example</summary>

For example, the input $|01\rangle$ yields $|0\rangle$ as output.

$\begin{pmatrix} 0 & 1 & 1 & 1 \\ 1 & 0 & 0 & 0 \end{pmatrix} |01\rangle = \begin{pmatrix} 0 & 1 & 1 & 1 \\ 1 & 0 & 0 & 0 \end{pmatrix} \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 \\ 0 \end{pmatrix} = |0\rangle$

</details> <br>
