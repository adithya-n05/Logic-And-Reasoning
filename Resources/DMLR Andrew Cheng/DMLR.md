### Discrete Mathematics, Logic & Reasoning



#### Propositional Logic

**Syntax**

Order of boolean connectives: 

$\neg, \bigwedge, \bigvee, \rightarrow, \leftrightarrow$​ . **from the strongest to the weakest**



**Repeated $\rightarrow$** :

$p \rightarrow q \rightarrow r \leftrightarrow (p \rightarrow q) \rightarrow r$ 



**Principal connective**: The "root" connective in a formation tree

- $p \bigwedge r \rightarrow r$ has principal connective $\rightarrow$ 
- $\neg(p \rightarrow \neg q)$ has principal connective $\neg$ 

Every non-atomic formula has a principle connective



**Technical terms**: 

- **Literal**: an atomic formula or a negation of an atomic formula
- **Clause**: A formula made of $\bigvee$ and literals
  - $(p \bigvee q) \bigwedge r$ is not a clause since it includes stuff other than $\bigvee$

- **Conjunction**: $\bigwedge$ 
- **Disjunction**: $\bigvee$



**Scheffer stroke**: (Basically NAND)

Written as $\uparrow$ 

- $T \uparrow T = F$
- $T \uparrow F = T$
- $F \uparrow T = T$
- $F \uparrow F = T$

All other Boolean connectives can be defined in terms of $\uparrow$ 



**Functional completeness**:

Let $C$ be a set of Boolean connectives. $C$ is functionally complete if any connective of any arity can be defined just in terms of connectives in $C$ 

- $\uparrow$ is functionally complete
- $\{ \neg, \bigwedge \}$​​ is also functionally complete



**Translation from English to Logic**:

- Unless: 
  - Could mean "OR"
  - It could also be "XOR"
    - I will go out unless it rains $\rightarrow 'I \ will \ go \ out' \leftrightarrow \neg(it \ will \ rain)$
- Only if, Is necessary for, Is sufficient for: $\rightarrow$



**Definition of Valid Arguments**:

Given formulas $\phi_1 \cdots ,\phi_n, x$​ 

An argument $\phi_1, \cdots ,\phi_n$ therefore $x$  is valid $\leftrightarrow$ 

$\bigwedge_{i=1}^n \phi_i \rightarrow x$ 

**Notation**: $\phi_1, \cdots, \phi_n \models x$​ 



**Example of (maybe) valid arguments**:

- **modus ponens**: $x,  \ x \rightarrow y$​  therefore $y$ is valid 
- **modus tollens**: $x \rightarrow y, \ \neg y$  therefore $\neg x$ is valid 
- $x \rightarrow y, \ y$ therefore $x$ is **not** valid in general



A propositional formula is **valid (logically)** if it is true in **every** situation

A propositional formula is **satisfiable** if it is true **at least one** situation

- **Contradiction**: A propositional formula that is not **satisfiable**

Two propositional formula are **logically equivalent** if they are true in **exactly the same** situations 

- Sometimes $\equiv$ is used to denote this relation

**Argument validity, validity, satisfiability, and equivalence are closely related**



Let $\phi_1, \cdots, \phi_n \models x$ be an argument. The formula $\bigwedge_{i=1}^n \phi_i \rightarrow x$ is the arguments **corresponding implication formula**

- Argument is valid $\leftrightarrow$ corresponding implication formula is valid



**Proving the validity of arguments**: 

- Truth table: $O(2^N)$ tho 
- Direct argument:
  - Justify stuff by the definition of operators ($\bigwedge, \rightarrow$.etc) 
  - Ex: Prove that $x \bigwedge (x \rightarrow y) \rightarrow y$ is valid 
    - if LHS is false then by def of $\rightarrow$ the formula is valid
    - if LHS is true then $x$ must be true and $x \rightarrow y$  must be true $\rightarrow$ y must also be true
    - Proved
- Equivalences: 
  - We know that "truth" is a valid formula
  - Convert the argument and reduce it to "truth" to show that it is valid using identities such as $a \bigwedge b \leftrightarrow b \bigwedge a$ 
  - **De Morgan Laws**:
    - $\neg(x \bigwedge y) \leftrightarrow \neg x \bigvee \neg y$
    - $\neg(x \bigvee y) \leftrightarrow \neg x \bigwedge \neg y$
  - Distributivity of $\bigwedge$ and $\bigvee$​​ 
    - $x \bigwedge (y \bigvee z) \leftrightarrow (x \bigwedge y) \bigvee (x \bigwedge z)$
    - $x \bigvee (y \bigwedge z) \leftrightarrow (x \bigvee y) \bigwedge (x \bigvee z)$ 
  - **Absorption**:
    - $x \bigwedge (x \bigvee y) \leftrightarrow x$
    - $x \bigvee (x \bigwedge y) \leftrightarrow x$​ 
  - Equivalences can be used to re-write a formula into a **normal form**
    - **Disjunctive Normal Form (DNF)**: A formula is in **DNF** if it is a disjunction of conjunction of literals, and it is not further simplifiable without leaving DNF form
      - A DNF is **unsatisfiable** $\leftrightarrow$​ each of its conjunction contains some literal and its negation. Checking can be done in $\mathcal{O}(N)$ 
      - Every formula has a DNF form
      - We can construct formula's DNF straight from the truth table
        - For each case it is true, represent the case using a conjunction, then disjunct all of these conjunctions
    - **Conjunctive Normal Form (CNF)**: A formula is in **CNF** if it is a conjunction of disjunction of literals and it is not further simplifiable without leaving CNF form
      - AKA **clausal normal form**
      - A CNF is **valid** $\leftrightarrow$​ each of its disjunctions contains some literals and its negation. Checking can be done in $\mathcal{O}(N)$​​ 
      - Every formula has a CNF form
      - We can construct formula's CNF also straight from the truth table
        - For each case it is false, represent the case using a disjunction that is only false giving the current values, then conjunct all of these disjunctions
    - **Rewriting a formula in normal form**:
      - Replace $x \rightarrow y$ by $\neg x \bigvee y$ 
      - Replace $x \leftrightarrow y$ by $(x \bigwedge y) \bigvee (\neg x \bigwedge \neg y)$
      - Use **De Morgan Laws** to push negations
      - Distributivity
      - **Absorption laws**
      - General simplification
      - **You might need to leave the form temporarily to further simplify it**
      - Reference all laws used. Try not to skip steps
- Natural Deduction: 
  - Establish validity of an argument by breaking it into smaller arguments and showing the validity of these intermediate parts
  - The $\vdash$​ symbol signals that we should use natural deduction
  - Each step of the proof should be a **valid argument**
  - $\bigwedge$-introduction: 
    - To introduce $x \bigwedge y$ , you have to have already introduced $x$ and $y$ 
  - $\bigwedge$-elimination: If you have $x \bigwedge y$, you can write $x$ or $y$ 
  - $\rightarrow$ -introduction: 
    - To introduce $x \rightarrow y$, you **assume** x and then prove $y$​ 
    - Boxes are used when making additional assumptions
    - You can't use anything in the box
    - We isolate the proof of $x \rightarrow y$ in a box
  - $\rightarrow$-elimination: If you have $x$ and $x \rightarrow y$ then we have $y$ 
  - $x$​​​ and $y$​​​​ are **Provably equivalent** (written as$(x \vdash \dashv y)$​​​ ): $(x \vdash y) \bigwedge (y \vdash x)$​​​​​​​ 
    - **Two formulas are provably equivalent $\leftrightarrow$ they are semantically equivalent**
  - $\bigvee$-introduction: 
    - To introduce $x \bigvee y$ , prove $x$ or prove $y$
  - $\bigvee$​-elimination:  If you can prove $z$ from $x$ and $z$ from $y$, then we have $z$ from $x \bigvee y$ 
    - Use side-by-side assumption boxes
    - Both boxes must end with the same formula $z$ 
  - $\neg$-introduction: To prove $\neg x$ u assume $x$ and prove falsity (reach a contradiction).
    - The assumption must also be in a box
  - $\neg$-elimination: From $x$ and $\neg x$ , deduce falsity 
  - $\neg\neg$​-introduction: From $x$ deduce $\neg\neg x$ 
  - $\neg\neg$-elimination: From $\neg\neg x$ deduce $x$
  - Falsity-Introduction: To prove Falsity, you prove $x$ and $\neg x$​ 
    - This is the same thing as $\neg$-elimination
  - Falsity-elimination: Falsity can lead to anything 
  - Truth-introduction: You can just insert true randomly
  - Truth-elimination: Does absolutely nothing
  - Derived rules: A rule that can be proven using primitive rules
  - Useful set of derived rules: 
    - $x \bigvee \neg x$​ is true $\forall x$ 
      - Uses this when the goal contains an element that doesn't exist in the set of premises
    - $x \leftrightarrow \neg\neg x$ 
    - Modus Tollens (MT): $(x \rightarrow y \bigwedge \neg y) \rightarrow  \neg x$​ 
    - Proof by Contradiction: To prove $x$ you can assume $\neg x$ and prove falsity
  - $\leftrightarrow$-Introduction: To prove $a \leftrightarrow b$ you prove $(a \rightarrow b) \bigwedge (b \rightarrow a)$
  - $\leftrightarrow$-Elimination: Given $a \leftrightarrow b$ , you can get $(a \rightarrow b) \bigwedge (b \rightarrow a)$
  - $\vdash x$​ means that $x$​ is called a **theorem**  (because it does not need any premises)



A proof system is **sound** if every theorem is **valid**

A proof system is **complete** if every valid formula is a **theorem** 

Natural deduction is **sound** and **complete**, this means that:

- Any provable propositional formula is valid
- Natural deduction is powerful enough to prove all valid formulas

A formula $x$ is said to be **consistent** if $\not\vdash \neg x$ 

A collection $\phi_1, \cdots, \phi_n$ of formulas is **consistent** if $\not\vdash \neg \bigwedge_{1 \leq i \leq n} \phi$ 

**A formula $x$ is consistent $\leftrightarrow$ $x$ is satisfiable** 



#### Predicate logic

Used to look inside propositional atoms such as **Aaron and Russell are friends** 

**Predicate symbol**: A symbol used to describe properties of and relationships between objects

**Arity**: Number of arguments something take

**Quantifiers**: Specifies a quantity (of an object)

- "All", "Some", "Most", "Eight out of the ten"...
- Two symbols: $\forall$, $\exist$

**Functions**: 

Something that takes an object that returns an object

- **Functions** return objects while **predicates** return true or false. Since **true** and **false** are not objects, **functions** never return boolean values
- A **function** that returns a boolean value is just a **predicate**



**Signature** of a predicate logic: A triple(set of constants, set of functions, set of predicates)

**Term**: Used to name objects

- Any constant in the signature is a term
- Any variable is a term
- The output of a function in the signature is a term if all of its inputs are terms

- **closed term** / **ground term**: A term that doesn't involve a variable

**Atomic Formula**: A predicate with arguments filled in with terms

**Literal**: An atomic formula or its negation

**Sentence**: A formula where all variables used are quantified by $\forall $ and $\exist$ 

**Binding conventions**: Same as Propositional logic, but in addition we have $\forall, \exist, \neg$ on the same level

**Domain of discourse**: A collection of objects to which a predicate logic might refer to. (Notation: $\mathbb{D}$)

An **L-Structure(Model)** is a pair $M = <\mathbb{D},\mathbb{I}>$​​ , where

- $\mathbb{D}$ = Domain of discourse
- $\mathbb{I}$​ is an **interpretation** that specifies the meaning of all constants, functions, and predicates
  - $\mathbb{I}$(constant1) = object1
  - $\mathbb{I}$(function1) = a map from $\mathbb{D}^n \rightarrow \mathbb{D}$ 
  - $\mathbb{I}$​(predicate1) $\subset$​ of $\mathbb{D}^n$​​ 
    - For ex: $\mathbb{I}$(bought) = $\{(o_1,o_2),(o_2,o_3)\}$​​​. This means that $bought(o_1,o_2) = true, bought(o_2,o_3) = true$, and all other combinations of $\mathbb{D}^n$ that is not in the set the predicate would evaluate to false

To say that a predicate $P$ with term $o$​ is true in a Model $M$, we write
$$
M \vDash P(o)
$$
And to say that it is false we write
$$
M \not\vDash P(o)
$$

**bound variable**: A variable that occurs within a quantifier ($\forall, \exist$)

**free variable**: A variable that is not bounded

**Assignment**: A function that takes a free variable and assigns a value to it

An assignment $h$ is a function that assigns each variable to an object in $dom(M)$. 
$$
h : V \rightarrow dom(M)
$$
Let $L$ be a signature, $M = < \mathbb{D}, \mathbb{I}> $, $h$ be the assignment function into $M$ , the value of $t$ in $M$ under $h$, is denoted as $v_M^h(t)$ 

- $x$ is a constant: $v_M^h(x) = x$ 
- $x$ is a variable: $v_M^h(x) = h(x)$
- $x$​​ is a function with parameters in it: $v(f(x_1, \cdots, x_n)) = f(v_M^h(x_1), \cdots, v_M^h(x_n))$​ 



**Evaluating formulas without quantifiers**:

Given assignments and $L$-structures, we can now evaluate any formula without quantifers

$M,h \models A$​ means that is $A$​ satisfied in the $L$​-Structure $M$​ and assignment $h$​. If it is not satisfied then we have $M,H \not\models A$ instead.



**Variable-equivalent variable assignments**:

Two variable assignments are $x$-equivalent if they differ at most in the assignment of the variable $x$ 

Ex: $f$ and $g$ are $x$-equivalent (written as $g =_x h$) in the following assignments

- $f(x) = 1, f(y) = 2, f(z) = 3$
- $g(x) = 0, g(y) = 2, g(z) = 3$



**Evaluating formulas with quantifiers**:

- $M,h \models \exist x \phi$​, if $M,g \models \phi$​ for **some** assignment $g$​ into $M$​ that satisfies $g =_x h$​. If not, then we have $M,h \not\models \exist x \phi$​
- $M,h \models \forall x \phi$, if $M,g \models \phi$, for **every** assignment $g$ into $M$ that satisfies $g =_x h$. If not, then we have $M,h \not\models \forall x\phi$



**Useful notation for free variables**:





**Logic to English Translation**:

In general, $\forall x (A \rightarrow B)$ translates to every $A$ is a $B$​ 

However, some $A$ is a $B$ should be translated to $\exist x(A \bigwedge B)$ as some $A$ is a $B$ means that there is a thing that is an $A$ and it is is also an $B$

- $\exist(A \rightarrow B)$ also holds when none of the object is an $A$ 



**English to Logic Translation**:

Express sub-concepts in logic first before piecing sub-logic sections together



#### Many-Sorted Logic

Basically type definitions

Each variable and constant with a sort $s$, the notation to indicate variable $x$ is of sort $s$ is $x : s$ 

Each function comes with a template $f : (s_1, \cdots, s_n) \rightarrow s$ 

- Corresponding sorts have to match when the function is called

Each relation also comes with a template

This allows us to write $\forall x : lecturer \ \exist y : PC(bought(x,y))$ instead of $\forall x (lecturer(x) \rightarrow \exist y (PC(y) \bigwedge bought(x,y)))$ 

Each object is allocated to exactly one sort 



**Valid argument**:

Let $L$ be a signature and $A_1, \cdots, A_n, B$ be $L$-formulas

If $M,h \models A_1, \cdots, M,h \models A_n$, then $M,h \models B$, we write $A_1, \cdots, A_n \models B$ 



**Valid formula**: 

A formula is valid if for every $L$-structure $M$ and assignment $h$ we have $M,h \models A$ 



**Satisfiable formula**:

A formula is satisfiable if for some $L$-structure $M$ and assignment $h$ we have $M,h \models A$ 



**Equivalent formulas**:

Formulas $A,B$ are logically equivalent if for every $L$-structure $M$ and assignment $h$ we have $M,h \models A$ if and only if $M,h \models B$ 



**Ways to validate arguments**:



**Direct reasoning**:





**Equivalences**:

In addition to propositional equivalences, we have

- $\forall x \forall y A = \forall y \forall x A$ 
- $\exist x \exist y A = \exist y \exist x A$​ 
- $\neg \forall x A = \exist x \neg A$ 
- $\neg \exist x A = \forall x \neg A$ 
- $\forall x (A \bigwedge B) = \forall x A \bigwedge \forall x B$ 
- $\exist x (A\bigvee B) = \exist x A \bigvee \exist x B$​ 



**Natural Deduction**:

Keep all of the old rules from natural deduction of propositional logic

$\exist$-Introduction: 

- For a formula $A$, a variable $x$ and a term $t$, if we have $A(t/x)$​ (the formula achieved by replacing all occurrences of $x$ by $t$) , we can write $\exist x A $ 

$\exist$-Elimination:

- If we have $\exist x A$, we can assume $A(c/x)$, where $c$​ is a new constant that has never appeared before and prove a result $B$ with it (in a box). The $c$ is called a **Skolem constant** 

$\forall$-Introduction:

- Introduce a new constant $c$ in a box and prove $A(c/x)$​ 

$\forall$-Elimination:

- If we have $\forall x A$, we can have $A(t/x)$ for any $t$ 



Derived rule: $\forall \rightarrow E$​ 

Given 

- $\forall x (A(x) \rightarrow B(x))$​​ $(1)$​​ 
- $A(t/x)$​ $(2)$​ 

we can get $B(t/x)$ through the rule $\forall \rightarrow E(1,2)$



Equality Rules:

- refl (reflexitivity): $t = t$ 
- sub (substitution): We can replace $t$ by $u$ if we proved either $t = u$ or $u = t$
- symmetry: If we proved $a = b$, we have $b = a$ 



#### Reasoning About Programs



**Induction on Numbers Overall Formula**:
$$
P(0) \bigwedge \forall k \in \mathbb{N}, [P(k) \rightarrow P(K+1) ] \rightarrow \forall n \in \mathbb{N}, P(n)
$$


**Induction on Numbers (Technique)**:

$\forall m \in \mathbb{Z}$, we have:
$$
P(m) \bigwedge \forall k \geq m [P(k) \rightarrow P(k+1)] \rightarrow \forall n \geq m, P(n)
$$


**Strong Induction**:
$$
P(0) \bigwedge \forall k \in \mathbb{N}[(\forall j \in [0,k] P(j)) \rightarrow P(k+1)] \rightarrow \forall n \in \mathbb{N} P(n)
$$

- The technique form also exists for strong induction



**Structural Induction Principle over lists**:

For any type $T$,and $P \subseteq [T]$:
$$
P([]) \bigwedge \forall vs:[T], \forall v :T [P(vs) \rightarrow P(v:vs)] \rightarrow \forall xs:[T], P(xs)
$$

- In situations when this doesn't work, either:
  - Introduce auxiliary lemmas 
  - Prove a stronger result instead then apply to get the desired result



**List Lemmas**:

- $us ++ [] = us$ 
- $[] ++ us = us$
- $(u:us) ++ vs = u:(us ++ vs)$ 
- $(us ++ vs) ++ ws = us ++ (vs ++ ws)$ 



**Induction Principle on Trees**:
$$
P(empty) \bigwedge \forall t_1,t_2:Tree \ T, \forall x:T [P(t_1) \bigwedge P(t_2) \rightarrow P(Node \ t_1 \ x \ t_2)]
$$



**Induction Principle on Inductively Defined Sets**:

Consider the set of ordered lists $OL \subseteq \mathbb{N}^*$  defined by:

- $[] \in OL$ 
- $\forall i \in \mathbb{N}, (i: []) \in OL$
- $\forall i,j \in \mathbb{N}, js \in \mathbb{N}^*, [i \leq j \bigwedge j: js \in OL \rightarrow i:j:js \in OL]$ 

For property $Q \subseteq \mathbb{N}^*$, the definition of $OL$ gives the inductive principle:

- $$
  Q([]) \bigwedge \forall i \in \mathbb{N}, Q(i:[]) \bigwedge \forall i,j \in \mathbb{N}, js \in \mathbb{N}^* [i \leq j \bigwedge j: js \in OL \bigwedge Q(j:js) \rightarrow Q(i:j:js)] \rightarrow \forall ns \in OL, Q(ns)
  $$

  

**Induction Principle on Inductively Defined Relations**:

The predicate $SL \subseteq \mathbb{N} \times \mathbb{N}$ is defined by:

- $\forall k \in \mathbb{N}, SL(0,k +1)$ 
- $\forall m,n \in \mathbb{N}, SL(m,n) \rightarrow SL(m+1,n+1)$ 

For property $Q \subseteq \mathbb{N} \times \mathbb{N}$, the definition of $SL$ gives the inductive principle:

- $$
  \forall k \in \mathbb{N}, Q(0, k+1) \bigwedge \forall m,n \in \mathbb{N}, [SL(m,n) \bigwedge Q(m,n) \rightarrow Q(m+1,n+1)] \rightarrow \forall m,n \in \mathbb{N}, [SL(m,n) \rightarrow Q(m,n)]
  $$

  

**Induction Principle on Inductively Defined Functions**:

Given a function $f$ that satisfies

- $f(0) = 0$ 
- $\forall j, k \in \mathbb{Z}, [j \neq 0 \bigwedge f(j-3) = k \rightarrow f(j) = k + 1]$

For a predicate $Q \subseteq \mathbb{Z} \times \mathbb{Z}$, we have:

- $$
  Q(0,0) \bigwedge \forall j,k \in \mathbb{Z}, [j \neq 0 \bigwedge f(j-3) = k \bigwedge Q(j-3,k) \rightarrow Q(j,k+1)] \rightarrow \forall j,k \in \mathbb{Z}, [f(j) = k \rightarrow Q(j,k)]
  $$

  

**Reasoning about Imperative Programs**:

We specific preconditions and postconditions about a piece of code

Sometimes **mid-conditions** are also used, they are basically postconditions up to the point in the code

We use **Hoare triples**, which takes the form
$$
\{P\} \text{ code } \{Q\}
$$
To prove this, we need to prove
$$
\{P\} \bigwedge code \rightarrow \{Q\}
$$
Notation:

- $x$ is used to reference the **most recent** value of $x$ (the value after the code has been executed)
- $x_{old}$ refers to the value of $x$ **before** the line of code is executed
- To simplify the presentation, we only use the $old$ notation when the variable is actually modified by the code
- The notation $P[x \mapsto x_{old}]$ means replacing all occurrences of $x$ in $P$ with $x_{old}$ 
- On the other hand, $x_{pre}$ refers to the **initial** value of an input to a method



**Array Notations**:

$NrOccurs(a[..),v)$ returns the amount of times the value $v$ occured in the array (subarray) $a$

$a[..) \sim b[..)$ means that the contents of $a$ is a **permutation** of the contents in $b$ 

$a[..) \approx b[..)$ means that $\forall i, a[i]= b[i]$ (referred to as **deep equality**)

$Sorted(a[..))$ means that the array (subarray) $a$ is sorted

$Swapped(a[..),b[..).i.j)$ means the arrays (subarrays) $a,b$ are exactly the same except for the elements at indices $i,j$, which are swapped



**Conditional Branches**:

Given a conditional branch

```c++
//Precondition: P
if(cond){
    code 1;
} else{
    code 2;
}
//Postcondition: Q
```

We need to prove:
$$
\{P \bigwedge cond\} \ code1 \ \{Q\} 
$$
and 
$$
\{P \bigwedge \neg cond \} \ code2 \ \{Q\}
$$
to prove the branch satisfies the specifications



**Method Calls**:

Given the following method call

```c++
//MID: P
someMethod(v1, ..., vn)
//MID: Q
```

where

```c++
void someMethod(type x1, ..., type xn)
//PRE: R
//POST: S
```

To prove this, we need to prove that:

- We can actually call the method (the precondition $R$) is satisfied
- Given the precondition $P$ and postcondition $S$ of the method, we get the postcondition $Q$

Symbolically,
$$
P \rightarrow R[\overline{x} \mapsto \overline{v}] \bigwedge P[\overline{v}[..) \mapsto \overline{v}[..)_{old}] \bigwedge S[\overline{x} \mapsto \overline{v}, \ \overline{x}[..)_{pre} \mapsto \overline{v}[..)_{old}] \rightarrow Q
$$



Given a function with a return value, the specification that we need to prove becomes:
$$
P \rightarrow R[\overline{x} \mapsto \overline{v}] \bigwedge P[\overline{v}[..) \mapsto \overline{v}[..)_{old}][res \mapsto res_{old}] \bigwedge res = r \bigwedge S[\overline{x} \mapsto \overline{v}, \ \overline{x}[..)_{pre} \mapsto \overline{v}[..)_{old}][res \mapsto res_{old}] \rightarrow Q
$$



**Recursion**:

Remember to replace variables (for ex $[i \mapsto i+1]$) if necessary, other parts are the same as reasoning about method calls



**Loops**:

Given a loop of the form

```c++
while(condition){
    code
}
//MID : M
```



If we can find a property $I$ such that:

- $\forall n \in \mathbb{N}$, $I$ holds after $n$ iterations of the loop (Shown using induction)
- If $I$ holds and the loop condition does not hold, then this implies the mid-condition $M$

This property $I$ is called the **loop invariant**



To prove a loop:

- We need to show that the loop variant holds right before the loop
- The loop body preserves the invariant whenever the loop condition holds
- Immediately after the loop, the invariant and the fact that the loop condition is false must imply the mid condition $M$ 

Symbolically, we prove that,
$$
P \rightarrow I, \ \{I \bigwedge cond\} \ body \ \{I\}, \ I \bigwedge \neg cond \rightarrow M
$$

- where $P$ is the pre-condition right before the loop
- $M$ is the mid condition right after the loop

To prove $P \rightarrow I$, we need to prove:
$$
P [mod \mapsto mod_{old}] \rightarrow I
$$
To prove $\{I \bigwedge cond\} \ body \ \{I\}$, we need to prove:
$$
I[mod \mapsto mod_{old}] \bigwedge cond[mod \mapsto mod_{old}] \bigwedge \text{ body effect } \rightarrow I
$$

- $mod$ is the list of variables that are modified by the code in the loop
- The **body effect** might include some implicit code effects. For ex, $a[..) \approx a[..)_{pre}$ whenever the code doesn't change the array itself



We also need to track the progress of the loop

We do this by finding an integer expression which:

- is larger than some value at the end of each loop iteration
- decreases in every loop iteration

Such an expression is called the **loop variant**

The loop variant measures progress towards completion

Symbolically, we prove that,
$$
V \geq 0 \bigwedge V[i \mapsto i_{old}] > V
$$




**Partial Correctness**: The program will satisfy the post-condition given that it terminates

**Total Correctness**: The program will satisfy the post-condition and terminate

