# Specification for Project 7 Applied Data Analytics

## Overview

Project 7 is a chance to explore applied data analytics, offering a preliminary introduction to more advanced topics in the field.
This project offers a guided introduction to several key areas in data analytics. It's an opportunity to apply your skills and try an area that you might enjoy.  Many of these areas are covered in more depth in subsequent courses.

You have the flexibility to choose from several application areas, each offering a glimpse into different aspects of data analytics:

1. ML. Basic Machine Learning (ML): Explore fundamental ML concepts using Python's statistical and visualization libraries with simple linear regression and predictive analytics.

1. App. Interactive Analytics App using Shiny for Python: Get introduced to creating interactive web applications with Shiny for Python. This choice focuses on building basic interactive tools for data analysis.

Later (or propose a project):

1. SQL. Applied SQL Project: Engage in an applied SQL project integrating Python and SQLite. This option focuses on database interactions and SQL for data manipulation and querying.

1. NLP. Web Mining and Natural Language Processing (NLP): Delve into the basics of web mining and NLP using Python's NLTK library. This area will allow you to explore text processing and extraction of information from web sources.


Each of these areas represents a critical component of data analytics, and this project guides you through applying these concepts in a practical setting.
The goal is not mastery; it's to gain a basic understanding and appreciation of their role and potential in the field of data analytics and learn where you might want to focus your efforts in the future.

The specification is similar to early projects, but you'll need to tailor it to your chosen area.

1. Will you use a Jupyter Notebook or a Python script?
2. What tools and libraries will you use?
3. What dependencies will you need to install in your project virtual environment?
4. How will you organize your project?
5. How will you manage your project with Git?
6. How will you document your tools, process, code, and project?

## Deliverable Names

- GitHub Repository:  datafun-07-applied
- Documentation:      README.md
- Source:             yourname_applied.py or yourname_applied.ipynb

Create a new GitHub repository with a README.md and a code file with the specified name.

### Version Control with Git

Use Git for version control.
Document your workflow for managing the project in your README.md.

## Module Specification

### Objective

Explore an area of applied data analytics.
Incorporate logging to document the process and provide feedback.

### Requirements

#### 1. Environment Setup

1. Create and activate a project virtual environment.
1. Install all required packages into your local project virtual environment.
1. After installing the required dependencies, generate a requirements.txt file.
1. Document the process and commands you used in your README.md.
1. Add a .gitignore file to your project with useful entries.

#### 2. Project Start

1. Create a docstring or markdown cell with a brief introduction to your project.
1. Include the usual introduction information.

#### 3. Import Dependencies

Import the required dependencies, following the conventional order.

#### 4. Logging

Logging is recommended for all script and notebook projects.
Implement logging to enhance debugging and maintain a record of program execution.

1. Configure logging to write to a file named log.txt.
1. Log the start of the program using logging.info().
1. Log the end of the program using logging.info().
1. Log exceptions using logging.exception().
1. Log other major events using logging.info().
1. Log the start and end of major functions using logging.debug().

#### 5. Sections based on your choice of Applied Data Analytics

Choose the sections for this area depending on your choice
and the specification details provided in their own document:

1. [Intro to Machine Learning](ML.md)
1. [Intro to Interactive Apps](APP.md)

For some, you might want a notebooks, and for some, a script might be better.
Some need data acquisition and others build a database schema.
Some build machine learning models, and some build an interactive app.
Some (notebooks) can show execution in GitHub, others may need screenshots in the README.md.

Making good tool and process decisions is critical for professional data analysts.

### Code Design

- Begin your code file with a summary including the title, author, date, and project's purpose. This provides an immediate understanding of the code file objective.
- Ensure your code and presentation are neat, well-organized, and follow good coding practices. This includes proper variable naming, consistent code style, and logical organization of code cells.
- Format your code using comments or Markdown features to enhance readability.

### Code Structure and Documentation

Once the code runs without errors, focus on how the content is structured and documented.
Organize your code into well-defined sections, each with a clear purpose and header.
Provide context, explain your analysis, and share findings.
Make your code file informative and engaging.
Use comments and text to explain the purpose and functionality of the code, especially complex or non-obvious code segments.

### Code Execution

Run your code to ensure it executes without errors.
Verify all code runs and visualizations render as expected.
Confirm that your code renders well on GitHub, so your work is accessible to others.

If working in a script, use conditional logic to ensure the script only runs
when executed directly and execute a main() function that contains the program logic.

### Evaluation Criteria

- Functionality: The project should be functional and meet all requirements.
- Documentation: The project should be well-written and well-documented.
- Presentation: The project should be presented in a clear and organized manner.
- Professionalism: The project should be submitted on-time and reflect an original, creative effort.

See rubric for additional information.
