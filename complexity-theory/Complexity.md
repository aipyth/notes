---
title: Complexity
author: Ivan Zhytkevych
header-includes: |
    \usepackage{fullpage}
    \usepackage[top=2cm, bottom=4.5cm, left=2.5cm, right=2.5cm]{geometry}
    \usepackage{amsmath,amsthm,amsfonts,amssymb,amscd}
    \usepackage{hyperref}
    \usepackage{fancyhdr}
    \usepackage{mathrsfs}
    \usepackage{amsmath}
    \usepackage{dsfont}

    \usepackage{mathtools}

abstract: Complexity theory notes
---

Just say hello!
===============

# Complexity Theory

## Lection 6: Computability

### Godel Numeration

- $\mathcal{D}$ - subject area (objects, properly built functions, ...)
- $\nu : \mathcal(D) \rightarrow \mathcal{N}$ - coding into unique natural number
Actually anything can be coded using this numeration.
- there are lots of Godel numerations ($\nu(x_1, ..., x_n) = 2^{\nu(x_1)} ... p_n^{\nu(x_n)}$)
- arithmetization of arbitrary theory (transposition from theory objects to natural numbers)
- partial function $f : \mathbb{N}^{n} \not\to \mathbb{N}, n \in \mathbb{N}$, is (algorithmically) computable $\iff$ there is such Turing machine $M: M(x_1, ..., x_n) \simeq f(x_1, ..., x_n), \forall x_1, ..., x_n \in \mathbb{N}$ (Turing thesis)
- set (algorithmically) computable functions coincides to set of partially-recursive functions (Church thesis)
- Turing Machines numeration $M_0, M_1, ...$
- numeration of every (algorithmic) computable functions $\varphi_0, \varphi_1, ...$

Example of computable function:
$$f(n) = 1, \text{ if there would be colony on Moon}$$
$$f(n) = 0, \text{ if there would be no colony on Moon}$$
subjunctive algorithm that proves computability of this function is to wait the predefined set time.

---

### Theorem about uncomputable function

Uncomputable function defined everywhere - exists.

#### Proof

- $\varphi_0^1, \varphi_1^1, ...$ - all computable functions (арності 1)
- $$
f(n) = \begin{cases}
    	\varphi_n^1(n) + 1, \;\; \text{ if } \; \varphi_n^1(n) \not= \bot \\
        0,  \;\;\; \text{ if } \varphi_n^1(n) = \bot \;\; (\not\exists \varphi_n^1)
\end{cases} \;,\;\;\;
n \in \mathbb{N}
$$
- $\forall n \in \mathbb{N} f \not\simeq \varphi_n^1: f(n) \not\simeq \varphi_n^1(n)$
- diagonalization method (Kantor)

---

### Theorem about parametrization

For arbitrary countable function $f(x, y)$ exists everywhere defined countable function $k(x)$ that $f(x, y) = \varphi_{k(x)}(y)$ for arbitrary Godel Numeration $\varphi_0, \varphi_1, ...$ unary countable functions.

#### Proof
- $f(x, y)$ is countable $\Rightarrow \exists \text{ TM } M: M(x, y) \simeq f(x, y)$
- $\forall a \in \mathbb{N} \exists \text{ TM } M_a : M_a(y) \simeq f(a, y)$
- composition of Turing Machines: add argument $a$ at input (additional) tape and start TM $M$
- number of TM $M_a$ is $k(a)$ value

#### Consequence
Number of function $k(x)$ depends only on parameter $x$.

---

### $s_n^m$ Kleene theorem (s-m-n Theorem)

#### Theorem
For arbitrary countable funcions' Godel Numeration exists such a primitiv recursive function $s: \mathbb{N}^2 \rightarrow \mathbb{N}$ (арності 2), that for arbitrary Godel number $p \in \mathbb{N}$ of some partial function of two variables next Kleene equality is true: $\varphi_{s(p, x)}(y) \simeq \varphi_p(x,y)$ for every natural number $x, y \in \mathbb{N}$. 

#### $s_n^m$ Kleene theorem (s-m-n theorem, parametrization theorem)

For arbitrary natural numbers $m,n > 0$ and arbitrary godel numeration of countable functions exists such a primitiv recursive function $s_n^m : \mathbb{N}^{m+1} \rightarrow \mathbb{N}$ that for arbitrary Godel number $p \in \mathbb{N}$ of some partial function of $m + n$ arguments Kleene equality is true:
\[ \varphi_{s_n^m(p, x_1, ..., x_m)}(y_1, ..., y_n) \simeq \varphi_p(x_1, ..., x_m, y_1, ..., y_n) \]
for every natural number $x_1, ..., x_m, y_1, ..., y_n \in \mathbb{N}$.

---

### Universal function

For arbitrary set of partial functions $\mathcal{H} \subseteq \mathcal{F}_n$ of $n$ variables, $n \in \mathbb{N}_0$, function $f \in \mathcal{F}_{n+1}$ of variables $n+1$ is called universal function of set of functions $\mathcal{H}$, if the following two conditions are true:
- for arbitrary number $c \in \mathbb{N}_0$ function $f(c, \cdot)$ of variables $n$ is in set of functions $\mathcal{H}$
- for arbitrary function $h$ of set of functions $\mathcal{H}$ exists such a number $c \in \mathbb{N}_0$, that $h(x_1, ..., x_n) \simeq f(c, x_1, ..., x_n)$ for arbitrary values $x_1, ..., x_n \in \mathbb{N}_0$.

Algorithm to compute universal function for a set is called universal.

#### Theorem (about numeration)

For arbitrary number $n \in \mathbb{N}_0$ exists such universal function of set of all partial computable functions $\mathcal{H}_n \subseteq \mathcal{F}_n$ of $n$ variables.

##### Proof
- let $f(y, x_1, ..., x_n) \simeq \varphi_y(x_1, ..., x_n)$ for arbitrary numbers $y, x_1, ..., x_n \in \mathbb{N}_0$
- by value $y \in \mathbb{N}_0$ find algorithm of computing function $\varphi_y$ and compute value $\varphi_y(x_1, ..., x_n)$ using this algorithm
- $\Rightarrow$ function $f$ is computable

#### Theorem

For arbitrary number $n \in \mathbb{N}_0$ there is no such universal funtion of set of defined everywhere computable functions $\mathcal{H}_n^{tot} \subseteq \mathcal{F}_n^{tot} \subset \mathcal{F}_n$ of $n$ variables.

##### Proof
- let universal function $f$ of set of functions $\mathcal{H}_n^{tot} : f(y, x_1, ..., x_n) = \varphi_y(x_1, ..., x_n)$ for arbitrary numbers $y, x_1, ..., x_n \in \mathbb{N}_0$
- let $h(x_1, ..., x_n) = f(x_1, x_1, ..., x_n) + 1$ for arbitrary numbers $x_1, ..., x_n \in \mathbb{N}_0$
- $\Rightarrow h \in \mathcal{H}_n^{tot} \Rightarrow \exists c \in \mathbb{N}_0 f(c, x_1, ..., x_n) = h(x_1, ..., x_n)$ for arbitrary numbers $x_1, ..., x_n \in \mathbb{N}_0$
- on one side $h(c, ..., c) = f(c, ..., c)$ but $h(c, ..., c) = f(c, ..., c) + 1$ by definition of $h$ $\Rightarrow$ *contradiction*.

---

* every universal function of unary computable functions set defines numeration $f(x, y) = \varphi_x(y)$
* binary function $U$ is called **main universal function (main numeration)** if for any binary computable function $h$ exists such a defined everywhere computable unary funtion $g$ that $h(x, y) = U(g(x), y)$ for any numbers $x, y \in \mathbb{N}_0$
* $\Rightarrow$ exists main universal function of set of all unary computable functions
* $\Rightarrow U_1(x, y) = U_2(c_1(x), y)$ and $U_2(x, y) = U_1(c_2(x), y)$ (**theorem about main numerations' ismorphism**)
* operations on computable functions $\Leftrightarrow$ operations on their indexes

---

### Theorem about motionless point

For arbitrary Godel numeration $\varphi_0. \varphi_1, ...$ of unary computable functions and arbitrary unary computable defined everywhere funtion $f$ exists such natural number $n \in \mathbb{N}_0$ that $\varphi_n \simeq \varphi_{f(n)}$.

##### Proof
- consider such function $\varphi_{f(\varphi_x(x))}(y)$, $\varphi_{f(\varphi_x(x))}(y) \simeq \psi(f(\varphi_x(x)), y) \simeq g(x, y) , \forall x, y \in \mathbb{N}_0$
- from $s_n^m$ Kleene theorem follows that exists such unary defined everywhere function $h$ that $\varphi_{f(\varphi_x(x))}(y) \simeq \varphi_{h(x)}(y), \forall x, y \in \mathbb{N}_0$
- let $h \simeq \varphi_m \Rightarrow \varphi_{f(\varphi_x(x))}(y) \simeq \varphi_{\varphi_m}(y), \forall x, y \in \mathbb{N}_0$
- let $\varphi_m(m) = n$ (defined everywhere) $\Rightarrow \varphi_{f(n)}(y) \simeq \varphi_n(y), \forall y \in \mathbb{N}_0$

#### Second theorem about recursion (Kleene, 1938)
For arbitrary Godel numeration $\varphi_0. \varphi_1, ...$ unary omputable functions and arbitrary binary partial computable function $f$ exists such natural number $n \in \mathbb{N}_0$ that $\varphi_n(y) \simeq f(n ,y)$ for all numbers $y \in \mathbb{n}_0$.

##### Consequence
Let  function $h$ - $f(x, y) \simeq \varphi_{h(x)}(y)$ ($s_n^m$ theorem).
Let number $m$ be motionless point of function $h$.
From theorem about Rodger's motionless point follows second theorem about recursion ($n=m, \; \varphi_m(y) \simeq \varphi_{h(m)}(y) \simeq f(m,y)$ for all numbers $y \in \mathbb{N}_0$)

##### Consequence
Let function $f$ - for arbitrary algorithm $\mathcal{A}_x$ algorithm $\mathcal{A}_{f(x)}$ "prints description" of algorithm $\mathcal{A}_x$.
Function $f$ is computable $\Rightarrow$ by theorem about motionless point exists algorithm $\mathcal{A}$, that "prints own description".

### Computable functions

> Can UTM compute arbitrary function $\{0, 1\}^* \rightarrow \{0,1\}^*$?

#### Theorem
Exists uncountable function UC: $\{0,1\}^* \rightarrow \{0,1\}$

##### Proof
- TM numeration using set $\{0,1\}^*$, for arbitrary word $x \in \{0,1\}^*$ appropriate Turing Machine is marked $M_x$ or $M_{\lceil x \rceil}$
- define $$UC(x) = \begin{cases}
	0, \text{ if } M_x(x) = 1 \\
	1, otherwise
\end{cases} \forall x \in \{0,1\}^*
$$
- let $\exists \text{ TM } \widetilde{M}: \forall x \in \{0,1\}^* \widetilde{M}(x) = UC(x)$
$\widetilde{M}(\lfloor\widetilde{M}\rfloor) = ?$
- if $\widetilde{M}(\lfloor \widetilde{M} \rfloor) = 1$, then $UC(\lfloor \widetilde{M} \rfloor)=0$ and vice versa

### Modification of TM for recognition tasks

Recognition task $\Leftrightarrow$ defined everywhere function $\{0,1\}^* \rightarrow \{0,1\}$

#### Definition (multitape Turing Machine)
- $k \in \mathbb{N}^+$ number of tapes
- $\Gamma$ Turing Machine alphabet
- $\# \in \Gamma$
- $\{0,1\}^*$ input alphabet
- $Q$ nonempty finite set of internal states
- $q_0 \in Q$ initial state
- $q_{acc} \in Q$ final state, that accepts input word
- $q_{rej} \in Q, q_{acc} \not= q_{rej}$ final state that rejects input word
- $\delta : (Q \backslash \{q_{acc}, q_{rej}\}) \times \Gamma^k \nrightarrow Q \times \Gamma^{k-1} \times \{L, S, R\}^k$ partial function of transitions

#### Notion
$q_{acc}, q_{rej} \in Q, q_{acc} \not= q_{rej}$, other ending configurations does not exist
($\Sigma = \{0,1\}, q_{acc} \equiv q_{accept} \equiv q_y \equiv q_{yes}, q_{rej} \equiv q_{reject} \equiv q_{n} \equiv q_{no}$)

#### Definition
Final configuration of TM is called positive (negative) if it's state is final state that accepts (rejects) input word.

#### Definition
TM $M$ input word $x$
- accepts if $M(x) = 1$ ($q_{acc}$, positive configuration)
- rejects if $M(x) = 0$
- not  accepts if $M(x) = 0$ or $M(x) = \bot$
- not rejects if $M(x) = 1$ or $M(x) = \bot$

### Language recognition

#### Definition
TM $M$ resolves (decides) language $L \subseteq \{0,1\}^*$
- if $x \in L$ then $M(x) = 1$
- if $x \not\in L$ then $M(x) = 0$

#### Definition
TM $M$ recognizes language $L \subseteq \{0,1\}^*$
- if $x \in L$ then $M(x) = 1$
- if $x \not\in L$ then $M(x) = 0$ or $M(x) = \bot$

#### Definition
Languages - decidable (recursive) or semidecidable (recursively countable)

language $L(M) \;\; (L_M)$ of TM $M$ - all word it accepts.

#### Definition
Turing machines $M_1$ and $M_2$ are:
- same if there exists such permutation of inner states and/or change of directions 'left' and 'right', otherwise - in principle different
- equivalent if $M_1 = M_2$, $M_1 \simeq M_2$
- with one language if $L(M_1) = L(M_2)$

### **HALT** problem

Define by binary representation of TM $M$ and input word $x \in \{0,1\}^*$, will TM $M$ stop on input word $x$. (decide language $L_{HALT}$)

#### Theorem
**HALT** task is unsolvable.

##### Proof
- let existance of $M_{HALT}$
- $M_{diag}(x) = M_{HALT}(x, x)$
- $$M^{co}(x) = \begin{cases}
\text{cycle}, M_{diag}(x) = 1 \\
\text{stop}, M_{diag}(x) = 0
\end{cases}$$
- $M^{co}(\lfloor M^{co} \rfloor)$ ?

### $HALT_\varepsilon$ problem

Define by binary representation of Turing Machine whether TM $M$ will stop on empty input word (decide language $L_{HALT_\varepsilon}$).

#### Theorem

Problem $HALT_\varepsilon$ is unsolvable.

##### Proof
- for arbitrary pair of TM $\widetilde{M}$ and input word $x$ there exists TM $\widetilde{M}_x$
- if such TM exists, that solves $HALT_\varepsilon$ problem, then it solves $HALT$ problem
- **contradiction**

### Rice's theorem

Numeric set $S \subseteq \mathbb{N}$ is called **invariant**, if representation of any two equivalent TM simultaneously is in or not in set $S$.

#### Examples
- all TM, that accepts input word $11$
- all TM, that accepts at least one input word
- all TM, that never get hung up
- all TM, that stop after 15 tacts with input word $1$

---
---

# Lection 7: Computability

## Language recognition

### Definition
TM $M$ decides language $L_1 \subseteq \{0,1\}^*$
- if $x \in L_1$ then $M(x) = 1$ ($q_{acc}$)
- if $x \not\in L_1$ then $M(x) = 0$ ($q_{rej}$)
this TM is called decider for language $L_1$.

### Definition
TM $M$ recognizes $L_{1} \subseteq\{0,1\}^{*}$ 
- if $x \in L_{1}$, then $M(x)=1\left(q_{a c c}\right)$
- if $x \notin L_{1}$ then $M(x)=0\left(q_{r e j}\right)$ or $M(x)=\perp$
TM $M$ is called a recognizer of language $L_{1}$

#### Consequence
- Arbitrary decider for arbitrary language $L_1$ always stops.
- Arbitrary decider for arbitrary language $L_1$ is a recognizer for language $L_1$.

### Definition
For arbitrary TM $M$ language associated with this TM is a set of all words it accepts and is signed as $L(M)$ or $L_M$.

#### Consequence
- $L(M) = L_1 \iff M$ is a recognizer for language $L_1$.
- $L(M) = L_1$ and $M$ always stops $\iff M$ is a decider of language $L_1$.

#### Remark
For arbitrary language $L_1$ corresponds an infinite number of TM $M_1, M_2, \dots$ such that $L_1 = L(M_1) = L(M_2) = \dots$

---
## Properties of TM
### Definition
TM $M_1$ and $M_2$ are:
- **the same** if exists such permutation of internal states and/or reversion of directions `left` and `right`, otherwise -- completely different
- **equivalent** if $M_1 = M_2$ ($M_1 \simeq M_2$)
- *with the same language* if $L(M_1) = L(M_2)$

#### Consequence
For arbitrary TM $M_1$ and $M_2$:
- if $M_1$ and $M_2$ are the same then they are equivalent
- if $M_1$ and $M_2$ are equivalent then they are with the same language

All recognizers (deciders) of one language are **with the same language** (equivaluent).

## Deciders and recursive enumerable languages
### Definition
Language (set) is called decidable (by Turing) (recursive, countable) if exists a deciders for it (otherwise undecidable).

Language (set) is  called recursive enumerable (by Turing) (enumerable, semi-decidable) if exists a recognizer for it.

Language (set) is called corecursive enumerable (by Turing) if it's complement is a enumerable language (set).


Language is decidable $\iff$ it's characteristic function is countable.
Language is recursively enumerable $\iff$ it's semi-characteristic function is countable $$ \mathbb{I}_{L_1}(x0 = \begin{cases}
1 & x \in L_1 \\
\perp &  x\notin L_1
\end{cases}$$

--- 
## Turing Machine as rewriter
**Rewriter** - TM that writes out one by one all words from the language, probably, with repetitions.

Language is recursively enumerable $\iff$ exists rewriter for this language.

##### Proof
- let the existance of recognizer $M_R$ for language $L_1$
- a set of all words upon alphabet is enumerable - $w_1, w_2, \dots$
- rewriter - for $i = 1, 2, 3, \dots$ models work of $M_R$ with input words $w_1, w_2, \dots, w_i$ during $i$ steps, writes out all words, that $M_R$ accepts.
- let the existance of rewriter $M_E$ for language $L_1$
- recognizer - to model the work of rewriter $M_E$ and compare it's words with input word

#### Statement
- empty language is a decidable
- any finite language and it's complement are decidable languages
- exists such infinite decidable languages with it's infinite complemets (words of even length)
- complement of decidable language is a decidable language
- union and intersection of finite number of decidable languages is decidable language
- any decidable language is recusively enumerable
- union and intersection of finite number of recursively enumerable languages is recursively enumerable language

## Post's theorem
If language $L_1$ and it's complement os recursively enumerable, then language $L_1$ and it's complement is decidable.

##### Proof
- exist such recognizers $M_1$ and $M_2$ og language $L_1$ and it's complement
- decider $\widetilde{M}_1$ of language $L_1$ - models work of $M_1$ and $M_2$ with one input word in parallel
- if $M_1(s) = 1, \widetilde{M}_1(x) = 1$; if $M_2(x) = 1, \widetilde{M}_1(x) = 0$
- by finite number of steps $M_1(x) = 1$ or $M_2(x) = 1$ ($x \in L_1$ or $x \in \overline L_1$)
- decider $\widetilde{M}_2$ of language $\overline L_1$ - if $M_1(x) = 1, \widetilde{M}_2(x) = 0$ if $M_2(x)=1, \widetilde{M}_2 (x) = 1$

$L_1$ - decideable  $\iff$ $L_1$ and $\overline L_1$ are recursively enumerable

## Language $A_{TM}$
Language $A_{TM} = \left\{ \langle M,x \rangle \mid \text{ TM M accepts input word x} \right\}$ 
$\langle M,x \rangle = \lfloor (M,x) \rfloor$

### Theorem
*Language $A_{TM}$ is unsolvable, but recursively enumerable.*

##### Proof
- model on *universal* TM $U$ - TM $M$ with input word $x$
- if $M$ accepts word $x$ then $U$ accepts word $\langle M,x \rangle$
- if $M$ rejects word $x$ then $U$ rejects word $\langle M,x \rangle$
- $\implies$ recognizing language $A_{TM}$
- if $M$ hangs up on input word $x$ then $U$ hangs up on input word $\langle M,x \rangle$
- *by contradiction*
- let $\widetilde M_A$ be a decider of language $A_{TM}$
- $$\widetilde M_A(\langle M,x \rangle) = \begin{cases}
	1 & M \text{ accepts word } x \\
    0 & M \text{ rejects word } x
\end{cases}$$
- $\widetilde M_A$ always stops
- build up TM $M_D$ that on input word $\langle M \rangle$
	- models $\widetilde M_A$ on word $\langle M, \langle M \rangle \rangle$
    - returns other value then $\widetilde M_A (1 - \widetilde M_A (\langle M, \langle M \rangle \rangle))$
- $$M_D (\langle M \rangle) = \begin{cases}
1 & M \text{ rejects word } \langle M \rangle \\
0 & M \text{ accepts word } \langle M \rangle
\end{cases}$$
- $$M_D (\langle M_D \rangle) = \begin{cases}
1 & M \text{ rejects word } \langle M_D \rangle \\
0 & M \text{ accepts word } \langle M_D \rangle
\end{cases}$$

## Language $E_{TM}$
Language $E_{TM} = \{ \langle M \rangle \mid M - \text{ TM and } L(M) = \varnothing \}$ 

### Theorem
*Language $E_{TM}$ is undecidable but is corecursive enumerable.*

##### Proof
- let the decider $\widetilde M_E$ of language $E_{TM}$
- using $widetilde M_E$ build up a decider $\widetilde M_A$ for language $A_{TM}$ that on input word $\langle M,x \rangle$:
	- build up a new TM $M_w$ that for arbitrary input word $$w - M_w(x) = \begin{cases}
    0 & x \not= w \\
    M(x) & x = w
    \end{cases}$$
	- models word of decider $\widetilde M_E$ with $\langle M_w \rangle$
    - $\widetilde M_A (\langle M,x \rangle) = 1 - \widetilde M_E (\langle M_w \rangle )$
- contradiction

## Language $EQ_{TM}$
Language $EQ_{TM} = \{ \langle M_1, M_2 \rangle \mid M_1, M_2 - \text{ TM and } L(M_1) = L(M_2) \}$

### Theorem
*Language $EQ_{TM}$ is unsolvable and is corecursively enumerable.*

##### Proof
- let decider $\widetilde M_{EQ}$ of languge $EQ_{TM}$ exists
- using $\widetilde M_{EQ}$ build up a decider $\widetilde M_E$ of language $E_{TM}$ that on input word $\langle M_1 \rangle$:
	- build new TM $M_2$ that for arbitrary input word $w - M_2(x) = 0$
    - models work of decider $\widetilde M_{EQ}$ with $\langle M_1, M_2 \rangle$
    - $\widetilde M_E(\langle M_1 \rangle) = \widetilde M_{EQ} (\langle M_1, M_2 \rangle)$
- contradiction

## $HALT$ problem
With binary representation of TM $M$ and input word $x \in \{ 0,1 \}^*$ decide whether TM $M$ stops on input word $x$.
Language $\text{HALT}_{TM} = \{ \langle M,x \rangle \mid M - \text{ TM and } M(x) \not= \bot \}$

### Theorem
*HALT problem is unsolvable.*

##### Proof
- let the decider $M_{HALT}, M_{diag} (x) = M_{HALT}(x, x)$ exists
- $$M_{co}(x) = \begin{cases}
	\bot & M_{diag}(x) = 1 \\
    1 & M_{diag}(x) = 0
\end{cases}$$
- $$M_{co} (\langle M \rangle) = \begin{cases}
	\bot & M(\langle M \rangle) \not= \bot \\
    1 & M(\langle M \rangle) = \bot
\end{cases}$$

## Problem $HALT_{\varepsilon}$

Decide by binary representation of TM $M$ whether it will stop on empty input word. Language $HALT_{\varepsilon} = \{ \langle M \rangle \mid M - \text{ TM and } M(\varepsilon) \not= \bot \}$

### Theorem
*Problem $HALT_{\varepsilon}$ is unsolvable.*

##### Proof
- for arbitrary pair of TM $\tilde M$ and input word $x$ exists such TM $\tilde M_x: \tilde M_x (\varepsilon) = \tilde M(x)$.
- if exists TM that solves HALT problem, then it solves problem HALT.
- contradiction

## Language $INF_{TM}$
Language $INF_{TM} = \{ \langle M \rangle \mid M - \text{ TM and } |L(M)| = \infty \}$

### Theorem
*Language $INF_{TM}$ is unsolvable, is not recursively enumerable and is not corecursively enumerable.*

## Unsolvability
To prove the unsolvability of a language :
- strict proof (diagnalization method)
- use of other unsolvable language
- Rice's theorem

## Rice's theorem
### Definition
Property of formal languages upon alphabet $\Sigma$ defines by set of languages upon alphabet $\Sigma$. Language $L_1 \in \Sigma^*$ **has a property $\mathbb{P}$**, if $L_1 \in \mathbb{P}$. For arbitrary property $\mathbb{P}$ **language of recognition of property $\mathbb{P}$** is called a language, that consists of representations of TMs of which languages belongs to the property $\mathbb{P}$ and this language is signed as $L_{\mathbb{P}}$, $L_{\mathbb{P}} = \{ \langle M \rangle \mid L(M) \in \mathbb{P} \}$.

### Definition
Property of formal languages upon an alphabet $\Sigma$ is called a **trivial one**, if all recursively enumerable languages upon an alphabet $\Sigma$ belongs to this property or all recursively enumerable languages upon an alphabet $\Sigma$ simultaneously do not belong to this property. Otherwise, this property of formal languages is called **non-trivial**.

For arbitrary trivial property of formal languages upon an alphabet $\Sigma$ it's language of recognition this property is solvable.

### Rice's Theorem
**If property of languages $\mathbb{P}$ is non-trivial, then the language of recognition this property is unsolvable.**
$$L_{\mathbb{P}} = \{ \langle M \rangle \mid L(M) \in \mathbb{P} \}$$

#### Remarks
- Rice's theorem notes about properties of languages, but not TM's ones
- it is required for property to be non-trivial
---
---
# Rado functions
## Busy beaver
- Tibor Rado, 1962
- TM model - $(1, \{0,1\}, \{1\}, 0, Q, q_H, q_0, \delta)$, where $\delta : (Q \backslash \{q_H\}) \times \{0,1\} \rightarrow Q \times \{0,1\} \times \{L,R\}$
- $\mathcal{K}_{BB}$ - all TM that stop on empty input word (Rado class)
- $\mathcal{K}_{BB}(n)$ - all TM that stop on empty input word and have $n$ nonterminal states
- $s(M)$ - number of steps that TM $M$ does before it stops on empty input word
- $\sigma(M)$ - number of nonempty cells that will be on tape after TM $M$ stops on empty input word

#### Definition
**Rado functions** are functions $S, \Sigma: \mathbb{N} \rightarrow \mathbb{N}$, that for arbitrary natural number $n \in \mathbb{N}$ accept values $S(n) = \underset{M\in \mathcal{K}_{BB}(n)}{\max} s(M)$ and $\Sigma(n) = \underset{M\in\mathcal{K}_{BB}(n)}{\max} \sigma(M)$

##### Corollary
For arbitrary natural number $n\in\mathbb{N}$ the following unequality is true:
$$\Sigma(n) \leq S(n)$$

##### Proposition
For arbitrary natural number $n\in\mathbb{N}$ the cardinality of Rado class $\mathcal{K}_{BB}(n)$ Turing machines is bounded above by value $(4(n+1))^{2n}$.

### Theorem
For arbitrary countable function $f: \mathbb{N} \rightarrow \mathbb{N}$ exists such natural number $n_f\in\mathbb{N}$ that $\Sigma(n) > f(n)$ for all natural numbers $n \in \mathbb{N}, n > n_f$.

#### Corollary 
- $\Sigma$ Rado function is uncountable
- $S$ Rado function is uncountable

#### Nowadays results
![original image](https://cdn.mathpix.com/snip/images/h5F3XSYn_B6TB_s__5TYm8ktSxaXCelMJH6Y4aM6Bmg.original.fullsize.png)

- for arbitrary countable and arithmetically correct theory exists such natural number $k \in \mathbb{N}$, that for arbitrary $n \geq k$ none of the statements like $S(n) = m$ where $m \in \mathbb{N}$ cannot be proved within the theory.
- within Zermelo–Fraenkel set theory cannot be coumputed the value $S(748)$
- built TM from Rado class $\mathcal{K}_{BB}(1919)$, that stops, when Zermelo-Fraenkel set theory with choice axiom is contradictional.
- built TM from Rado class $\mathcal{K}_{BB}(744)$, that stops, if Riemann hypothesis is false

### Conclusions
- small by construction TM may generate massive calculations
- there is a certain limit of computational functions, and quite rapid by growth functions uncomputable

### Useful resources
- Поточнi рекорди та iсторiя машин Тюрiнга класу Радо
https://webusers.imj-prg.fr/~pascal.michel/
http://turbotm.de/~heiner/BB/
- Computerphile “Busy Beaver” вiдео (англ. мова), prof. Brailsford
https://www.youtube.com/watch?v=CE8UhcyJS0I
- Фiзична реалiзацiя (3, 2) Busy Beaver
https://www.youtube.com/watch?v=28pnk2JIBSE
- Фiзична реалiзацiя (4, 2) Busy Beaver
https://www.youtube.com/watch?v=2PjU6DJyBpw
- Реалiзацiя (4, 2) Busy Beaver в Minecraft
https://www.youtube.com/watch?v=IefoYnf6xKI

---
---

# Complexity Class

## General properties of complexity class

"Good" complexity class must:
- have some features and characterize important practical problems
- be unchangable within reasonable changes of computance model
	- $k$ TM tapes  at $\mathcal{O}(t(n)) \rightarrow 1$ tape  at $\mathcal{O}(t^2(n))$
    - RAM machine at $\mathcal{O}(t(n)) \rightarrow 3$ tapes at $\mathcal{O}(t^6(n))$
- does not depent on chosen problem encoding schema
- be closed class on the use of language operations, algorithms and subalgorithms composition

## Complexity class concept

##### Definition 
Complexity class is arbitrary languages set.

- languages upon $\{0,1\}$
- for instance, set of all languages upon $\{0,1\}$ that contain word $010$
- not all languages sets are useful for classification creation (resouces restriction, closed on operations)

##### Definition 
Complexity class is languages set that can be recognized within some resources restrictions, that arise while using.

## Operations on complexity classes

Complexity class - set.
$\implies$ all set operations are appliable: union, intersection, difference, complement, inclusion and others...
Complexity class - set of sets of ordered sets of alphabet symbols, symbols 0 and 1.
$\implies$ set-theoretic operations and relations can be applied at any level of abstraction.

##### Definition

let $C_1$ and $C_2$ complexity classes.

**Complex intersection** of complexity classes is binary operation with complexity class result $\{ L_1 \cap L_2 \mid L_1 \in C_1, L_2 \in C_2 \}$ and signed as $C_1 \land C_2$.

**Complex union** oc complexity classes $C_1$ and $C_2$ is bianry operation with complexity class result $\{ L_1 \cup L_2 \mid L_1 \in C_1, L_2 \in C_2 \}$ and signed as $C_1 \lor C_2$.

##### Definition
**Complex complement** $coC_1$ of arbitrary complexity class $C_1$ is unary operation with result of complexity class $\{ L_1 \subseteq \{0,1\}^* \mid \overline L_1 \in C_1 \}$.

##### Example
Let language $L_0 \subset \{0,1\}^*$ consist of all words that start with $0$, and language $L_1 \subset \{0,1\}^*$ consist of all words that start with $1$.
Let's define complexity classes:

$C_0 = \{ L_2 \subset \{ 0,1\}^* \mid L_2$ has only words that start with 0 or empty word, but $L_2 \not= \varnothing \text{ and } L_2 \not= \{\varepsilon\} \}$

$C_1 = \{ L_2 \subset \{ 0,1\}^* \mid L_2$ has only words that start with 1 or empty word, but $L_2 \not= \varnothing \text{ and } L_2 \not= \{\varepsilon\} \}$

$C_2 = \{ \varnothing, \{\varepsilon\} \} \cup \{ L_2 \subset \{ 0,1\}^* \mid L_2$ is required to have at least one word that starts with 0 and at least one word that starts with 1 $\}$

$C_3 = \{ \varnothing, \{0,1\}^* \}$

\[ C_0 \cup C_1 \cup C_2 = 2^{\{0,1\}^*} \]
\[ C_0 \cap C_1 = C_1 \cap C_2 = C_0 \cap C_2 = \varnothing \]
\[ C_0 \land C_1 = \{ \varnothing, \{\varepsilon\} \} \]
\[ C_0 \land C_0 = C_0 \land C_2 = C_0 \cup \{ \varnothing, \{ \varepsilon \} \} \]
\[ C_1 \land C_1 = C_1 \land C_2 = C_1 \cup \{ \varnothing, \{ \varepsilon \} \} \]
\[ C_0 \cup C_1 = 2^{\{0,1\}^*} \backslash C_2 \]
\[ C_0 \cup C_2 = 2^{\{0,1\}^*}  \backslash C_1 \]
\[ C_1 \cup C_2 = 2^{\{0,1\}^*} \backslash C_0 \]
\[ C_0 \lor C_1 = C_2 \backslash \{\varnothing,\{\varepsilon\}\} \]
\[ C_0 \lor C_2 = (C_0 \cup C_2) \backslash \{\varnothing, \{\varepsilon \}\} \]
\[ C_1 \lor C_2 = (C_1 \cup C_2) \backslash \{ \varnothing, \{\varepsilon\}\} \]

\[ coC_0 = (C_0 \backslash \{ L_0 \}) \lor \{ L_1 \} \]
\[ coC_1 = (C_1 \backslash \{ L_1 \}) \lor \{ L_0 \} \]
\[ coC_2 = (C_0 \backslash \{ L_0 \}) \lor \{ L_1 \} \]
$coC_{2}=2^{\{0,1\}^{*}} \backslash\left(\left(\left\{L_{0}\right\} \vee\left(C_{1} \cup\{\varnothing\}\right)\right) \triangle\left(\left\{L_{1}\right\} \vee\left(C_{0} \cup\{\varnothing\}\right)\right)\right) ;$
$\overline{C_{3}}=2\{0,1\}^{*} \backslash\left\{\varnothing,\{0,1\}^{*}\right\} ;$
$\operatorname{coC}_{3}=C_{3} ;$
for arbitrary complexity class $C_{4} \in 2^{\{0,1\}^{*}}$
$C_{3} \wedge C_{4}=C_{4} \cup\{\varnothing\} ;$
for arbitrary complexity class $C_{4} \in 2\{0,1\}^{*}$
$C_{3} \vee C_{4}=C_{4} \cup\left\{\{0,1\}^{*}\right\} .$

## Complexity class ALL
##### Definition
Complexity class *ALL* os a set of all languages upon $\{0,1\}$.

##### Corollary
- *ALL* - set of all functions $f: \{0,1\}^* \rightarrow \{0,1\}$
- *ALL* - set of all recognition tasks

## Classes *ALL, RE, R* and *NRNC*
##### Definition
**Complexity class RE** (recursively enumerable) is a set of all recursively enumerable by Turing languages upon $\{0,1\}$.

##### Definition
**Complexity class R** (recursive) is a set of all decidable by Turing languages upon $\{0,1\}$.

##### Definition
**Complexity class NRNC** is defined as $NRNC = ALL \backslash (RE \cup coRE)$.

##### Corollary
$R \subseteq R E \subseteq A L L$ і $R \subseteq \operatorname{coRE} \subseteq A L L$
$R=R E \cap \operatorname{coRE}$ (Post's theorem corollary)
$R \neq R E, R \neq \operatorname{coRE}, R E \neq \operatorname{coRE} ;$
$N R N C \neq \varnothing ;$
$R \subset R E \subset A L L, R \subseteq \operatorname{coRE} \subset A L L .$

## Complexity classes and problems diagram
![original image](https://cdn.mathpix.com/snip/images/M8mVjU0ZQj5qODalm7KM4YqCG7Qv5eDaIZgFK5hbdHU.original.fullsize.png)

## Properties of complexity classes *ALL, RE, R, NRNC*

Complexity class *R* is closed with respect to join operations,
intersection and concatenation of languages, as well as the operation of Klenee closure and language additions.
The *RE* complexity class is closed with respect to join operations,
intersection and concatenation of languages, as well as the operation of Klenee closure, but not closed to the language complement operation.
The *NRNC* complexity class is closed with respect to the complement operation
language, but is not closed to join and intersection operations
as.
The *ALL* complexity class is closed with respect to any operation on
languages.

\[ \varnothing \subset INF_{TM} \subset \{0,1\}^* \]

## Reducibility

#### Definition
Reducibility is some procedure (or algorithm) of translating one problem to another.
Problem P1 reduces to problem P2:
- use available solution of P2
- prove complexity of problem P1 solution


#### Example
- P1 : $ax^2 + bx + c = 0$
- P2 : $x^2 + bx + 1 = 0$
- P3 : $x^2 -2x+1=0$
- P3 reduces to P2
- P2 reduces to P1

#### Example
- PRIME — for given natural number define whether it is prime
- COMPOSITE — for given natural number define whether it has non-trivial dividers (not 1 and itself)
- FACTOR — for given natural numbers $m$ and $k$ define whether number $m$ has non-trivial divider that is $\not\geq k$
- COMPOSITE -> PRIME
- PRIME -> COMPOSITE
- PRIME & COMPOSITE -> FACTOR
- FACTOR not -> PRIME | COMPOSITE

#### Definition
Reduction of languages is arbitrary binary relation on set $\{0,1\}^*$ that is reflexive and transitional. Laguage $L_1 \subseteq \{0,1\}$ reduces to language $L_2 \subseteq \{0,1\}$ if ordered pair $(L_1,L_2)$ belong to the binary relation that defines reduction. For language reduction signing $\leq$ is used with probable use of under- and upper- indexes for clarification of specifical reduction.

##### Consequence
Computable problem P1 reduces to computable problem P2 if such encoding schemas $e_1, e_2$ of P1 and P2 exists, that language $L[P1, e_1]$ reduces to $L[P2, e_2]$.

##### Remark
Is applicable for arbitrary sets.
