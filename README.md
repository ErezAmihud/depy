# depy
This repo aims to decompile python3.9 - which no existing decompiler does. And ofcourse extend to more versions

### Desclaimer
Some of the data here may be inaccurate. Please point it out.

### Why create a new decompiler from scratch?

Good question.
This compiler - in contradiction to others - will only convert bytecode to ast tree and then use an external tool to convert the ast tree to code (`astunparse` in python <= 3.8 and `ast.unparse` in 3.9). That will save us some of the code and making it cleaner.

The decompiler will do a minimal effort convertion between the bytecode to the ast tree. Meaning things such as `or` statements and others can present itself as 2 different `if` statements - that will work but will look bad to the user. In this way I can try to throw out the problem of ambigious byte code. If someone want to improve the readability, then can do it in the ast!

When moving the bytecode to ast, the decompiler will use the context of the program. Meaning it will keep track of the python vm stack.
Probably, to make handling of the control flow easier, the decompiler will first split the function by its different possible paths and parse each inner part seperatly to connect it back later.

### Why doing it at all

I have read in different python decompilers issue boards that python 3.9 and up is more tricky to decompile because of ambigious instructions and trouble to follow control flows. I accept the challenge!
