%title: Advanced (Python) Features!
%author: Orden Aitchedji
%date: 2019-04-08

               Don't get rattled by what I say.
                                     __    __    __    __                              
                                    /  \  /  \  /  \  /  \                
               ____________________/  __\/  __\/  __\/  __\_____________________________       
               ___________________/  /__/  /__/  /__/  /________________________________       
                                  | / \   / \   / \   / \  \____         
                                  |/   \_/   \_/   \_/   \    o \                              
                                                          \_____/--<
                                                                    It's just my opinion.





> This Workshop goes over solutions for very simple common problems,

> that people tend to solve in sub-optimal ways!


-------------------------------------------------------------------------------

-> # Background
<br>

  * Found myself spending a lot of time on code styling:
<br>

> While any kind of *black magic* is possible with Python,
<br>

> the `most explicit` and `straightforward` manner is *preferred*.
<br>



  * Conclusion?

  <br>
      * I suck at Python.
    
  <br>
> Python is powerful when used right.

  * So why am I not using it to its fullest potential?

      <br>
      *   ¯\\_(**)_/¯

  <br>
  * Decided to investigate supported features:

  * Found that: 
  
  <br>
      * *Python (3) is awesome, it's loaded with features!*

-------------------------------------------------------------------------------

-> # Objectives

## Highlight

  * *Python 3 features*

      * `f-strings`

      * `enumerate`

      * `For ... else`

      * `Exception handling`

  <br>
  * The *Itertools* Operators

        * `zip`

  <br>
  * The *Collections* Module

        * `defaultdict`

  <br>
  * Build a *Decorators* function.
      * A function that `takes a function` as a parameter and `returns a function`.


-------------------------------------------------------------------------------

-> # Python 3 features

*f-strings*

`    myX, someY, someZ = "3", "5", 7    `



<br>
* Option #0: *concatenation*

     _concatenation = 'X = ' + myX + ' | Y = ' + someY + ' Z = ' + str(someZ)


<br>
* Option #1: *%-formatting*

     _percent = 'X = %s | Y= %s | Z = %d' % (myX, someY, someZ)


<br>
* Option #2: *str.format()*

     _format = 'X = {} | Y= {} | Z = {}'.format(myX, someY, someZ)


<br>
* Option #3: *f-string*  [Python *3.6+*]

     _fstring = f'X = {myX} | Y= {someY} | Z = {someZ}'


-------------------------------------------------------------------------------

-> # Python 3 features

*enumerate* 

<br>
* Walk through a list and print position and cities.

     
          1  cities = ['Denver', 'Lakewood', 'Golden', 'Englewood']
          

<br>
* The Bad Way

     
          2  i = 0
          3  for city in cities:
          4     print(i, city)
          5     i += 1
          

<br>
* The Pythonic Way

     
          6  for i, city in enumerate(cities):
          7     print(i, city)
          

-------------------------------------------------------------------------------

-> # Python 3 features

*For ... else*

<br>
* Search the needle in the haystack.

     
          1  needle = 'd'
          2  haystack = ['a', 'b', 'c']

<br>
>We can just ask *if needle in haystack* but ... we have a different purpose here.

<br>
* The Bad Way

     
           3  found = False
           4     for letter in haystack:
           5        if needle == letter:
           6           print('Found!')
           7           found = True
           8           break
           9    if not found:
          10        print('Not Found!')      
          

<br>
* The Pythonic Way

     
          11  for letter in haystack:
          12     if needle == letter:
          13        print('Found!')
          14        break
          15  else:
          16     print('Not found!')
          


-------------------------------------------------------------------------------

-> # Python 3 features

*Exception handling*

* Say we want to convert variable to an integer.

          1    print('Converting!')
          2    print(int('x'))
          3    print('Done!')

<br>
> *ValueError*      Python doesn't know how to do that.

<br>
> Most people are familiar with *try/except*
<br>

          4    print('Converting!')
          5    try:
          6       print(int('x'))
          7    except:
          8       print('Conversion Failed!')
          9    print('Done!')

<br>
> *try* statement supports an *else* statement -> `If no-except`
<br>

           4    print('Converting!')
           5    try:
           6       print(int('x'))
           7    except:
           8       print('Conversion Failed!')
           9    else:
          10       print('Conversion Successful!')    
          11    print('Done!') 


-------------------------------------------------------------------------------

-> # Python 3 features

*Exception handling*

> *try* statement also support a *finally* statement for -> `Always`
<br>

          11    print('Converting!')
          12    try:
          13       print(int('x'))
          14    except:
          15       print('Conversion Failed!')
          16    else:
          17       print('Conversion Successful!')  
          18    finally:  
          18        print('Done!') 

<br>
> The *finally* statement may seem a bit pointless, but it does serve a purpose. :)
<br>

* Say we only had a *try/finally*
<br>

          19    print('Converting!')
          20    try:
          21       print(int('x'))
          22    finally:
          23       print('Done!')     

<br>
> We still get a *ValueError* but ... *Done* still gets printed.

<br>
> Convinient for *Clean Up code*. 

<br>
* Say you're dealing with a file & an error occurred.
<br>

     * You *nevertheless* want to close the file.

-------------------------------------------------------------------------------

-> # The Itertools Operators

*zip*

<br>
* Walk through the two lists at the same time and print (x,y).

     
          1  x_list = [1, 2, 3]
          2  y_list = [4, 5, 6]
          

<br>
* The Bad Way

     
          3  for i in range(len(x_list)):
          4      x = x_list[i]
          5      y = y_list[i]
          6      print(x, y)
          

<br>
* The Pythonic Way

     
          7  for i in zip(x_list, y_list):
          8     print(x, y)
          

-------------------------------------------------------------------------------

-> # The Collections Module

## Implements alternative container datatypes other than the Built-ins to store collections of data.

*defaultdict*

<br>
* Say we want to get my age from a dictionary of ages.

           1  ages = {
           2       'John'   : 31,
           3       'Mary'   : 28
           4  }

<br>
* The Bad Way

     
           5  if 'Orden' in ages:
           6      age = ages['Orden']
           7  else:
           8      age = 'Unknown'
           9  print(f'Orden is {age} years old.')
          

<br>
* The Better Way

          10  age = ages.get('Orden', 'Unknown')
          11  print(f'Orden is {age} years old.')


<br>      
* The Pythonic Way 
     * Using *defaultdict* from the *collections* library.
     
     <br>
          12  from collections import defaultdict
          13
          14  ages = defaultdict(lambda: 'Undefined', ages)
          15  print(f'Orden is {ages['Orden']} years old.')


-------------------------------------------------------------------------------

-> # Decorator Funtions

* We have a *div* function that divides some number *a*, by some other number *b*.

          1  def div(a, b):
          2     return a / b
          3
          4  print(div(10, 5))

<br>
* Say instead we had

          5  print(div(10, 0))

<br>
> We get a *ZeroDivisionError*
<br>

* How can we fix this?
<br>

     * Add a check in our *div* function to make sure we're not dividing by 0
<br>

     * We can use *decorators*
<br>

          * Lets us `extend` the functionality of our function.
          
          * With `No modification` to the function itself! :)


-------------------------------------------------------------------------------

-> # Decorator Funtions

* Let's create a decorator function *check*
<br>

           1  def check(func):
           2     def inside(x, y):
           3        if b == 0: 
           4           print('Can't divide by 0')
           5           return
           6        func(x, y)
           7     return inside

<br>
* To actually add the *check* functionaly to our *div* function.
<br>

     * We create a variable and set it equals our decorator function. 
<br>

           8  div = check(div)
           9 
          10  print(div(10, 0))

<br>
> Running this, will return: *'Can't divide by 0'*
<br>

* This is a really common pattern in Python.

<br>
* Python added a special syntax just for decorators.
<br>

     * Instead of a the repetative pattern underneath your function,

<br>
     * You can simply type *@check* above the function.

<br>
           1  @check
           2  def div(a, b):
           3     return a / b
           4
           5  print(div(10, 0))

<br>
> Running this again, will return *'Can't divide by 0'*


-------------------------------------------------------------------------------

-> # Context Manager

## Context managers are mainly used to properly manage resources.
<br>

* The most common use of a context manager is the opening of a file:
<br>

`with open('workfile', 'r') as f:`

<br>
> Most developers have no idea *how* that really works underneath nor how they can create their *own*.

<br>
<br>






* Good Resources are out there.

* I found these helpful:

[Advanced Python Features](https://tech.io/playgrounds/500/advanced-python-features?forceABTesting=Runnable&utm_source=code-org&utm_campaign=HOC2017&utm_term=advanced-python#context-managers)

[Context Managers the Easy Way](https://www.youtube.com/watch?v=U2t2t_cpvoc)


-------------------------------------------------------------------------------
-> # Closing

<br>

## Contact

  I'm *ordn007* on `github` and *oaitchedji* `linkedin`.

  This Presentation is published at [PythonTips](https://github.com/PythonTips/ordn007/)

  You are welcome to connect with me at [LinkedIn](http://www.linkedin.com/in/oaitchedji)

<br>
                        .---.
                       /     \
                       \.@-@./
                       /`\_/`\
                      //  _  \\
      __________     | \     )|_
    < Questions? >  /`\_`>  <_/ \
      ----------    \__/'---'\__/

