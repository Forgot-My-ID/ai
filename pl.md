Negation

"It is not the case , that p". "Today is Friday." would be "It is not the case that, today is Friday." or more succinctly "Today is not Friday."

```python
def negation(P):
    return not P

print("p    a")
for p in [True, False]:
    a = negation(p)
    print(p, a)
```

Conjunction

"I am a rock and I am an island." 

```python
def conjunction(p, q):
    return p and q

print("p    q    a")
for p in [True, False]:
    for q in [True, False]:
        a = conjunction(p, q)
        print(p, q, a)
```

Disjunction 

"She studied hard or she is extremely bright." 

```py
def disjunction(p, q):
    return p or q

print("p    q    a")
for p in [True, False]:
    for q in [True, False]:
        a = disjunction(p, q)
        print(p, q, a)
```

Exclusive Disjunction

"Take either 2 Advil or 2 Tylenol."

```py
def exclusive_disjunction(p, q):
    return (p and not q) or (not p and q)

print("p    q    a")
for p in [True, False]:
    for q in [True, False]:
        a = exclusive_disjunction(p, q)
        print(p, q, a)
```

Implication

" If you get a 100 on the final exam, then you earn an A in the class." 

```python
def implication(p, q):
    return not p or q  # p → q is equivalent to not p or q

print("p    q    a")
for p in [True, False]:
    for q in [True, False]:
        a = implication(p, q)
        print(p, q, a)
```

Bi-Implication

"It is raining outside if and only if it is a cloudy day."

"You get a 100 on the final exam if and only if you earn an A in the class." 

```python
def bi_implication(p, q):
    return p == q  # True if p and q are the same

print("p    q    a")
for p in [True, False]:
    for q in [True, False]:
        a = bi_implication(p, q)
        print(p, q, a)
```

 Example 6 - Conditional, Converse, Contrapositive and Inverse.

a. Translate the statement, "If an integer n, is divisible by 4, then it is divisible by 2", using a conditional.
b. Form its converse, contrapositive, and inverse and translate.
Solution
a. Let p: An integer n, is divisible by 4
q: An integer n, is divisible by 2
The sentence, "If an integer n, is divisible by 4, then it is divisible by 2", is translated p⟹q.

b. Its converse is q⟹p, which may be translated, "If an integer n, is divisible by 2, then it is divisible by 4."

The contrapositive is ¬q⟹¬p, which may be translated, "If an integer n, is not divisible by 2, then it is not divisible by 4."

The inverse is ¬p⟹¬q, which may be translated, "If an integer n, is not divisible by 4, then it is not divisible by 2." 

Create a truth table for the compound proposition: (p∧q)⟹(p∧r) for all values of p,q,r. 

```python
def implication(p, q, r):
    return not (p and q) or (p and r)  # (p∧q) ⟹ (p∧r)

print("p     q     r     (p∧q) ⟹ (p∧r)")
for p in [True, False]:
    for q in [True, False]:
        for r in [True, False]:
            result = implication(p, q, r)
            print(f"{p}   {q}   {r}   {result}")
```

The Universal Quantifier , ∀, represents the statement "for all", "for every", "for each". When it comes before a statement, it means that statement is true for all values in the domain. 

Let P(x) be the statement x+x>x. Is this true for all integers x?

```python
stmt = "For all x, P(x)."
def P(x):
    return x + x > x

forall = True
for x in [-2, -1, 0, 1, 2]:
    # check if at least 1 is false
    if not P(x):
        forall = False
print(stmt)
print(forall)
```

The Existential Quantifier , ∃, represents the statement "there exists", "for some", "at least one". When it comes before a statement, it means the statement is true for at least one value in the domain. 

Existential Quantifier ∃x,x^2=4

Let P(x)
be the statement x^2=4. Is this true for at least one integer x? 

```python
stmt = "There exists an x, such that P(x)."
def P(x):
    return x**2 == 4

exists = False
for x in [-2, -1, 0, 1, 2]:
    # check if at least 1 is true
    if P(x):
        exists = True
print(stmt)
print(exists)
```

"Every student in this class has taken Programming Fundamentals."

This is a universally quantified statement and can be expressed as ∀xP(x) where P(x) is the statement "x has taken Programming Fundamentals" and the domain consists of all the students in this class. The negation of the statement would be "It is not true that every student in this has taken Programming Fundamentals." 
Equivalently, "There is a student in this class who has NOT taken Programming Fundamentals." This is an existentially quantified statement expressed as ∃x¬P(x).
This demonstrates that the negation of a universally quantified statement is an existential statement. In symbols, we have ¬∀xP(x)≡∃x¬P(x).

Someone in the class can speak Latin.
Using quantifiers, we write this statement as ∃xL(x)
where L(x) is the proposition "x speaks Latin." and the domain is the students in the class. Its negation would be ∀x¬L(x).
All the students in the class can not speak Latin.

```python
from itertools import product

# Define the truth values for propositions
truth_values = list(product([True, False], repeat=2))  # for 2 propositions (p, q)

# Function to print the truth table
def print_truth_table(statement_func, statement_name, variables=['p', 'q']):
    print(f"\nTruth Table for: {statement_name}")
    print(" | ".join(variables) + " | Result")
    print("-" * (len(variables) * 4 + 10))
    for values in product([True, False], repeat=len(variables)):
        result = statement_func(*values)
        print(" | ".join(str(v) for v in values) + f" | {result}")

# a. It is raining outside if and only if it is a cloudy day (p <-> q)
def statement_a(p, q):
    return p == q  # biconditional

# b. If you get a 100 on the final exam, then you earn an A in the class (p -> q)
def statement_b(p, q):
    return not p or q  # implication

# c. Take either 2 Advil or 3 Tylenol (p or q)
def statement_c(p, q):
    return p or q

# d. She studied hard or she is extremely bright (p or q)
def statement_d(p, q):
    return p or q

# e. I am a rock and I am an island (p and q)
def statement_e(p, q):
    return p and q

# Print truth tables for each statement
print_truth_table(statement_a, "It is raining outside if and only if it is a cloudy day")
print_truth_table(statement_b, "If you get a 100 on the final exam, then you earn an A in the class")
print_truth_table(statement_c, "Take either 2 Advil or 3 Tylenol")
print_truth_table(statement_d, "She studied hard or she is extremely bright")
print_truth_table(statement_e, "I am a rock and I am an island")

```

