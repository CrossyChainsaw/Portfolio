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
     - [Learning Outcome 1: Web Application (GP)](#learning-outcome-1-web-application-gp)
     - [Learning Outcome 3: Agile Method](#learning-outcome-3-agile-method)
     - [Learning Outcome 5: Cultural Differences and Ethics](#learning-outcome-5-cultural-differences-and-ethics)
     - [Learning Outcome 6: Requirements and Design](#learning-outcome-6-requirements-and-design)
     - [Learning Outcome 7: Business processes](#learning-outcome-7-business-processes)
     - [Learning Outcome 8: Professional (GP)](#learning-outcome-8-professional-gp)
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

[Restaurant Ordering System Documentation](https://github.com/fontys-group3)

## Learning Outcome 1: Web Application (GP)
*You design and build **user-friendly**, **full-stack** web applications.*

Clarification:

**User friendly**: You apply basic User experience testing and development techniques.

**Full-stack**: You design and build a full stack application using commonly accepted front end (Javascript-based framework) and back end techniques (e.g. Object Relational Mapping) choosing and implementing relevant communication protocols and addressing asynchronous communication issues.

### Front-end
The front-ends has been mainly made by Me, Mike, Tim and David. We coded it in React-TypeScript. Me and David worked on the same repo, Tim had its own and Mike also had its own. We had different repositories since we used a microservice structure.

### Back-end
The application has multiple backends. The backends have been made by Me, Mike, David and Cas. The only language we used in our backend is Java. Me and David worked on the same backend. After a while when me and David got some processes working between the front-end and back-end we decided that I would mainly focus on the front-end and he would focus on the back-end, since it was pretty annoying to both work on both. But on the other hand, since we've setup everything together we both exactly knew how each others' application worked.

### UX-Testing
We haven't done UX-Testing in our group project.

## Learning Outcome 3: Agile Method (GP)
*You can implement the software process for your project according to a given agile software development method.*

Clarification:

**Agile** method: You are aware of most popular agile methods and their underlying agile principles. You are able to implement the process of your software project according to a chosen methodology.

### Scrum
For our group project we used the agile method scrum. This means we have one scrummaster every sprint. The scrummaster would lead the standups and standdowns. Furthermore the scrummaster in our project didn't have too much meaning. For example, usually the contact person in the group is the scrummaster. But we found it easier to make that role static and give it to a groupmember (me). It kinda felt like we were all the scrummaster, this way of working didn't really give any problems.

## Cultural Differences and Ethics
*You **recognize** and **take into account** cultural differences when working with multi-site teams and are aware of ethical aspects in software development.*

Clarification:

**Recognize**:  Recognition is based on theoretically substantiated awareness of cultural differences and ethical aspects in software engineering.

**Take into account**: Adapt your communication, working, and behavior styles to work with other developers from different cultures; 
Address one of the standard Programming Ethical Guidelines (e.g., ACM Code of Ethics and Professional Conduct) in your work.  

### Coding Together
We didn't have very strict coding standards in our team. We did have one rule and that is to code everything in english. 

If multiple people worked on one repository we made branches and push the branches to github. finally we merge them to the master. Working like this we avoid pushing our code to the master branch which could be very fatal.

## Learning Outcome 6: Requirements and Design
*You translate (non-functional) requirements to extend existing (architectural) designs and can validate them using **multiple types of test techniques**.*

Clarification:

**Multiple types of test techniques**: You apply user acceptance testing and stakeholder feedback to validate the quality of the requirements. You evaluate the quality of the design (e.g., by testing or prototyping) taking into account the formulated quality properties like security and performance.

### Quality Requirements
Before we started coding, we showed our user stories to the stakeholders. When they agreed to the user stories we started working on them. In a sprint delivery we didn't only deliver all our products but also did we show our stakeholder which user stories we would work on next sprint. This is very good to do since if they don't like a part of a user story or the priority of a user story they tell it us. Sadly we don't have footage of the stakeholders giving us feedback, but we do have the minutes of every meeting. Here are some example of feedback we wrote down during meetings/sprint deliveries.

In blue you can see their feedback on all our user stories. Since it's a lot i'll translate a few. *add the user story that adds the functionality to place an order*, *user story 12 'actions' isn't clear for us, and what do you guys consider as a mistake?*, *in lots of user stories you guys use the format 'bla bla because bla bla' , you guys can leave away the because if it's not necesary.* 
![image](https://user-images.githubusercontent.com/74303221/173034408-4500e704-bafe-476f-a42b-fa1a3fadbe93.png)

In blue it says, *It's not important to focus on the paying process*, underneath the blue sentence they gave us advice on fuctionalities they would like to see instead, for example, *Make it impossible for outsiders to reach our website*, *saving a session to the backend*, *show all orders in the managment portal* and *completing an order*.
![image](https://user-images.githubusercontent.com/74303221/173032795-1fd22516-dc6e-421c-824a-2c7d2a544552.png)

### Security and Performance
We had a few security issues in our project. For example, its possible to place an order, eat your food, remove your cookies on the browser. and it doesn't say you have to pay anymore. Our solution for this would be to save the cookies in the backend. At this moment we only save it in the frontend. Another security flaw is that it's possible to place an order while you aren't even near the restaurant. We wanted to solve this problem by making it impossible to reach the url if you are on a different IP, but that required wifi. And using a restaurant wifi isn't the most user friendly solution. so for this flaw we didn't find an solution yet. Sadly we ran out of time to build the functionalities.

## Learning Outcome 7: Business processes
*You can explain **simple** business processes and **relate** them to the development of your software project.*

Clarification:

**Simple**: predominantly sequential processes with one or two alternative paths.

**Relate**: understanding the relationships between the process and software.

### Ordering Process
In our business process we visualized the entire process of making an order digital and analog. You see 3 phases in this process, these are placing the order, prepare the order and finishing the order. Let's go through 2 quick examples. 

### Analog
John enters the restaurant and takes a seat. Now the ordering process takes place. In the order process John orders a burger and a coke. The waiter writes it all down and brings the order to the kitchen and bar. This is where the preparing phase starts. The kitchen makes a burger and the bar prepares a coke. When everything is prepared, the waiter takes it to John's table. If John is done dining, the ending phase starts. In this phase the cashier types in the amount of money John has to pay. John pays for the food. If John gave too much money he also gets his change from the cashier. Now the cashier asks John if he wants the receipt. John decides he wants the receipt, and leaves the restaurant.

### Digital
John enters the restaurant and takes a seat and scans the QR code to open up the menu. Here the process of ordering will start. John clicks on a burger and a coke, and places the order. Now the preparing phase starts. Kitchen and bar employee claim the burger and the coke in their interface respectively. When both are ready to serve, they drag the order to done in their interface. Then the waiter gets the order and serves it out to John. If John is done eating, the ending phase starts. He gets an invoice to his phone, after paying he can choose if he wants the receipt and he's free to go.

### Key Differences
Lets go through the biggest differences between analog versus digital together. 

#### Ordering
When ordering analog the waiter can accidentally write down an order wrong just because he misunderstood the customer. When done digitally, the cusomter chooses what he wants to eat using software. Before ordering you can double check everything what you've selected. After placing the order the waiter brings it to the kitchen and bar, this could also go wrong in multiple ways. The waiter might have to help a customer on its way to the kitchen or the bar. also can he mix up what has to go to the bar and what has to go to the kitchen. Digitally this all goes automatic.

#### Preparing the order
In an analog situation, the order comes in and the employee takes the order and prepares it. This is very simular to how it would go digitally. When using our software you replace the paper with technology.

#### Payement
In an analog situation you have to go to the checkout. Here they get your bill, and type it in on the cash register. Digitally you can just stay on your place, pay and leave. The cashier could possibly give you the wrong bill giving a bad cumstomer experience. When paying digital, this can't occur.

*Business process for making an order*
![image](https://user-images.githubusercontent.com/74303221/173024638-a51d2346-4b31-43a5-b7ad-1ce023b01e67.png)


## Learning Outcome 8: Professional (GP)
*You act in a **professional manner** during software development and learning.*

Clarification:

**Professional manner**: You develop software as a team effort according to a prescribed software methodology and following team agreements. You are able to track your work progress and communicate your progress with the team. You actively ask and apply feedback from stakeholders and advise them on the most optimal technical and design (architectural) solutions. You choose and substantiate solutions for a given problem.

### Team Communication
Inside our group we used Teams and Discord to communicate. We started off in Teams, but after a while we only used the Teams for files and we permanently switched to Discord. In our group project we had a few set of rules about presence.

*Rules of Presence*
![image](https://user-images.githubusercontent.com/74303221/172949644-04301849-de14-4ae8-b7b8-f988d8f2ef1b.png)

For the English readers, this says. *Be present at 09:00, after 09:10 you will be considered as late, if you know you will be late let us know 1 day before. If you don't let us know anything, you are late and you don't have a valid reason to be late, we give you a strike. All the rules that apply to being to late also apply to not showing up at all. If you get you're third strike we inform the teacher about your presence. 

Always if i knew i would be late i let my group know but to prove it here are some messages of me letting my group know i will be too late.

![image](https://user-images.githubusercontent.com/74303221/172952242-3fc00baa-3ed7-4e82-8ae6-3f1f81da832b.png)
![image](https://user-images.githubusercontent.com/74303221/172952188-a35c89c3-2e90-468e-9be0-0e4e525bf3b3.png)
![image](https://user-images.githubusercontent.com/74303221/172952157-a3bf6c8e-2f65-412a-8499-e911c2bad0e0.png)
![image](https://user-images.githubusercontent.com/74303221/172952128-d5dea735-1c1e-4233-a8c6-55e5a5ed2a42.png)
![image](https://user-images.githubusercontent.com/74303221/172952108-61ab7cb4-30cf-45f9-82ee-94bb2c2578d0.png)

Again for the English readers, these are just messages like, *I will be x minutes later, I gotta go to the family doctor, I had a bloody nose so I will be later.*

### Communication with the Stakeholders
Not only is the communication in our group solid, but also the communication between us and the stakeholders. As soon as something unexpected happens we've let them know, for example. When a group member decided to stop we've let them know as soon as possible ans also sended them the current state of our user stories.

![image](https://user-images.githubusercontent.com/74303221/172954296-68a9f5d1-df14-4668-9c32-50241f31f021.png)

### What are the others doing?
On our jira board i could always see what the others were doing for the project. In the folliwing picture i can see that Cas is currently working on 2 user stories and Tim is working on a task. Mike isn't assigned to an user story or task yet. I assume he finished his most recent user story recently. Since everyone is always working on something.

![image](https://user-images.githubusercontent.com/74303221/172953466-a102c551-0f8c-4077-8ba9-071b1cd4685b.png)

### Ask for feedback
After every sprint delivery we got feedback from the stakeholders and from the teacher. But this is only once every 3 weeks. We also often mailed our stakeholders to ask for feedback on user stories we were still working on. Here follows some proof.

![image](https://user-images.githubusercontent.com/74303221/172954438-de04f77b-ffb3-468c-ad17-51a4dbe20fcc.png)

![image](https://user-images.githubusercontent.com/74303221/172954933-1a472fc4-1d5f-41b8-9ab4-215f73518b2b.png)

### Technical Decisions
For our technical decisions I strongly recommend to visit our applications documentation.

[Restaurant Order System Documentation](https://github.com/fontys-group3)

# Research

## Which database fits my application the best?
For this research I made use of the [DOT framework](https://ictresearchmethods.nl/The_DOT_Framework).

**What**: I want to research which database fit my application the best.

**Why**: Instead of choosing a random database, I'd like to know which database fits my application the best. Because if you realize you chose the wrong database in the middle of the project it might cost a lot of time, effort and money(for a company, I'm just a student).

**How**: Find multiple articles about how to choose the right database for your application, validate them, and use them for my project.


