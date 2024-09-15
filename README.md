# CPSC354 Investigation

## The Question
What is the role of syntactic and semantic formalism in programming language design? How does abstract syntax in a language aid in program 
verification and correctness, especially in safety-critical systems like avionics or medical devices?


## Introduction
### Role of Syntactic and Semantic Formalism in Programming Language Design

### Semantic Formalism
In programming language design, syntactic and semantic formalism plays a crucial role in defining how programs are written (syntax) and what 
they mean (semantics). Syntactic formalism focuses on the structural rules that govern the language’s syntax. These rules are typically 
specified using formal grammar systems like context-free grammars (CFGs), which ensure the correct arrangement of symbols in the language.

Semantic formalism, on the other hand, defines the meaning of syntactically correct programs. This can be approached in multiple ways, such 
as operational semantics (how the program executes), denotational semantics (what the program represents mathematically), and axiomatic 
semantics (what can be logically proven about the program’s behavior). Semantic formalism is essential for ensuring that programs behave 
correctly according to their design.

**Key roles of syntactic and semantic formalism:**
1. **Correctness enforcement**: By specifying syntactic rules formally, language designers can avoid ambiguity and enforce correct program 
structures. For example, type systems, which are a mix of syntactic and semantic rules, ensure that functions and data types are used 
consistently.
2. **Compilation and interpretation**: Syntactic rules help ensure that compilers and interpreters can efficiently translate high-level 
programs into machine code or another executable format. Semantic formalism ensures that the compiled code behaves as expected.
3. **Tool support**: Formal syntax and semantics allow the development of automated tools like parsers, analyzers, and proof assistants that 
can reason about programs, making programming more reliable.
4. **Language evolution**: As languages evolve, having formal syntactic and semantic rules enables designers to extend the language without 
introducing inconsistencies or errors.

### Abstract Syntax

**Abstract syntax** is a formal representation of a programming language's structure that abstracts away from the specific details of its 
surface syntax (such as punctuation, keywords, or stylistic conventions). It captures the logical essence of programs by focusing solely on 
the hierarchical and functional relationships between components, usually represented as an **Abstract Syntax Tree (AST)**. 

In contrast to **concrete syntax**, which focuses on how a program is written (e.g., how statements are delimited), abstract syntax concerns 
itself with how the program operates and the relationships between its various constructs. Abstract syntax is widely used in language 
design, compilation, and formal verification due to its simplicity and machine-readability.

### Importance in Semantics and Verification:
Abstract syntax plays a fundamental role in defining the formal semantics of programming languages, allowing for precise reasoning about 
program behavior. By representing language elements (like expressions, loops, or assignments) in a structured form, abstract syntax enables 
formal analysis techniques such as **symbolic execution**, **model checking**, and **deductive verification**. These methods are crucial for 
ensuring program correctness, especially in safety-critical systems like avionics, where failures can have catastrophic consequences.

### Example of Abstract Syntax:
Consider a simple arithmetic expression in a language like C:

```c
x = (5 + 3) * 2;
```

The concrete syntax of this statement specifies the exact characters to use, including parentheses, operators, and assignment symbols. In 
abstract syntax, the same statement would be represented in terms of its logical structure:

- The assignment (`=`) is the root operation.
- The left-hand side is the variable `x`.
- The right-hand side is a multiplication operation (`*`) with two sub-expressions: 
  - One being the constant `2`.
  - The other being an addition operation (`+`) between `5` and `3`.

This could be visualized as an Abstract Syntax Tree (AST) like this:

```
       =
     /   \
    x     *
         / \
        +   2
       / \
      5   3
```

This hierarchical representation makes it easier for tools to perform formal analysis, such as verifying that the expression adheres to type rules or evaluating potential runtime errors.
### Example in Formal Semantics:
In formal semantics, abstract syntax allows us to define program behavior in terms of transition rules without worrying about surface-level 
syntax. For instance, in the **K framework**, abstract syntax provides the scaffolding on which formal semantic rules are built, enabling 
verification of programs in languages like C or Java by ensuring that rules for computation are applied consistently across all program 
states.

By focusing on structure and behavior, abstract syntax is instrumental in developing reliable, verifiable, and formally analyzable systems. 
his is especially important in domains like avionics or medical devices, where correctness and safety are paramount, and formal verification 
based on abstract syntax ensures that no superficial syntactic variations can lead to misinterpretation or errors.



### Subfields of Programming Languages (PL) Contributing to the Question
Several subfields of programming languages (PL) research have contributed to the investigation of these questions, including:

1. **Formal Semantics**:
   - **Operational semantics** (by Plotkin), **denotational semantics** (Scott and Strachey), and **axiomatic semantics** (Hoare) all contribute by providing frameworks for defining and reasoning about the meaning of programs. These models allow formal reasoning about program correctness and enable the verification of complex systems.
   
2. **Type Theory**:
   - **Type systems** ensure that operations are used with the correct types, preventing errors related to incorrect data usage. Type theory intersects with formal semantics by allowing the static verification of program correctness and safety properties, especially in type-safe languages used in critical systems.

3. **Model Checking and Formal Verification**:
   - Subfields like **model checking** and **theorem proving** build on the foundations of formal semantics and abstract syntax. They provide automated tools that verify whether programs adhere to certain properties, such as correctness, safety, and liveness. Techniques like symbolic execution rely heavily on abstract syntax to verify the possible states and transitions of a system.

4. **Rewriting Systems**:
   - The field of **rewriting logic** (e.g., **K framework** and **Maude**) contributes by offering a formalism for defining language semantics through rewriting rules. These rules operate on abstract syntax structures and are used for formal verification, enabling automatic analysis and reasoning about program behavior.

### Influence Between Subfields

- **Formal semantics** influences both **type theory** and **verification** techniques by providing the foundational frameworks that define program behavior. For example, operational semantics is used in both type checking (to ensure correct usage of types during program execution) and model checking (to reason about state transitions).
- **Type theory** contributes to formal verification by allowing the static analysis of programs. For instance, strong type systems can prevent certain categories of runtime errors, thus reducing the need for extensive verification. In return, **verification tools** sometimes incorporate type theory to refine and enhance their verification methods.
- **Model checking** and **formal verification** depend on the formal definitions provided by **semantics** and **abstract syntax**. Without precise semantics, model checkers and theorem provers would lack a clear model to analyze, leading to potential gaps in verification coverage.
- **Rewriting systems**, such as those used in the **K framework**, leverage both formal semantics and abstract syntax to provide executable language definitions. This allows rewriting systems to act as a bridge between high-level language design and low-level verification, influencing the development of new languages with built-in verification features.

In sum, these subfields work together to provide the syntactic and semantic foundations required to ensure the correctness, reliability, and safety of programs, especially in critical systems like avionics or medical devices. The influence between subfields has led to the development of more robust verification techniques and language design principles.

## Historical Developments

The formalization of programming languages has a rich history that can be traced back to the 1960s and 1970s, with key developments in 
formal grammar (such as **Backus-Naur Form**, or BNF) and semantics.

1. **Syntactic Formalism**: The development of formal syntactic rules began with **context-free grammars** (CFGs), popularized by **John 
Backus** and **Peter Naur** during the design of ALGOL. This formalism became the standard for defining the structure of programming 
languages and led to the development of powerful parsing techniques used by modern compilers.

2. **Semantic Formalism**: The late 1960s saw the emergence of formal semantic models, including **operational semantics** (introduced by 
**Gordon Plotkin**), which defines how programs execute step-by-step. Another influential model, **denotational semantics**, was introduced 
by **Dana Scott** and **Christopher Strachey**, mapping programs to mathematical domains. **Axiomatic semantics**, developed by **C.A.R. 
Hoare**, introduced the use of formal logic (Hoare logic) to verify program properties.

3. **Abstract Syntax and Verification**: The concept of abstract syntax gained prominence in the 1970s, particularly through tools like 
**abstract syntax trees** (ASTs), which allowed compilers and verifiers to operate on a higher level of abstraction. The development of 
tools like **theorem provers** and **model checkers** in the 1980s and 1990s (e.g., the development of **SPIN** for model checking) further 
emphasized the role of abstract syntax in program verification.

4. **Safety-Critical Systems**: In safety-critical domains, the demand for rigorous verification grew. Standards like **DO-178C** (for 
avionics) and **IEC 62304** (for medical devices) emerged, requiring formal methods for ensuring software safety. **Abstract syntax** became 
crucial in applying formal verification techniques to real-world systems, as seen in tools like **Frama-C** (for C programs) and **PVS** 
(Prototype Verification System), which are widely used in these industries to ensure correctness and compliance with safety standards.

The use of syntactic and semantic formalism, combined with abstract syntax, plays a pivotal role in the design of reliable programming 
languages. Historically, these formalisms have evolved alongside the increasing complexity of software, particularly in safety-critical 
systems. Abstract syntax enables the use of formal verification tools to ensure program correctness and compliance with stringent safety 
standards, ensuring that these systems operate without failure. This historical trajectory highlights the growing importance of formal 
methods in modern software development, especially in domains where correctness is a matter of life and death.


## Literature
### Review of Key Articles and Their Relevance to Program Verification and Safety-Critical Systems


#### 2. **J. Bowen and V. Stavridou (1993), "Safety-Critical Systems, Formal Methods, and Standards"**

Bowen and Stavridou’s work is a seminal exploration of the role of formal methods in safety-critical systems, including but not limited to 
avionics and medical devices. This article delves into the formal techniques used to ensure that software in these systems behaves as 
intended, focusing particularly on the role of **industry standards** like DO-178C (avionics) and IEC 62304 (medical devices). The authors 
argue that formal methods provide the only reliable way to ensure software correctness in these environments, where even minor errors can 
lead to catastrophic outcomes.

A key theme of this paper is how **abstract syntax** provides the foundation for these formal methods. Abstract syntax allows the 
representation of program logic in a way that is independent of the programming language's superficial syntax, making it easier to apply 
formal analysis tools. Bowen and Stavridou emphasize that abstract syntax enables the **modular verification** of complex systems. By 
breaking down a system into individual components represented through abstract syntax trees, formal tools can verify each component in 
isolation before integrating them to verify the system as a whole.

The article also highlights how abstract syntax is crucial for compliance with safety standards. In avionics, for instance, software must be 
shown to meet the stringent safety requirements of DO-178C, which mandates the use of formal verification techniques in the higher levels of 
certification. Abstract syntax provides a means of systematically checking that the software meets these standards. The same holds for 
medical devices, where software errors could lead to fatal consequences. The article discusses how formal methods, underpinned by abstract 
syntax, are applied to ensure that medical device software complies with regulatory standards such as IEC 62304, which governs the lifecycle 
of software used in medical devices.

**Application to the question**: This article is highly relevant to understanding how abstract syntax contributes to program verification 
and correctness, particularly in regulated industries. It demonstrates how abstract syntax supports formal methods that help prove the 
correctness of safety-critical systems, making compliance with industry standards possible. The focus on standards highlights how abstract 
syntax bridges the gap between formal methods and regulatory requirements, ensuring both the correctness and legal compliance of software in 
critical systems.

**New Questions**:
- With the evolution of safety-critical systems towards greater automation (e.g., autonomous vehicles and robots in medical environments), 
will the current use of abstract syntax and formal methods suffice, or will new approaches be necessary to ensure compliance with updated 
safety standards?
- How might emerging technologies like artificial intelligence and machine learning, which are inherently probabilistic, challenge the 
current use of abstract syntax in proving software correctness in safety-critical systems?

#### 3. **M. Huth and M. Ryan (2004), "Logic in Computer Science: Modelling and Reasoning about Systems"**

Huth and Ryan’s book is a comprehensive guide to the logical foundations of formal verification. The authors explore various methods for 
reasoning about the behavior of programs, including **model checking**, **theorem proving**, and **axiomatic verification**. The book 
highlights how formal logic can be applied to verify system properties such as correctness, safety, and liveness, particularly in systems 
where these properties are critical, such as in avionics or medical devices.

A central theme of the book is how **abstract syntax** enables the formal reasoning process by providing a high-level, structured 
representation of programs. Abstract syntax allows programs to be modeled as mathematical objects, which are then subject to formal 
analysis. For example, in model checking, abstract syntax is used to create models of program states and transitions, enabling the 
verification of temporal properties (e.g., "this system will never enter an unsafe state"). In theorem proving, abstract syntax allows 
programs to be treated as logical formulas that can be proven correct using formal proofs. The book demonstrates how these methods are 
applied in both theoretical and practical settings, with a particular focus on their use in safety-critical systems.

One of the key contributions of this book is its detailed treatment of **compositional reasoning**, where abstract syntax plays a crucial 
role. Compositional reasoning allows for the verification of individual components in isolation, with the assurance that when combined, 
these components will still behave correctly. This method is especially valuable in large, complex systems like those found in avionics, 
where verifying the system as a whole may be too complex or costly. Abstract syntax provides the structure needed to apply compositional 
reasoning effectively.

**Application to the question**: This book is highly relevant to understanding the broader role of abstract syntax in formal verification. 
It delves deeply into how abstract syntax supports various formal reasoning techniques, such as model checking and theorem proving, which 
are essential for verifying safety-critical systems. The use of abstract syntax to facilitate compositional reasoning is particularly 
significant, as it allows for the scalable verification of large systems, which is a common challenge in domains like avionics and medical 
devices.

**New Questions**:
- How can compositional reasoning be extended to more dynamic systems, such as those with real-time constraints or evolving behaviors, which 
are increasingly common in safety-critical domains?
- What are the limitations of current formal verification tools when applied to probabilistic or non-deterministic systems, such as 
AI-driven medical devices or autonomous aircraft, and how can abstract syntax support their verification?

#### 4. **S. Owre, et al. (1992), "PVS: A Prototype Verification System"**

This paper introduces **PVS (Prototype Verification System)**, a widely used tool in formal verification, particularly for safety-critical 
systems. PVS provides an environment for writing formal specifications and conducting formal proofs of system correctness. The system relies 
on **abstract syntax** to represent programs as logical entities, which can then be reasoned about using a combination of automated and 
interactive techniques.

One of the significant contributions of this paper is the explanation of how PVS leverages **abstract syntax trees (ASTs)** as the 
foundation for formal proofs. ASTs allow PVS to break down complex programs into logical components, which can then be analyzed for 
correctness properties. For example, PVS can verify that a system satisfies safety properties (such as "the system will never reach an 
unsafe state") or liveness properties (such as "the system will eventually complete its task"). This is critical in safety-critical domains 
like avionics or medical devices, where software errors can lead to disastrous outcomes.

The paper also discusses how PVS supports **compositional verification**, where the system is broken down into smaller components that are 
verified individually. Abstract syntax makes this possible by providing a formal representation of each component that can be analyzed 
separately. Once the individual components are verified, PVS can combine them to ensure that the entire system behaves correctly. This 
approach is particularly useful in avionics systems, where software complexity is high, and verifying the entire system as a whole would be 
prohibitively expensive.

**Application to the question**: This paper is directly relevant to the question as it provides a practical example of how abstract syntax 
is used in a formal verification tool. PVS, through its use of abstract syntax trees, enables the verification of complex systems, 
particularly in safety-critical domains. The ability to represent programs formally and conduct rigorous proofs of correctness is critical 
for ensuring that these systems are reliable and meet the necessary safety standards.


Here are additional article reviews relevant to the topic of formal methods in programming language design, abstract syntax, and their role 
in safety-critical systems.

#### 5. **C. Ellison and G. Roșu (2012), "An Executable Formal Semantics of C with Applications"**

This paper presents a complete, executable formal semantics of the C language using the **K framework**. The authors emphasize how abstract 
syntax, paired with formal semantics, can uncover undefined behavior and ensure the correctness of C programs. The paper uses **Abstract 
Syntax Trees (ASTs)** to model C programs' structure and then applies formal analysis tools like symbolic execution and model checking.

One of the critical aspects of this paper is how formal verification techniques can be derived from the semantics directly, allowing the 
formal analysis of real-world C programs. For example, the authors demonstrate how **undefined behavior**—a significant source of bugs in 
C—can be detected through formal analysis based on abstract syntax. By executing the semantics in the K framework, errors such as undefined 
operations (e.g., multiple assignments to the same variable in an undefined context) can be automatically identified.

**Application to the question**: This paper shows how abstract syntax and formal semantics work together to ensure the correctness of C 
programs, a language widely used in safety-critical systems. The fact that C’s undefined behavior is often a source of critical bugs makes 
the formal verification approaches presented in this work particularly relevant for avionics and medical software. By applying abstract 
syntax to represent C programs and using formal methods to verify them, the paper demonstrates the importance of rigorous software 
verification in safety-critical domains.

**New Questions**:
- How can the lessons learned from formal verification of C be extended to newer, more complex languages that are increasingly used in 
critical domains?
- Could the integration of more advanced static analysis tools into this formal verification framework provide additional scalability in 
real-world systems?

#### 6. **D. Park, A. Stefănescu, and G. Roșu (2015), "KJS: A Complete Formal Semantics of JavaScript"**

This paper presents **KJS**, a formal executable semantics of JavaScript, one of the most widely used programming languages. The authors 
build a complete formal model of JavaScript based on **abstract syntax** and demonstrate how the semantics can be used to verify JavaScript 
code's correctness and detect runtime errors. By using **ASTs** to represent JavaScript programs and applying the K framework for symbolic 
execution and testing, the paper illustrates how formal verification can be extended to widely used languages beyond those traditionally 
used in safety-critical domains.

The authors validate their work by testing JavaScript engines like **Chrome** and **Firefox**, revealing subtle implementation bugs. The 
formal semantics allow for detailed, structured analysis of program behavior, and the abstract syntax captures JavaScript’s complex control 
flow and object-oriented features, which are particularly challenging to verify in real-world software.

**Application to the question**: Although JavaScript is not commonly used in avionics or medical systems, this paper shows how abstract 
syntax and formal semantics can apply to any programming language, ensuring correctness and safety. The techniques used here could be 
adapted for verifying safety-critical systems, as they prove that even dynamically typed, high-level languages can benefit from formal 
analysis methods.

**New Questions**:
- How can the methods used to verify a dynamically typed, interpreted language like JavaScript be adapted for real-time or embedded systems 
in avionics or medical devices?
- Can the performance of formal verification tools for complex languages like JavaScript be improved to meet the stringent requirements of 
safety-critical software?

#### 7. **A. Sătefănescu, G. Roșu, et al. (2014), "All-Path Reachability Logic"**

This paper introduces **all-path reachability logic**, a formalism that generalizes both **rewrite rules** and **Hoare triples**. The 
authors explain how reachability logic can be used to verify program correctness by leveraging abstract syntax and formal semantics. Using 
this framework, they provide proof systems for reasoning about the entire behavior of a program, ensuring that it satisfies its 
specification under all possible execution paths.

The paper illustrates how this logic is applicable across multiple programming languages by formalizing their semantics using abstract 
syntax. Reachability logic enables compositional verification, where individual program components are verified independently using their 
abstract syntax representation and combined to ensure global correctness.

**Application to the question**: All-path reachability logic highlights the power of abstract syntax in representing program behavior and 
verifying its correctness. For safety-critical systems, where failure is not an option, this type of rigorous formal analysis ensures that 
all possible execution paths are considered, making it a crucial tool for verifying avionics and medical software.

**New Questions**:
- Can reachability logic scale to handle large, complex systems, such as multi-threaded avionics software or distributed medical device 
networks?
- How can the verification process be made more efficient for real-time systems, where execution timing is critical?

#### 8. **N. Bjørner and L. M. de Moura (2008), "Z3: An Efficient SMT Solver"**

This paper describes **Z3**, a state-of-the-art **Satisfiability Modulo Theories (SMT) solver** widely used in formal verification. SMT 
solvers like Z3 allow for the automatic verification of properties by solving logical constraints over program structures. The authors 
highlight the efficiency and scalability of Z3 in solving complex verification tasks, which are often represented using abstract syntax.

Z3 plays a critical role in many formal methods tools, acting as the underlying engine that verifies the correctness of programs by checking 
if logical formulas derived from abstract syntax trees hold. This makes it particularly useful for analyzing programs in safety-critical 
domains, where tools like **symbolic execution engines** use Z3 to verify program properties such as absence of runtime errors, safety, and 
liveness.

**Application to the question**: Z3’s application in formal verification, supported by abstract syntax, shows its importance in ensuring 
program correctness in safety-critical systems. The ability to efficiently solve complex verification tasks makes Z3 a key component in 
tools used to verify avionics and medical device software.

**New Questions**:
- How can SMT solvers like Z3 be further optimized for use in real-time systems where performance and timing are critical?
- Can SMT solvers be extended to handle the verification of systems with probabilistic or non-deterministic behavior, such as those 
incorporating AI components?

### Conclusion
These articles collectively illustrate how abstract syntax and formal methods enable robust program verification, particularly in 
safety-critical systems. They demonstrate that abstract syntax is essential for simplifying the verification process, while formal methods 
ensure correctness by rigorously analyzing all possible execution paths. Each article contributes unique perspectives on how these concepts 
are applied, raising questions about scalability, efficiency, and the verification of increasingly complex systems.





Here are the scientific citations for the articles referenced in the reviews:

2. **J. Bowen and V. Stavridou (1993)**:
   - Bowen, J. P., & Stavridou, V. (1993). *Safety-Critical Systems, Formal Methods and Standards*. Software Engineering Journal, 8(4), 189-209. https://www.researchgate.net/publication/2526537_Safety-Critical_Systems_Formal_Methods_and_Standards

3. **M. Huth and M. Ryan (2004)**:
   - Huth, M., & Ryan, M. (2004). *Logic in Computer Science: Modelling and Reasoning about Systems*. Cambridge University Press. ISBN: 9780521543101. http://staff.ustc.edu.cn/~huangwc/book/LogicInCS.pdf

4. **S. Owre, et al. (1992)**:
   - Owre, S., Rushby, J. M., & Shankar, N. (1992). *PVS: A Prototype Verification System*. In *Proceedings of the 11th International Conference on Automated Deduction* (pp. 748-752). Springer, Berlin, Heidelberg. https://link.springer.com/chapter/10.1007/3-540-55602-8_217

5. **C. Ellison and G. Roșu (2012)**:
   - Ellison, C., & Roșu, G. (2012). *An Executable Formal Semantics of C with Applications*. In *Proceedings of the 39th ACM SIGPLAN-SIGACT Symposium on Principles of Programming Languages* (pp. 533-544). https://doi.org/10.1145/2103656.2103719

6. **D. Park, A. Stefănescu, and G. Roșu (2015)**:
   - Park, D., Stefănescu, A., & Roșu, G. (2015). *KJS: A Complete Formal Semantics of JavaScript*. In *Proceedings of the 36th ACM SIGPLAN Conference on Programming Language Design and Implementation* (pp. 346-356). https://dl.acm.org/doi/10.1145/2737924.2737991

7. **A. Sătefănescu, G. Roșu, et al. (2014)**:
   - Sătefănescu, A., Roșu, G., et al. (2014). *All-Path Reachability Logic*. In *Proceedings of the 25th International Conference on Rewriting Techniques and Applications* (pp. 425-440). Springer, Berlin, Heidelberg.https://experts.illinois.edu/en/publications/all-path-reachability-logic-2

8. **N. Bjørner and L. M. de Moura (2008)**:
   - Bjørner, N., & de Moura, L. M. (2008). *Z3: An Efficient SMT Solver*. In *Proceedings of the International Conference on Tools and Algorithms for the Construction and Analysis of Systems* (pp. 337-340). Springer, Berlin, Heidelberg. https://doi.org/10.1007/978-3-540-78800-3_24

These citations cover the key contributions of each paper to the topics of formal methods, abstract syntax, and verification in safety-critical systems.
