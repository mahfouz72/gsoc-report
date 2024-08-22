# Google Summer of Code 2024 Final Report

### **Project**: [Java 21 Language Feature Support](https://github.com/checkstyle/checkstyle/wiki/Checkstyle-GSoC-2024-Project-Ideas#project-name-java-21-language-features-support)

### **Student**: [Mohamed Mahfouz](https://github.com/mahfouz72)

### **Organisation**: [Checkstyle](https://github.com/checkstyle)

### **Mentors**: [Richard Veach](https://github.com/rnveach), [Nick Mancuso](https://github.com/nrmancuso)

---
### Project Goals

The project aimed to modernize [Checkstyle](https://github.com/checkstyle/checkstyle),
a static code analysis tool, by supporting Java 21 language features.
By updating existing checks, creating new ones, and establishing a sustainable process for
the evolution of Checkstyle itself, we aimed to ensure that Checkstyle stays relevant
in the Java community for years to come.
We also wanted to lay the groundwork for a cultural shift in the Checkstyle community, 
transforming the existing reactive development model to a proactive model where the Checkstyle
community establishes best practices and takes the lead in creating new ways to improve code quality.

---

### What I Did During GSoC

1. **Development of an Analytical Model for New Language Features Integration Process**:
   I began by designing a process to systematically identify which existing checks require updates
   and where new checks need to be implemented to support new Java language features.
   This guide titled "[New Language Feature Check Integration Process](https://github.com/checkstyle/checkstyle/blob/master/docs/NEW_LANGUAGE_FEATURE_INTEGRATION_PROCESS.md)"
   serves as foundation for the planning and scoping the work required to support new language features.
2. **Planning and Scoping**: Using the analytical model that was done in the first phase, 
   we defined the work required to support Java 21 language features.
   We identified the checks that need to be updated and the new checks that need to be implemented.
3. **Implementation of Identified Changes**: We implemented the changes identified by our model, which included:
   - **Update Existing Checks**: I updated existing checks to support new language features and 
   ensure that checks don't produce false negatives or positives when encounter code that uses new Java language features.
   - **New Check Implementation**: Where existing checks were insufficient, new checks were developed to cover the new
   language constructs to ensure developers can enforce coding standards for Java 21.
   - **Extending Test Cases With New Language Features**: I added new unit tests 
   to verify as well as document the behavior of checks when dealing with the new language features.
   - **Updating Documentation**: I updated Checkstyle documentation to reflect the
   changes made. This included descriptions of how the new and updated checks work, as well as usage examples
   to help developers leverage these checks effectively.

---

### Current Status and Future Work

The project is currently in a stable state, with the majority of the planned updates and new checks implemented.
However, there are several areas for future enhancements:

- **Implementation of the Remaining New Checks**: [Some new checks](https://github.com/checkstyle/checkstyle/issues?q=is%3Aopen+is%3Aissue+author%3Amahfouz72+label%3A%22new+module%22) 
  remain unimplemented. Completing these checks will further enhance Checkstyle’s support for new Java language features.
- **Refinements to Our Model**: Introduce more effective methods for analyzing the impact of new language features on existing checks. 
  We can also provide a broader range of examples for each section of the process.
- **Templates for Analysis**: Develop templates to standardize the analysis process for integrating new language features.
- **Automate some parts of the update process**: Explore the development of advanced tools. These tools could automatically identify similar tokens,
  suggest new checks, and generate reports with insights drawn from AST analysis.
- **Other Ambitious Pursuits**: Consider additional ambitious goals such as exploring machine learning techniques for predicting required updates
  by training a model on historical data of language feature updates.
  The model could analyze patterns in how new language features have impacted checks in the past.

---

### Code Contributions
- All PRs related to the project can be found [here](https://github.com/checkstyle/checkstyle/pulls/mahfouz72?q=is%3Aopen%20is%3Apr%20author%3Amahfouz72%20project%3Acheckstyle%2F6).
- All PRs/Issues related to the project can be found in [GitHub project board](https://github.com/orgs/checkstyle/projects/6).
- All PRs related to updating existing checks can be found [here](https://github.com/checkstyle/checkstyle/pulls?q=is%3Apr+project%3Acheckstyle%2F6+NOT+%22input%22+NOT+%22new+check%22+in%3Atitle+).
- All PRs related to new checks can be found [here](https://github.com/checkstyle/checkstyle/pulls?q=is%3Apr+project%3Acheckstyle%2F6+%22new+check%22+in%3Atitle).
- All PRs related to extending test cases can be found [here](https://github.com/checkstyle/checkstyle/pulls?q=is%3Apr+project%3Acheckstyle%2F6+%22new+input%22+in%3Atitle+).
- My work on this project is part of Checkstyle 10.18.0 release.
  The release notes can be found [here](https://checkstyle.org/releasenotes.html#Release_10.18.0).
- All my contributions to checkstyle can be found [here](https://github.com/checkstyle/checkstyle/pulls/mahfouz72).

---

### What I Learned During GSoC

#### Technical Skills: 

- **Static Code Analysis**: I have developed a good understanding of static code analysis.
  I’ve learned how we generate grammar using ANTLR. We employ the visitor design pattern to traverse the parse tree
  and build the AST, which is then used to perform static code analysis.
- **Code Quality**: Working on Checkstyle has improved my ability to write clean and maintainable code
  by enforcing high coding standards through tools like Checkstyle itself, PMD, IDEA inspections, and SpotBugs.
  My contribution involved more than just using these tools. I, through an analytic process,
  established new best practices by designing and implementing code quality tools.
- **Software Testing**: Checkstyle use JaCoCo for code coverage metrics and PIT for mutation testing.
  With Checkstyle's strict policy of requiring 100% code coverage and zero surviving mutations,
  I’ve learned the critical value of writing effective tests.
- **Participating in Design Reviews**: I participated in design reviews focused on the development of new static code analysis
  checks for Checkstyle. Collaborated with mentors to evaluate the design of these checks and 
  deciding on the best approaches for implementation.


#### Non-Technical Skills:

- **Project Management**: We dedicated almost a month to thoroughly plan and organize the project.
  During this time, we outlined the project’s scope and defined objectives. We opened detailed tracker issues
  for each language feature. This process involved breaking down larger tasks into manageable issues and documenting requirements.
  We organized the work by prioritizing tasks based on their importance.
  For example, we decided to tackle false positives first. All of this was done before coding began allowed
  us to have a clear roadmap and a well-defined scope.
- **Effective Communication**: I developed strong communication skills, including how to effectively interact
  with mentors and handle disagreements in asynchronous communication environments.
- **Analytic Framework Development**: I developed an analytic framework for integrating new language features into Checkstyle.
  This achievement not only highlights my ability to design practical methods for analyzing new language features
  but also improved my technical writing skills.

The growth I've experienced in these areas is just as significant as the technical skills I developed. 
My initial expectations when writing the proposal focused primarily on coding, but I now realize that the ability
to manage projects effectively, communicate clearly, and discipline are the qualities that will set me apart
in my career. This summer has been an invaluable learning experience, not just in terms of coding,
but in understanding what it takes to be successful in the tech industry.

---

### Acknowledgements

I am very grateful to my mentors [Nick Mancuso](https://github.com/nrmancuso) and [Richard Veach](https://github.com/rnveach)
for their guidance and support throughout the project and for providing me with such amazing opportunity to learn and grow.
I would also want to thank [Roman Ivanov](https://github.com/romani) for his continuous guidance.
I am looking forward to keep on contributing to this project and working with the Checkstyle community.
