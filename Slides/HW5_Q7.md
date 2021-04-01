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
  
  ![division](https://lukaseder.files.wordpress.com/2012/03/unbenannt1.png)
  
  
  ![divsion2](data:image/png;base64,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)
