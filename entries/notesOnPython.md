# How is Python executed?

# CPython vs. Cython

  Using Wikipedia here.
 
## CPython 

   'CPython is the reference implementation of the Python programming language' (Wiki). It is written in both C and Python.

   'CPython can be defined as both an interpreter and a compiler as it compiles Python code into bytecode before interpreting it'.

   CPython makes use of a GIL, meaning that 'within a single (interpreter) process only one thread may be processing Python bytecode at any one time'. However, this does not render multithreading pointless in Python; e.g. threads could be waiting on external processes to complete. To achieve true parallel Python code execution, it is necessary to have multiple CPython interpreter processes running concurrently.

   Besides CPython, there are other Python implementations:
   * Jython, written in Java for the JVM
   * PyPy, written in RPython and translated into C
   * IronPython, written in C# for the Common Language Infrastructure

  All three of the alternative implementations above provide a JIT compiler, but CPython does not (and likely never will).  

## PyPy

   The name 'PyPy' is used to refer to two things:

   * the RPython translation toolchain, used to generate interpreters for dynamic programming languages
   * a particular implementation of Python produced using RPython

     Starting with source code written in RPython, the RPython translation toolchain is applied to the source, producing a #binary executable#, PyPy. PyPy is a Python interpreter written in Python, hence its name.

     In order to disambiguate these two things, PyPy is now used to refer only to the Python implementation and RPython to the translation toolchain. RPython source code is written in a restricted subset of Python (hence 'Restricted Python'). 

   'PyPy is a JIT compiler, not an interpreter': so says Wikipedia, something flatly contradicted by the PyPy documentation. PyPy apparently does have a JIT compiler. 

   A description of PyPy's execution model (?) from Wiki:
   
>The PyPy project has developed a toolchain that analyses RPython code and translates it into a form of byte code, together with an interpreter written in the C programming language. Much of this code is then compiled into machine code, and the byte code runs on the compiled interpreter. 


>PyPy’s Python Interpreter is written in RPython and implements the full Python language. This interpreter very closely emulates the behavior of CPython. It contains the following key components:
>
>* a bytecode compiler responsible for producing Python code objects from the source code of a user application;
>* a bytecode evaluator responsible for interpreting Python code objects;
>* a standard object space, responsible for creating and manipulating the Python objects seen by the application.
>  
>The bytecode compiler is the preprocessing phase that produces a compact bytecode format via a chain of flexible passes (tokenizer, lexer, parser, abstract syntax tree builder, bytecode generator). The bytecode evaluator interprets this bytecode. It does most of its work by delegating all actual manipulations of user objects to the object space. The latter can be thought of as the library of built-in types. It defines the implementation of the user objects, like integers and lists, as well as the operations between them, like addition or truth-value-testing.

## Cython

   'Cython is a programming language that aims to be a superset of the Python programming language, designed to give C-like performance with code that is written mostly in Python with optional additional C-inspired syntax.'

   'Cython is a compiled language that is typically used to generate CPython extension modules. Annotated Python-like code is compiled to C or C++ then automatically wrapped in an interface, producing extension modules that can be loaded and used by regular Python code using the import statement, but with significantly less computational overhead at run time. Cython also facilitates wrapping independent C or C++ code into Python-importable modules.'

# Some notes on interpreters and compilers

  Taken from https://softwareengineering.stackexchange.com/a/269878 and other sources given in text

 
## Definitions
   
   A interpreter is a program or machine or other mechanism that executes a program in a language such that it performs the effects of the program and evaluates the results as prescribed by the language specification.

   A CPU is usually an interpreter for its own instruction set, but modern high-performance CPUs may have an underlying proprietary private instruction into which the public instruction set is compiled or interpreted.

   I'm used to the idea that a compiler translates a program from one language into another, but not the stipulation that the compiled program be semantically equivalent to the input program, i.e. compilation preserves the semantics of the input program. It seems obvious now, of course.

   Just-in-time (JIT) compilers compile a program as it is running, whereas ahead-of-time (AOT) compilers compile a program ahead of runtime.

   Note that AOT/JIT is not a meaningful distinction for interpreters.

## JIT compilers

   JIT compilers differ in what they compile, how often, and at what resolution.

   The JIT compiler in Microsoft's 'Common Language Runtime':

   * compiles code once
   * compiles a whole assembly at a time

     NB: a CLR assembly is a deployment unit, packaged as a DLL or executable file.

   Other JIT compilers may recompile code several times as the program runs and information is gathered to the end of optimising the code's execution.

   Another distinction is between JIT compilers which compile a static unit of code (a unit being a module, function, class, etc.) in one go and those which trace the dynamic execution of code to find dynamic traces (typically loops) that they will then compile (these are tracing JITs).

   In its most basic form, a JIT compiler removes interpreter overhead, but a good one performs a host of optimisations. JIT compilers can generate specialised code at runtime on the basis of data gathered from the program in execution, data not available to AOT compilers. 

   Note that JIT compilers 'can also interact with interpreters, unlike ahead of time compilers...', which accounts for their association with interpreters, although 'they can and do exist independently'. 
   (https://stackoverflow.com/questions/13034991/does-the-python-3-interpreter-have-a-jit-feature)

## Combining interpreters and compilers

   AOT compilers can be combined with interpreters. Typically, compilation translates a higher-level, readable language to a more compact language optimised for machine interpretability. The CPython Python execution engine has an AOT compiler that compiles Python sourcecode to CPython bytecode, which is then interpreted by the Python interpreter.

   Another approach is to combine the two in a 'mixed-mode execution engine'. Here two modes of execution work side-by-side, rather than sequentially. Compilation takes time, and a lot of time if the code is to be heavily optimised, so one can run the interpreter on the code to begin with whilst the JIT compiler compiles it, then switch execution to the compiler's output code once it is ready (what sort of application would one run like this? Why not just wait for the compiler to finish?)

   Alternatively, one can run the interpreter for some time to collect information on execution, then feed this dynamic information to the compiler to allow it to generate more optimised code. If the code is overly optimised, one can also throw away the compiled code and revert to interpreting. The HotSpot JVM does this: it contains both a JVM bytecode interpreter and a JVM bytecode compiler (besides another compiler; javac?). HotSpot is so-called because it seeks 'hot spots' during execution to target for just-in-time optimisation (a 'hot spot' more generally is a compute-intensive region of a program).

   The two approaches above can also be combined in a two-phase approach. The first sees the AOT compiler compile to bytecode and the second uses a mixed-mode engine that interprets the bytecode and compiles it to native (machine) code. The Rubinius Ruby execution engine works like this.
  
### More on Java 

The JIT compiler compiles bytecode to native machine code (https://www.baeldung.com/graal-java-jit-compiler). Oracle's JDK contains two conventional JIT compilers, C1 and C2, for client-side and server-side compilation. The C2 compiler carries out longer periods of compilation but produces better-optimised code. HotSpot uses both compilers in the default execution mode in an approach known as 'tiered compilation'. The JVM begins by interpreting all code. Frequently called methods are identified as the code is interpreted and these are compiled with C1. Future calls of these methods are monitored and if their use becomes more frequent, they are compiled with C2. 
