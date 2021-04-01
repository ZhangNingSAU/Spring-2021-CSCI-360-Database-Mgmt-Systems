# How to write a query for Q7 in HW5?
# Method 1: no aggregate funtion Count()
+ then, we need to understand one concept we did not cover in our class
## DIVISION
+ DIVISION Operation, denoted by (÷)
  - The division operation is applied to two tables R and S, denoted by R(Z) ÷ S(X) where
    + Z is the set of columns of R
    + X is the set of columns of S
    + X is a subset of Z
    + Let Y be the set of columns of R that are not attributes of S, i.e, Y = Z - X
  - The result of DIVISION is a relation T(Y) that includes a row t if row t<sub>R</sub> appear in R with t<sub>R</sub>[Y] = t, and with t<sub>R</sub>[X] = t<sub>S</sub> for every tuple t<sub>S</sub> in S.
  - For a row t to appear in the result T of the DIVISION, the values in t must appear in R in combination with every row in S.
  - DIVISION Examples
  
  ![division](../Resources/division1.png)
  
  
  ![division2](../Resources/division2.png)
