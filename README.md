# Pashmak programming language
hi there. this is pashmak programming language. pashmak is a interpreter wrote in python.
the pashmak scripts has a cool syntax.

### hello world!
this is a simple hello world script in pashmak:

```bash
mem 'hello world\n'; out ^;
```

read the following Documentation to learn pashmak

# Documentation



## Basics

a simple printing in screen in pashmak:

```bash
mem 'some thing to print\n'; out ^;
```

#### how it works?

before every thing, we'll browse about pashmak syntax structure.
the base structure of pashmak syntax, is this:

```bash
<operation> [arguments];
<operation> [arguments];
<operation> [arguments]; <operation> [arguments];
```

some thing like this. in this example, we have two operations:

```bash
mem 'some thing to print\n'; # first operation
out ^; # second operation
```

in here, mem is a operation and `'something to print\n'` is argument of that, and
out is a operation and `^` is argument of that.

but this code doing what?

when you run the script in terminal:

```bash
pashmak myscript.pashm # or any filename you saved code in that
```

you will get this output:

```
something to print
```

this code, prints `'some thing to print'` on the stdout.
but how?

first, `mem` command brings the string `'some thing to print'` on the memory, and next `out` command prints the memory value on screen.

### what is `mem`?
you cannot print any thing like this:

```bash
out 'hello world\n';
```

because commands in pashmak never gets a value directly.
if you wanna pass a value to the commands, need to use `mem` command to load that value.
in this example, we first loading the `'some thing to print'` with mem command, and next pass value of mem to the out command:

```bash
mem 'hello world';
out ^; # the ^ is pointer to value of mem
```

the ^ is pointer to value of mem

you can also write the code like this to have shorter code:

```bash
mem 'hello world\n'; out ^;
```

###### NOTE: remember to put \n when you want to go next line

#### mem is temp

look at this example:

```bash
mem 'some thing\n';

out ^; # output: some thing

out ^; # output: None
```

why in the first time while reading mem value, the value correctly printed on screen, but in the second time the None value printed?

because memory is temporary. when you read the memory, that will be empty automatic after read.

look at this example:

```bash
mem 'first value\n';
out ^;

mem 'second value\n';
out ^;
```

output of this code:

```
first value
second value
```

###### NOTE: the # is comment operation. you can put comment in your code after # character


### more about mem
you can calculate every thing in mem

for know this, look at the following examples:

```bash
mem 'hi there'; out ^; # output: hi there

# you can paste strings
mem 'first string ' + 'last string'; # output: first string last string

# run math operations
mem 2*7; out ^; # output: 14

mem 3*(2+1); out ^; # output: 9

mem str(7*7) + ' is sum'; out ^; # output: 49 is sum
# the `str` function gets a value and convert it to string.
# in here you can not paste number to string. first need to convert num to str with str()
```

the `mem` command is very very important and you need to use it every where



## Variables

variables are like a put where you can save a data on them

to set and handle variables in pashmak, we work with tree commands: `set`, `copy`, `free`

```bash
set %myvar; # set a variables named %myvar
mem 'this is data'; # bring string 'this is data' to mem
copy ^ %myvar; # copy mem (^) to %myvar

out %myvar; # output: this is data
```

###### NOTE: always put % before name of variable every where

also you can set more than one variables with `set` command:

```bash
set %var1 %var2 %var3;
```

### use variables in mem

look at this example:

```bash
set %name; # set name variable
mem 'parsa'; copy ^ %name; # copy 'parsa' string to name variable

mem 'hello ' + %name + '\n'; out ^; # output: hello parsa

set %num; mem 12; copy ^ %num;
mem %num*5; out ^; # output: 60

set %num2; mem 4; copy ^ %num2;

mem %num * %num2 + 1; out ^; # output: 49
```

#### how it works?
we declared a %name variable and put `'parsa'` string in that

next, in mem we maked a string and paste %name variable value to `'hello '` with a \n in end of that, and we printed that mem

you can use variables in mem like that example


### free variables
when you seta variable, that var is in memory. you can delete that var with `free` command:

```bash
set %somevar;
mem 'some value'; copy %somevar;

out %somevar; # output: some value

free %somevar;

out %somevar; # you will get VariableError: undefined variable %somevar (because it is deleted by free command)
```

also you can free more than one variable with `free` command:

```bash
free %var1 %var2 %var3; # ...
```

#NOTE: in that example, we used `copy` command like this:

```bash
mem 'some value';
copy %somevar;
# that is alias of
copy ^ %somevar;
```

when you give just a variable to copy command, the mem will be copy in that variable

look at this example:

```bash
set %var1 %var2;

mem 'hi'; copy %var1;
mem 'bye'; copy %var2; # this is alias of `copy ^ %var2`

out %var1; # output: hi
out %var2; # output: bye

copy %var1 %var2; # copy a variable in variable

out %var1; # output: hi
out %var2; # output: hi

```



