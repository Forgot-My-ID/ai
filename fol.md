Consider the following simple family scenario: 

define the Predicates: 

Parent(x, y): Indicates that x is the parent of y. 

Parent(y, z): Indicates that y is the parent of z. 

Grandparent(Parent(x, y), z): Indicates that x is the grandparent of z. 

Statements addressing the family 

Parent(Jhon, Mary): Jhon is Mary's father. 

Parent (Mary, Joe): Mary is Joe's mother. By using First Order logic we can conclude. 

Now prove Grandarent(.Jhon, Joe) Because Jhon is the father of Mary (Parent(Jhon, Mary)) and Mary is the mother of Joe (Parent(Mary, Joe)), as it can infer that Jhon is also the grandfather of Joe.

```python
# Define parent relationship using a dictionary
parents = {
    "John": "Mary",  # John is Mary's parent
    "Mary": "Joe"    # Mary is Joe's parent
}

# Define the Parent predicate
def Parent(x, y):
    return parents.get(x) == y

# Define the Grandparent predicate
def Grandparent(x, z):
    for y in parents:
        if Parent(x, y) and Parent(y, z):
            return True
    return False

# Check if John is the grandparent of Joe
print("Is John the grandparent of Joe?")
print(Grandparent("John", "Joe"))  # Expected: True
```

```python
from sympy import symbols, Function, And, Implies

# Define the symbols
John, Mary, Joe = symbols('John Mary Joe')

# Define the predicates
Parent = Function('Parent')
Grandparent = Function('Grandparent')

# Define the statements
statement1 = Parent(John, Mary)  # John is Mary's parent
statement2 = Parent(Mary, Joe)   # Mary is Joe's parent

# Define the rule for grandparent
grandparent_rule = Implies(And(Parent(John, Mary), Parent(Mary, Joe)), Grandparent(John, Joe))

# Print the conclusion
print("John is the grandparent of Joe.")
```

