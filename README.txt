lex.rkt and simpleParser.rkt helpes to parse the code into the supported form.
Interpreter interprets the program and returns a value (Based on denotational semantics)

(02/17/2019):

1. In 'declare', change the structure so the semantics is more clear
	-The last case the value needs to be parsed into 'M-value' function
2. under 'if-else', change the name of abstraction to "stament" and "else-stament"
3. In 'return' change "M-name" to "M-value"
4. If-else statement change of abstraction, error message deleted
(error will never be reached)
5.Change the name "interpreter" to "interpret"
6.While-interpret added
7.For 'M-value', add a case to address negative sign, a helper method "isRightOperandNull" added.
8.In 'program-interpret', add a condition for return.


Abstraction:
Changed (define var-name cdr) to (define var-name cadr)
Changed var-name-c to isDeclared to differentiate from (define var-name cadr)
Added (define get-vars-list car) and (define get-val-list cadr) for stat
- couple other changes to abstraction
fixed return of true/false
removed let
Worked on doing the extra challenge part, got everything to work but test 25. 

^Can't seem to get the right x value without affecting other tests for this.
Have a problem with too many (M-state (___ stmt) state) terms. This is mainly due to retrieving the state upon side effects. 

---------------------------------------------------------------------------------------------------

03/03/2019
Starting interpreter 2.
Polish up the previous code, delete multiple "assign" statement. Modification in M-value methods. All side effects accomplished. Ready for interpreter 2.


03/05/2019
Use call/cc instead of cps. 
Return added,
break added,
continue added.
Test 1-10 passed.
However, break and continue has an error problem, also when continues and breaks the state does not pop top layer.


(03/06/2019):
Changed the representation of the state so that each scope has its bindings in its own list.
For example:
    ((a b c) (1 2 3) (x y z) (4 5 6)) -> (((a b c) (1 2 3)) ((x y z) (4 5 6)))
Hopefully, this makes changes for Part 3 easier to incorporate into pre-existing code.

Changed variable declarations so that variables with the same name can exist between different scopes.
Changes to a variable with a specific name will affect only the first appearance of the variable with that name in the state.
Declaring a variable with the same name in an inner scope never happens in any of the given test cases, so this change does not affect any test results in this part of the assignment.
This functionality might be necessary for Part 3 though.

Some function names were changed to be more consistent/clear.
Elaborated a bit on some function descriptions.

