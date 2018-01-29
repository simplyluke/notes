# CS345 Haskell
2018-01-19
2018-01-22
2018-01-24

He’s teaching from (and recommends) [Learn You a Haskell for Great Good!](http://learnyouahaskell.com/). Already own - should work ahead some this weekend.

“You need to read haskell like it’s poetry… read every line carefully… as opposed to more like a trashy novel which is what java is” 

“You can’t print in a normal function because it’s a side effect”
`main` is the only function that can have prints
## GHCI
`:l` to load/compile a file and be able to call its functions
`:r` will reload the file
## Functions
calling  a function is done such as `doubleMe 9` which returns 18 
`doubleMe x = x * x `
camelCase the names
left associative 

### Recursive functions
`pow n m = if m == 0 then 1 else n * pow n (m-1)`
```
pow1 n 0 = 1
pow1 n m = n * pow1 n (m-1)
```
The above uses _pattern matching_ 
```
pow2 n m = 
case m of 
0 => 1
m' => n * pow2 n (m' - 1)
```
the above uses cases

`pow3 = \n -> \m if m == 0 then 1 else n * pow3 n (m-1)`
“This is a first class function” ? _Clarify what he’s doing here_
## Whitespace
Haskell is indentation sensitive  
use indents to break functions into lines, much like python
## If statements 
`doubleSmallNumber x = (if x > 100 then x else x*2) + 1`
## Lists
`lostNumbers = [4,8,16]`
`l = 1: [2,  3,  4]`
`:` is the cons operator  - right associative 
`l’ = 1 : 2 : 3 : 4 : []`
### Concat
`++` operator
`cat = “Hello” ++ “World”`
## Comments
`—-` inline 
## Strings
Lists of chars
## Data
defining new data types
`data BOOL = TRUE | FALSE `
`data GEOM = Point Int | Rect Int Int Int Int`
“These are called algebraic data types” 
Datatypes and constructors must begin with uppercase letters
`a = Point 3 5`
`b = Rect 1 1 10 10`
Both will be of type GEOM, “Point and Rect are functions not types, you can’t use them in a place where a type is expected”

```
data POINT = Point Int Int
  deriving Show

data GEOM = GPoint POINT
          | Rect POINT POINT
          | Circle POINT Float
          | Group [GEOM]
  deriving Show
```

## Type classes
```
class Eq a where
	(==) :: a -> a -> Bool
```
```
instance Eq Int where
	(==) = inteq
```
allows you to apply properties to different types

```
class Show a where
	show :: a -> string

instance Show Int
	show :: Int -> String
	-- implementation 

```
# Readings 
## Learn you a haskell for great good 
### Chapter 1 - starting out
`==` will do type checking
*infix* functions go between two parameters 
most functions are *prefix* functions which come before their params, no parens or commas needed

“function application has the highest precedence of all the operations in haskell”
#school/cs345 #dev/haskell