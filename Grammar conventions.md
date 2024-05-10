The lexical and syntactic grammars are presented using grammar productions. Each grammar production defines a non-terminal symbol and the possible expansions of that nonterminal symbol into sequences of non-terminal or terminal symbols. In grammar productions, non-terminal+ symbols are shown in italic type, and terminal symbols are shown in a fixed-width font.

The first line of a grammar production is the name of the non-terminal symbol being defined, followed by a colon. Each successive indented line contains a possible expansion of the nonterminal given as a sequence of non-terminal or terminal symbols. For example, the production:

if-expression:
      if if-condition then true-expression else false-expression

defines an if-expression to consist of the token if, followed by an if-condition, followed by the token then, followed by a true-expression, followed by the token else, followed by a false-expression.

When there is more than one possible expansion of a non-terminal symbol, the alternatives are listed on separate lines. For example, the production:

variable-list:
      variable
      variable-list , variable

defines a variable-list to either consist of a variable or consist of a variable-list followed by a variable. In other words, the definition is recursive and specifies that a variable list consists of one or more variables, separated by commas.

A subscripted suffix "opt" is used to indicate an optional symbol. The production:

field-specification:
      optionalopt field-name = field-type

is shorthand for:

field-specification:
      field-name = field-type
      optional field-name = field-type

and defines a field-specification to optionally begin with the terminal symbol optional followed by a field-name, the terminal symbol =, and a field-type.
