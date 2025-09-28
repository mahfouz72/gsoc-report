# Google Summer of Code 2025 Final Report

### **Project**: [New ANTLR Grammar for Javadoc Comments](https://github.com/checkstyle/checkstyle/wiki/Checkstyle-GSoC-2025-Project-Ideas#project-name-new-antlr-grammar-for-javadoc-comments)

### **Student**: [Mohamed Mahfouz](https://github.com/mahfouz72)

### **Organisation**: [Checkstyle](https://github.com/checkstyle)

### **Mentors**: [Nick Mancuso](https://github.com/nrmancuso)

---
### Project Goals

This project aimed to create a modern, grammar-based parser for Javadoc comments using [ANTLR](https://www.antlr.org/).
The existing parser had become increasingly difficult to maintain and extend as Javadoc syntax evolved,
and it also suffered from performance issues. The goal was to replace it with a cleaner and more flexible grammar
that future developers could more easily maintain and enhance.
Another key objective was to make it possible to extend the grammar safely and efficiently, without introducing performance risks and degradation.
In addition, the project aimed to integrate the new parser into Checkstyle’s APIs
and adapt all Javadoc-related checks to work properly with the new AST structure.

---
### What I Did During GSoC

The work on this project was completed in three main phases.

#### Phase 1: Lexer and Parser Development
I began by building the foundation of the new Javadoc parser in a [separate repository](https://github.com/checkstyle-GSoC25/javadoc-parser).
This involved creating a base ANTLR lexer and parser to define the grammar for Javadoc comments.
The main focus in this phase was to produce a correct parse tree, independent of Checkstyle’s AST,
in order to decouple parsing from AST construction and introduce a clean layer of abstraction.
This separation simplified the overall architecture and allowed us to write a much cleaner and maintainable grammar, 
since the grammar only needed to model the Javadoc specification itself rather than being constrained by Checkstyle’s internal AST requirements.
We also placed a strong emphasis on testing to ensure the grammar behaved correctly and to catch regressions early.

By the end of this phase, the grammar was able to correctly recognize and parse the full range of Javadoc
tags and HTML elements, and we ensured full coverage of the [Javadoc Specification](https://docs.oracle.com/en/java/javase/22/docs/specs/javadoc/doc-comment-spec.html)

#### Phase 2: AST Construction and Integration

After stabilizing the grammar, the work moved into Checkstyle’s main repository.
In this phase, I worked on my fork, where I implemented an AST construction layer using the visitor pattern
to convert the raw ANTLR parse tree into Checkstyle’s internal AST representation.
Once this layer was complete, I integrated the new parser with Checkstyle’s core APIs
so that it could function as a replacement for the legacy parser.
I also added dedicated AST test files to validate the correctness of the new AST
and to cover interesting edge cases, helping ensure future regressions are caught early.

#### Phase 3: Updating Javadoc Checks

The final phase focused on updating Checkstyle’s checks to work with the new Javadoc parser.
This included both user-facing checks and the `AbstractJavadocCheck` subclasses used internally for shared functionality.
Each check was reviewed and adapted to the new AST structure.

To validate these changes, we ran regression testing reports across large projects.
The results showed some differences, but these were mainly due to expected difference in parsing behaviour,
not unintended breakages. This process gave us confidence that the migration preserved correctness
while delivering a cleaner and more reliable parsing model.

After completing all three phases, I prepared and submitted a single final pull request to Checkstyle’s main repository,
containing all of these changes for review and integration.

---

### Current Status and Future Work

All planned functional changes for the new Javadoc parser have been completed. 
The main pull request from my fork to Checkstyle’s main repository is ready,
with only minor adjustments needed to address CI issues and review feedback. 
Because the changes are large and fundamental, the review process may require iterations to ensure stability
and avoid unintended regressions.

At this point, the parser is stable, well-tested, and designed with long-term maintainability in mind.
This means that Checkstyle now has a strong foundation for handling Javadoc consistently,
without the performance and maintainability bottlenecks.

Looking ahead, the next step is to begin migrating all existing regex-based Javadoc checks to become AST-based. 
This will make the checks more reliable, and easier to maintain.

---

### Code Contributions

- All PRs related to phase 1 can be found [here](https://github.com/checkstyle-GSoC25/javadoc-parser/pulls?q=is%3Apr+is%3Aclosed),
  where we built the base ANTLR lexer and parser and ensured full Javadoc specification coverage in separate repo.
- PR related to phase 2 can be found [here](https://github.com/checkstyle-GSoC25/checkstyle/pull/22),
  where we implemented the AST construction layer using visitor patter.
- All PRs related to phase 3 can be found [here](https://github.com/checkstyle-GSoC25/checkstyle/pulls?q=is%3Apr+is%3Aclosed),
  where we updated all Javadoc checks to work with the new parser and do full integration with checkstyle APIs.
- Final PR to the main repository can be found [here](https://github.com/checkstyle/checkstyle/pull/17837).

---

### What I Learned During GSoC

I gained a number of important skills and insights:
- **Grammar design**: 
  - I learned how to design and implement a full lexer and parser using ANTLR including handling a real-world specification like Javadoc.
  - I learned how to build an AST construction layer using the visitor pattern, and how decoupling parsing from AST building leads to cleaner and more maintainable code.
- **Integration with existing systems**: I gained experience integrating large-scale changes into a large open-source project while preserving backward compatibility.
- **Project management and execution**: Improved my ability to break down a large, complex project into smaller phases and deliverables, moving systematically from grammar definition to integration and final migration.

---

### Acknowledgements
I want to thank my mentor, [Nick](https://github.com/nrmancuso), for all his support since day one of my journey with Checkstyle.
His guidance and experience made a huge difference, helping me get through the tricky parts of this project
and teaching me how to think about problems in new ways. A big thanks as well to [Richard](https://github.com/rnveach),
even though he was not an official mentor, he still helped us a lot and I really appreciate it.
And finally, thanks to [Roman Ivanov](https://github.com/romani), our org admin, for trusting me and giving me the chance to work on this project.