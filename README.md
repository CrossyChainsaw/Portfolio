# Portfolio Semester 3 - Kaan Gögcay

image of all products

## Table of contents
 - [Preface](#preface)
 - [Products](#products)
   - [Reverse Hangman Online](#reverse-hangman-online)
     - [Learning Outcome 1: Web Application (IP)](#learning-outcome-1-web-application-ip)
     - [Learning Outcome 2: Software Quality](#learning-outcome-2-software-quality)
     - [Learning Outcome 4: CI/CD](#learning-outcome-4-cicd)
     - [Learning Outcome 8: Professional (IP)](#learning-outcome-8-professional-ip)
   - [Restaurant Ordering System](#restaurant-ordering-system)
     - [Learning Outcome 1](#learning-outcome-1-gp)
     - [Learning Outcome 3](#learning-outcome-3)
     - [Learning Outcome 5](#learning-outcome-5)
     - [Learning Outcome 6](#learning-outcome-6)
     - [Learning Outcome 7](#learning-outcome-7)
     - [Learning Outcome 8](#learning-outcome-8-gp)
 - [Research](#research)
   - [How do I create a fair but challenging bot for my game?](#how-do-i-create-a-fair-but-challenging-bot-for-my-game)
   - [Which database fits my application the best?](#which-database-fits-my-application-the-best)

# Preface
Whilest reading you might encounter certain terms like IP, GP and S3, these refer to the terms Individual Project, Group Project and Semester 3 respectively. I'll start with showing all products I made this semester and then we'll go into the researches I did. Nothing else to add, have fun reading.

# Products
This semester I had to realise all the learning outcomes of semester 3. Per product I will explain how i realised the corresponding learning outcome. Here's a list with all the learning outcomes. I'll also include a list of requirements I have to realise this semester in my individual project.

[Learning Outcomes S3](https://fhict.instructure.com/courses/12078/outcomes)

[List of requirements Individual Project](https://fhict.instructure.com/courses/12078/pages/what-should-be-covered-in-my-individual-project?module_item_id=749928)

# Reverse Hangman Online
Reverse Hangman Online is a game I made for my individual project. I will explain per learning outcome how I realised it with my individual project. Everthing about Reverse Hangman Online itself can be found in its documentation.

[Reverse Hangman Online Documentation](https://github.com/Epic-Chainsaw-Massacre)

## Learning Outcome 1: Web Application (IP)
*You design and build **user-friendly**, **full-stack** web applications.*

Clarification:

**User friendly**: You apply basic User experience testing and development techniques.

**Full-stack**: You design and build a full stack application using commonly accepted front end (Javascript-based framework) and back end techniques (e.g. Object Relational Mapping) choosing and implementing relevant communication protocols and addressing asynchronous communication issues.

### Front-end
The front-end has been made in React-TypeScript.

[Reverse-Hangman-Online-Frontend](https://github.com/Epic-Chainsaw-Massacre/reverse-hangman-online-frontend)

### Back-end
The back-end has partially been made in C# .Net and partially in Java Spring.

[Reverse-Hangman-Online-Backend](https://github.com/Epic-Chainsaw-Massacre/reverse-hangman-online-backend)

### UX-Testing
I sadly haven't been able to do user experience testing since my application wasn't done yet. So I couldn't let someone test it. Parts of my application were done quite early but the game itself wasn't.

## Learning Outcome 2: Software Quality
*You use software **tooling and methodology** that continuously monitors and improve the software quality during software development.*

Clarification:

**Tooling and methodology**: Carry out, monitor and report on unit integration, regression and system tests, with attention for security and performance aspects, as well as applying static code analysis and code reviews.

### Testing
blank

### Static Code Analysis
blank

### Code Reviews
blank

## Learning Outcome 4: CI/CD
*You **design and implement** a (semi)automated software release process that matches the needs of the project context.*

Clarification:

**Design and implement**: You design a release process and implement a continuous integration and deployment solution (using e.g. Gitlab CI and Docker).

### Continous Integration
In my front-end and my back-end I've setup a ci pipeline. The pipeline build my application and runs all the unit tests I've written. I did all of this using the github actions section. Github actions provides lots of templates which make it very easy to setup a pipeline. For my front-end and back-end I used a Node.js and a .NET template respectively. 

[Reverse Hangman Online Frontend CI](https://github.com/Epic-Chainsaw-Massacre/reverse-hangman-online-frontend/actions/workflows/node.js.yml)

[Reverse Hangman Online Backend CI](https://github.com/Epic-Chainsaw-Massacre/reverse-hangman-online-backend/actions/workflows/dotnet.yml)

### Continous Deployment
blank

## Learning Outcome 8: Professional (IP)
*You act in a **professional manner** during software development and learning.*

Clarification:

**Professional manner**: You actively ask and apply feedback from stakeholders and advise them on the most optimal technical and design (architectural) solutions.
You choose and substantiate solutions for a given problem.

### Feedback
This semester started off with [Leon van Bokhorst](https://github.com/leonvanbokhorst). I asked him weekly feedback, sadly you won't be able to find it all back in my FeedPulse PDF Report, since sometimes my teacher forgot to open a feedpulse session. Leon has motivated me a lot troughout the semester, and definitely turned this boring documentation focussed semester into a fun semester. Later in the semester, the last 3 weeks, i got 2 new teachers, [Jean-Paul Ligthart](https://github.com/jpligthart) and [Timo Hermans](https://github.com/timohermans). I also tried to speak both of them once a week.

blank v
[FeedPulse PDF Report](#blank)

# Restaurant Ordering System
The Restaurant Ordering System was my group project this semester. I made it together with [Mike van den Hoef](https://github.com/Headoros), [Tim Meijvogel](https://github.com/Timsel1), [Cas Esselink](https://github.com/CasEsselink) and [David Chang](https://github.com/Davidchang24). Everything about our Group Project can be found at it's documentation

blank v
[Restaurant Ordering System](#blank)

## Learning Outcome 1 (GP)
*You design and build **user-friendly**, **full-stack** web applications.*

Clarification:

**User friendly**: You apply basic User experience testing and development techniques.

**Full-stack**: You design and build a full stack application using commonly accepted front end (Javascript-based framework) and back end techniques (e.g. Object Relational Mapping) choosing and implementing relevant communication protocols and addressing asynchronous communication issues.

### Front-end
The front-ends has been mainly made by Me, Mike, Tim and David. We coded it in React-TypeScript. Me and David worked on the same repo, Tim had its own and Mike also had its own. We had different repositories since we used a microservice structure.

### Back-end
The application has multiple backends. The backends have been made by Me, Mike, David and Cas. The only language we used in our backend is Java. Me and David worked on the same backend. After a while when me and David got some processes working between the front-end and back-end we decided that I would mainly focus on the front-end and he would focus on the back-end, since it was pretty annoying to both work on both. But on the other hand, since we've setup everything together we both exactly knew how each others' application worked.

# Research

## Which database fits my application the best?
For this research I made use of the [DOT framework](https://ictresearchmethods.nl/The_DOT_Framework).

**What**: I want to research which database fit my application the best.

**Why**: Instead of choosing a random database, I'd like to know which database fits my application the best. Because if you realize you chose the wrong database in the middle of the project it might cost a lot of time, effort and money(for a company, I'm just a student).

**How**: Find multiple articles about how to choose the right database for your application, validate them, and use them for my project.


