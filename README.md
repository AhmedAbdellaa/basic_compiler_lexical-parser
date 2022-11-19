**1. Introduction**
A compiler is a computer program that helps you transform source code written in a language
of the highest level into a language of the lowest machine level. It converts the code written in
one programming language to another language without affecting the code 's purpose. The
compiler also efficiently makes the end code which is optimized for execution time and
memory space./
The compiling method involves simple translation and error detection mechanisms. Compiler
process goes through front-end lexical, syntax, and semantic analysis, and back-end code
generation and optimization.\
\
**2. Language description**
A program in this language consists of a main C function in which we can:\
• Declare integer, floating point and character variables.\
• Perform an assignment statement where the right-hand-side may be a constant, single variable or expression (including +,-,*, / operators as well as () ).\
• Perform an if/if-else statement which may include any number of assignment statements and if/if-else statements in any order. The condition of the if/if-else statement may include >,=,<=,==,!= and ().\
• In general, our main function may include any number of assignment and if/if-else statements in any order and as described above\


## parser analysis

main_fun :  int main  (  )   scope_stmt

scope_stmt : { statement_list   }

statement_list : statement_list   statement | ε


statement :expression | var_declaration | update_var | scope_stmt | if_stmt | return_stmt

type_specifier : int | float |char
var_declaration : type_specifier  ID  var_next 
var_next : , ID var_next | = expression var_next | ;
update_var : ID = expression ;

return_stmt : return expression ;


if_stmt : if (comparison) statement_list else_part
else_part : ε | else statement 
comparison: expression   comp_op   expression | expression 
comp_op : <= | < | > | >= | == | !=

expression : expression add_op   term | term
add_op : + | -
term : term   mul_op   factor | factor
mul_op : * | /
factor : ( expression ) | ID | NUM | FLOAT | CHAR


ID : [a-zA-Z_][a-zA-Z0-9_]*
NUM : [0-9]+
FLOAT : ([0-9]*[.])?[0-9]+
CHAR : ['][a-zA-Z][']
