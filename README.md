# Portfolio Semester 3 - Kaan Gögcay

image of all products

## Table of contents
 - [Preface](#preface)
 - [Products](#products)
   - [Reverse Hangman Online](#reverse-hangman-online)
     - [Learning Outcome 1: Web Application (IP)](#learning-outcome-1-web-application-ip)
     - [Learning Outcome 2: Software Quality](#learning-outcome-2-software-quality)
     - [Learning Outcome 4: CI/CD](#learning-outcome-4-cicd)
     - [Learning Outcome 6: Design](#learning-outcome-6-design)
     - [Learning Outcome 8: Professional (IP)](#learning-outcome-8-professional-ip)
   - [Restaurant Ordering System](#restaurant-ordering-system)
     - [Learning Outcome 1: Web Application (GP)](#learning-outcome-1-web-application-gp)
     - [Learning Outcome 3: Agile Method](#learning-outcome-3-agile-method)
     - [Learning Outcome 5: Cultural Differences and Ethics](#learning-outcome-5-cultural-differences-and-ethics)
     - [Learning Outcome 6: Requirements](#learning-outcome-6-requirements)
     - [Learning Outcome 7: Business processes](#learning-outcome-7-business-processes)
     - [Learning Outcome 8: Professional (GP)](#learning-outcome-8-professional-gp)
 - [Research](#research)
   - [Which database is most suitable for my application?](#which-database-is-most-suitable-for-my-application)
   - [How do I protect the URLs my microservices use to communicate?](#how-do-i-protect-the-urls-my-microservices-use-to-communicate)
 - [Reflection](#reflection)

# Preface
Whilst reading you might encounter certain terms like IP, GP and S3, these refer to the terms Individual Project, Group Project and Semester 3 respectively. I'll start with showing all products I made this semester and then we'll go into the researches I did. Nothing else to add, have fun reading.

# Products
This semester I had to realise all the learning outcomes of semester 3. Per product I will explain how i realised the corresponding learning outcome. Here's a list with all the learning outcomes. I'll also include a list of requirements I have to realise this semester in my individual project.

[Learning Outcomes S3](https://fhict.instructure.com/courses/12078/outcomes)

[List of requirements Individual Project](https://fhict.instructure.com/courses/12078/pages/what-should-be-covered-in-my-individual-project?module_item_id=749928)

# Reverse Hangman Online
Reverse Hangman Online is a game I made for my individual project. I will explain per learning outcome how I realised it with my individual project. Everything about Reverse Hangman Online itself can be found in its documentation.

[Reverse Hangman Online Documentation](https://github.com/Epic-Chainsaw-Massacre)

## Learning Outcome 1: Web Application (IP)
*You design and build **user-friendly**, **full-stack** web applications.*

Clarification:

**User friendly**: You apply basic User experience testing and development techniques.

**Full-stack**: You design and build a full stack application using commonly accepted front end (JavaScript-based framework) and back end techniques (e.g. Object Relational Mapping) choosing and implementing relevant communication protocols and addressing asynchronous communication issues.

### Front-end
In this section I'll show some parts of my frontend, the bigger milestones. The front-end has been made in React-TypeScript. You can check the code in my repository.

[Reverse Hangman Online Frontend Repository](https://github.com/Epic-Chainsaw-Massacre/reverse-hangman-online-frontend)

#### TypeScript
Making a start with React TypeScript was very hard, without any experience I hopped in vscode and tried to do anything. This didn't work out at all. Everything I tried failed. My classmate [Mike van den Hoef](https://github.com/Headoros) was always willing to help me but still, It wouldn't work out this way. I decided to plan a TypeScript spike. In this spike I gathered information from the [W3schools TypeScript tutorial](https://www.w3schools.com/typescript/index.php) and at the same time i practised everything I was learning in a test project. TypeScript is such an awesome languange.

#### React
I also planned a React spike, same concept as above, I just try to gather as much information about React and try to implement it. I really like this type of learning and it always works out for me. For React I used the [W3schools React tutorial](https://www.w3schools.com/REACT/default.asp). In my opinion W3schools has the best tutorials to learn the basics.

#### Text Input
It was surprisingly hard to get the text input value and put it in a variable for the first time. I managed to do this with a variable called word. This updates everytime the text input changes. the variable basically represents live what's in the text input. Also did I have a second variable, called permission. if you click the button permission becomes true, because the word gets permission to be checked on existence, get it? I've put the code down here so you can try to understand what i've done (I've left out parts of code that make it more complicated and irelevant for this topic).

*parts of singleplayer.tsx*
```ts
const [word, setWord] = useState<string>("");
const [permission, setPermission] = useState<boolean>(false);

useEffect(() => {
    if (word.length > 3 && permission) {
        //send word to backend
        GetGoal();
        GetLives();
        GetGuessLine();
        setVisibilityClass('not-hidden')
    }
}, [gameStarted, word, permission])

// this happens everytime text input gets updated
function OnChange(e: React.ChangeEvent<HTMLInputElement>) {
    setWord(e.currentTarget.value);
}

function OnCLick(e: React.MouseEvent<HTMLButtonElement, MouseEvent>) {
    setButtonClicks(buttonClicks + 1);
    setPermission(true);
}
```

#### API Requests
This was hard to get into, even when I did a request once. It stayed hard for a while. After doing it a few times API requests are a breeze. Here are some API request examples, these are the ones used in the code above.

*parts of singleplayer.tsx*
```ts
const GetLives = async () => {
    console.log("word: " + word);
    const apiUrl = "https://localhost:7071/Lives?word=" + word;
    const data = await fetch(apiUrl);
    const jsonData = await data.json();
    setLives(jsonData)
};
const GetGoal = async () => {
    console.log("word: " + word);
    const apiUrl = "https://localhost:7071/Goal?word=" + word;
    const data = await fetch(apiUrl);
    const jsonData = await data.json();
    setGoal(jsonData)
};
const GetGuessLine = async () => {
    console.log("word: " + word);
    const apiUrl = "https://localhost:7071/GuessLine?word=" + word;
    const data = await fetch(apiUrl);
    const jsonData = await data.json(); // Error
    setGuessline(jsonData)
};
```

### Back-end
Just like the front-end section, I'll show some of the milestones, more noticeable events that occured in my backend. The back-end has partially been made in C# .NET and partially in Java Spring. You can check the code in my repositories.

[Reverse Hangman Online Backend Repository](https://github.com/Epic-Chainsaw-Massacre/reverse-hangman-online-backend)

[Game Statistics Service Repository](https://github.com/Epic-Chainsaw-Massacre/Game-Statistics-Service)

[Word Service Repository](https://github.com/Epic-Chainsaw-Massacre/Word-Service)

#### External API
I've heard of it so many times, yet did I never use it. External API's, had 0 experience going into this. As you should already know, I'm making a hangman-like game. Since there will be used words in my game, they should get checked on existance. To check a word on existance I've build a very, very vague process. So my backend does an API request to Miryam Webster (dictionary API I use). If the word exists, Miryam Webster returns me values, so now you would say, if tha API returns anything it's good right? WRONG, this is where it gets interesting. Miryam Webster's dictionary API uses fuzzy search, this means that if I do ana API request with 'Birate'. It will return me lots of different words that are almost the same as 'Birate', for example 'Pirate'. See example.

![image](https://user-images.githubusercontent.com/74303221/173444601-1bbfd695-1937-41d2-bdfa-2f0d5724679a.png)

To solve this problem I found a solution. If I do a request of the word 'Pirate', this is the JSON result I get.

```json
[
   {
      "meta":{
         "id":"pirate",
         "uuid":"02589eac-2077-4abd-abfe-1d72ad856773",
         "sort":"1600684000",
         "src":"sd2",
         "section":"alpha",
         "stems":[
            "pirate",
            "pirates",
            "piratical",
            "piratically"
         ],
         "offensive":false
      },
      "hwi":{
         "hw":"pi*rate",
         "prs":[
            {
               "mw":"\u02c8p\u012b-r\u0259t",
               "sound":{
                  "audio":"pirate01"
               }
            }
         ]
      },
      "fl":"noun",
      "def":[
         {
            "sseq":[
               [
                  [
                     "sense",
                     {
                        "dt":[
                           [
                              "text",
                              "{bc}a robber of ships at sea {bc}a person who commits piracy"
                           ]
                        ]
                     }
                  ]
               ]
            ]
         }
      ],
      "shortdef":[
         "a robber of ships at sea : a person who commits piracy"
      ]
   }
]
```

Important to note is that meta.id contains the word i did a request for. So the only thing I gotta do in my code is check if meta.id equals the word I did a request for. Here's my code for it. As you see I've put it in a try catch, since the json object isn't guaranteed to have data for meta.id. Because as you saw in the 'Birate' request we didn't have meta nor did we have id. This is the way I filter away words that don't exist.

```java
String wordString;
try {
    wordString = json.getJSONObject(0).getJSONObject("meta").getString("id");
}
catch (Exception e) {
    return false;
}
```

#### Reverse Hangman Forms Copy Paste
So as you might know, I made an application in WinForms called ReverseHangmanDesktop. Since all the logic in ReverseHangmanDesktop was coded seperately from the presentation layer, I could just copy paste all the logic from that application into my application. My application did become an absolute mess. But i got all the backend functionalities in only a few minutes. Otherwise it would probably take hours.

![image](https://user-images.githubusercontent.com/74303221/173446686-4a8d6a00-e537-4be5-9aee-1028e6214576.png)

#### Communicate with Front-end
Communicating with the frontend was a mystery at the start, I looked op tutorials how you make a C# service that can talk with a React frontend. It looked all super vague to me, I even tried to build a controller in WinForms haha don't do that. I did manage to call API requests from a WinForms application, that was actually pretty funny. But I was wasting time. Finally I went in visual studio and wrote API ASP.NET something like that. I clciked the one with ASP.NET Core. It was all a very random process. Maybe I also used a guide I can't remember it too well. But when I got in the project I got an auto-generated example with WeatherForecast that returned an array with some extra's. I just simplified that auto-generated endpoint and created the following.

```cs
app.MapGet("/Lives", ([FromUri] string word) =>
{
    gameSetup.differentLettersInWord = WordClass.CountDifferentLetters(word);
    gameSetup.game.teamCollection.GetTeamList()[0].CalculateLives(gameSetup.differentLettersInWord);
    return gameSetup.game.teamCollection.GetTeamList()[0].Lives;
}).WithName("GetLives");

app.MapGet("/Goal", ([FromUri] string word) =>
{
    int goal = gameSetup.game.teamCollection.GetTeamList()[0].GuessCollection.CalculateGoal(gameSetup.differentLettersInWord);
    return goal;
}).WithName("GetGoal");

app.MapGet("/GuessLine", ([FromUri] string word) =>
{
    gameSetup.game.SetWord(word);
    string guessline = gameSetup.game._wordClass.CalculateWordStripes();
    return guessline.Length / 2;
}).WithName("GuessLine");
```

My frontend just gives the word to an endpoint, the endpoint does some calculations with the word and returns for example the amount of lives it should return.

### Future Plans
My future plans are to finish a working round in Reverse Hangman Online. Right now you can only fill in a word, and make it check on existance. further on do the lives and goal get calculated using the word.

Also do I still want to save game results to a database. Right now nothing with a database happens. Also would I like to show my data from my database in my frontend. Further on I was planning to make songs for my game. I really looked forward to that. Also adding sound effects, it brings the game overal more alive. At last I also wanted to add different languages, for this project i was planning on making English and Dutch. By changing the language, not only the UI should change but also the checking of words, so that means I would probably have to use a dutch dictionary API. Finally I wanted to add a ranking system to my game. people would be able to create an account and have an amount of rank points, elo. This elo would make people play against others from the same skill level.

### UX-Testing
I sadly haven't been able to do user experience testing since my application wasn't done yet. So I couldn't let someone test it. Parts of my application were done quite early but the game itself wasn't.

### Object Relational Mapping
In our GP we used an ORM for our menu-service. In our service we've created entities, with some annotations and configuration we set up that the entities we've created get created in a MySQL database. Here is an example of what an entity class looks like. 

![image](https://user-images.githubusercontent.com/74303221/173344401-af5e6d42-49b6-4505-95a2-c96be3813518.png)

This is what it looks like in MySQL if we run the application.

![image](https://user-images.githubusercontent.com/74303221/173344881-16332f66-b3d9-42ca-8dc5-958a8d745f00.png)

As you saw there's already data in it, we've done this by adding a data.sql file. In the red square you can see the lines of code that generate our data.

![image](https://user-images.githubusercontent.com/74303221/173345048-ed4d1e85-3cd3-4586-9eec-fdb036860ba1.png)


## Learning Outcome 2: Software Quality
*You use software **tooling and methodology** that continuously monitors and improve the software quality during software development.*

Clarification:

**Tooling and methodology**: Carry out, monitor and report on unit integration, regression and system tests, with attention for security and performance aspects, as well as applying static code analysis and code reviews.

### Testing
In this semester I have to make use of 4 types of tests, unit, integration, regression and system tests. If i have a good explanation for it I may decide to not use certain types of tests.

### Static Code Analysis
For code analysis i've made use of SonarCloud. I chose SonarCloud since a classmate of mine told me it is pretty easy to setup via SonarCloud. After a pull request to master, the SonarCloud code analysis get executed. Using code analysis i can easily find vulnerabilities in my code.

![image](https://user-images.githubusercontent.com/74303221/173247608-e802e311-4316-4a2a-96d0-318d8b2dcf75.png)

Right now I only got the SonarCloud code analysis working on 2 out of 4 repositories. My goal is to have code analysis in every repository, so all of my repositories will have better code. 

#### Code Smells
Currently SonarCloud doesn't detect any bugs or vulnerabilities in my code. It does detect a few code smells.  

![image](https://user-images.githubusercontent.com/74303221/173247751-ebf66669-5bfe-4a9f-8b06-0e320609cce6.png)

Here's an entire list of code smells in my front-end application. 

![image](https://user-images.githubusercontent.com/74303221/173247849-7599d782-7d60-4b1e-808f-4ed045f2dfbc.png)

My goal with SonarCloud is to review the code smells and fix them. If SonarCloud notifies me that there are problems I will solve them first before merging my pull request.

### Code Reviews
blank

## Learning Outcome 4: CI/CD
*You **design and implement** a (semi)automated software release process that matches the needs of the project context.*

Clarification:

**Design and implement**: You design a release process and implement a continuous integration and deployment solution (using e.g. Gitlab CI and Docker).

### Continuous Integration
I've setup continuous integration pipelines in all my applications. The pipelines build the application and run all the unit tests I've written. I did all of this using the GitHub actions section. GitHub actions provides lots of templates which make it very easy to setup a pipeline. For my front-end, back-end, game-statistics-service and word-service I used a Node.js, .NET template another .NET template and a Java maven template respectively. 

Here's an example where I the pipeline actually helped me improve my code. I kept getting build errors, but my project itself would just run normally so without the pipeline I would't notice. I did get a few messages in my IDE but I always ignored them, I only noticed it when they were gone.

![image](https://user-images.githubusercontent.com/74303221/173389942-39ad0666-73b5-41bd-9837-1a12e6ed8b8f.png)

[Reverse Hangman Online Frontend CI/CD](https://github.com/Epic-Chainsaw-Massacre/reverse-hangman-online-frontend/actions/workflows/node.js.yml)

[Reverse Hangman Online Backend CI/CD](https://github.com/Epic-Chainsaw-Massacre/reverse-hangman-online-backend/actions/workflows/dotnet.yml)

[Game Statistics Service CI/CD](https://github.com/Epic-Chainsaw-Massacre/Game-Statistics-Service/actions/workflows/dotnet.yml)

[Word Service CI/CD](https://github.com/Epic-Chainsaw-Massacre/Word-Service/actions/workflows/maven.yml)

### Continuous Deployment
I also added CD to all of my repositories. This means that, after a pull request on the master everything gets deployed on docker.

![image](https://user-images.githubusercontent.com/74303221/173250305-8d6d2b01-faec-4ed3-bb0f-29a94ca0c52b.png)

## Learning Outcome 6: Design
*You translate (non-functional) requirements to extend existing (architectural) designs and can validate them using **multiple types of test techniques**.*

I've split this learning outcome into 2 parts. In this section I'll focuss more on the design. If you are looking for the requirements part of this learning outcome, have a look at the GP version of this learning outcome.

[Learning Outcome 6: Design](#learning-outcome-6-design)

### Design Origin
At first glance it all might looked like I was building a random interface and hoping for the best. Actually what I was doing all this time is trying to recreate my application I made earlier, ReverseHangmanDesktop. This is was ReverseHangmanDesktop looks like (if you've read Reverse Hangman Online Documentation this might look furmilair).

![image](https://user-images.githubusercontent.com/74303221/173570455-621c2a54-a43f-4498-80e6-6f570801afb1.png)

![image](https://user-images.githubusercontent.com/74303221/173570820-9ee24450-4e26-46ab-9e69-7cb9e7e419ea.png)

#### Comic Sans MS
But how did I come up with this design you're asking? As you might know, Comic Sans MS is the real meme font. ReverseHangmanDesktop itself was a meme that slowly became reality. So I wanted to make the application for it a big meme. This also perfectly fits that it has been made in WinForms.

#### Black and White
The colors black and white haven't been chosen randomly. I wanted to create a page that gives a 'grim ominous' vibe. I'm not sure if thats the corerct words I'm trying to say 'een kille en nare vibe'. Having a black screen gives this dead and cold vibe. For a long time I was also looking for scary fonts like these.

![image](https://user-images.githubusercontent.com/74303221/173572160-33f7eccf-f126-4236-8559-78cf226fd0b8.png)

![image](https://user-images.githubusercontent.com/74303221/173572196-314fc5da-5216-4b9b-951a-0f81fb178c52.png)

But usually they costed money or I didn't like them, after like 30 minutes of searching for a good font I just decided to roll with the meme.

#### User Interface
For the UI I just wanted to keep it simple and clean. I don't want people to stare all day to the screen trying to understand what it all says. That's why i tried to sctructure the app. Down below you can again see ReverseHangmanDesktop.

![image](https://user-images.githubusercontent.com/74303221/173572547-f1828901-a42d-4e0b-82f7-2724134b4567.png)

The idea is again to replicate this onto my project. Currently it looks like this.

![image](https://user-images.githubusercontent.com/74303221/173572977-84aa2916-a58a-4712-bd0e-58bf1c2bd9b6.png)

I also still wanted to make a background looking something like this. This also adds up to the spooky vibe of the application. Here are some skechtes, this is NOT how the applciation looks like now. just ideas.

![image](https://user-images.githubusercontent.com/74303221/173578807-efd02e2c-b314-4269-b9e9-e2da0d06e798.png)

![image](https://user-images.githubusercontent.com/74303221/173579409-fb21c35e-8216-4c86-9a32-b666b18bf8c8.png)

#### UX-Testing
If you are looking for UX-Testing check out.

[Learning Outcome 1: Web Application (IP)](#learning-outcome-1-web-application-ip)

## Learning Outcome 8: Professional (IP)
*You act in a **professional manner** during software development and learning.*

Clarification:

**Professional manner**: You actively ask and apply feedback from stakeholders and advise them on the most optimal technical and design (architectural) solutions.
You choose and substantiate solutions for a given problem.

### Feedback
This semester started off with [Leon van Bokhorst](https://github.com/leonvanbokhorst). I asked him weekly feedback, sadly you won't be able to find it all back in my FeedPulse PDF Report, since sometimes my teacher forgot to open a feedpulse session. Leon has motivated me a lot throughout the semester, and definitely turned this boring documentation focussed semester into a fun semester. Later in the semester, the last 3 weeks, i got 2 new teachers, [Jean-Paul Ligthart](https://github.com/jpligthart) and [Timo Hermans](https://github.com/timohermans). I also tried to speak both of them once a week.

blank v
[FeedPulse PDF Report](#blank)

# Restaurant Ordering System
The Restaurant Ordering System was my group project this semester. I made it together with [Mike van den Hoef](https://github.com/Headoros), [Tim Meijvogel](https://github.com/Timsel1), [Cas Esselink](https://github.com/CasEsselink) and [David Chang](https://github.com/Davidchang24). Everything about our Group Project can be found at it's documentation

[Restaurant Ordering System Documentation](https://github.com/fontys-group3)

## Learning Outcome 1: Web Application (GP)
*You design and build **user-friendly**, **full-stack** web applications.*

Clarification:

**User friendly**: You apply basic User experience testing and development techniques.

**Full-stack**: You design and build a full stack application using commonly accepted front end (JavaScript-based framework) and back end techniques (e.g. Object Relational Mapping) choosing and implementing relevant communication protocols and addressing asynchronous communication issues.

### Front-end
The front-ends has been mainly made by Me, Mike, Tim and David. We coded it in React-TypeScript. Me and David worked on the same repo, Tim had its own and Mike also had its own. We had different repositories since we used a microservice structure.

### Back-end
The application has multiple backends. The backends have been made by Me, Mike, David and Cas. The only language we used in our backend is Java. Me and David worked on the same backend. After a while when me and David got some processes working between the front-end and back-end we decided that I would mainly focus on the front-end and he would focus on the back-end, since it was pretty annoying to both work on both. But on the other hand, since we've setup everything together we both exactly knew how each others' application worked.

### My Tasks
I'll slowly take you through everything I was responsible for.

#### Menu Logic
Me and David have worked on everything behind the scenes of our menu. We came across such a hard problem that I couldn't even describe it to look it up. I also couldn't do it in C#. I was completely lost, since usually, logic wise, nothing is impossible to me in C#. The problem we had was sorting our products into categories. So that all deserts get sorted together, all  main dishes would get sorted together etcetera. In the end of the day Mike or David solved it some how. Pretty funny, I found the message back where I'm saying "_design is going good but I have no idea how to get them sorted right_".

![image](https://user-images.githubusercontent.com/74303221/173420101-f96a85ce-5683-4cd9-a557-19a143107225.png)

#### Menu Design
Also did i work on the design in the first sprint. The menu looked a bit prototype-ish, so Mike gave it a big make over. Here is the old design I made in sprint 1.

![image](https://user-images.githubusercontent.com/74303221/173419259-bc31c838-1cdb-48e7-b750-2cf27c51535b.png)

#### Inventory
My latest task was about making the inventory in our menu. I made the inventory so that when you click on a product, it check in the database how much there's left for the item. If there's more than 0 left, one gets removed from the database. Why do we use a database for this you'd ask? Since you can also save everything on the page. We used to save in on the page, but the problem then was that it wouldn't share data between different clients. If a product is out of stock it gets grayed out like down below.

![image](https://user-images.githubusercontent.com/74303221/173433824-06d00ee3-5066-4b5b-b48a-bf28efb75f90.png)


### UX-Testing
We haven't done UX-Testing in our group project.

## Learning Outcome 3: Agile Method
*You can implement the software process for your project according to a given agile software development method.*

Clarification:

**Agile** method: You are aware of most popular agile methods and their underlying agile principles. You are able to implement the process of your software project according to a chosen methodology.

### Scrum
For our group project we used the agile method scrum. We chose Scrum after the result of a research one of our group members did, sadly he stopped and I can't find it back. In our project we have one scrum master every sprint. The scrum master would lead the stand-ups and standdowns. Furthermore, the scrum master in our project didn't have too much meaning. For example, usually the contact person in the group is the scrum master. But we found it easier to make that role static and give it to a group member (me). It kind of felt like we were all the scrum master, this way of working didn't really give any problems. 

### Kanban
The kanban methodology has 6 practises that help you through your project, we'll cover all 6 briefly.

#### Visualize your work
When starting a kanban project its important to visualize your work in a kanban board. Kanban boards can look very differently, in the image below you see the most basic exmaple.

![image](https://user-images.githubusercontent.com/74303221/173593181-bc1769a5-fd60-4637-94d6-afcce31bfab1.png)

Some people tend to add extra tabs to it, or make it their own. That's all depending on your group.

![image](https://user-images.githubusercontent.com/74303221/173593650-26a8a1b3-d3a0-4df8-a903-176a243b90cd.png)

#### Limit Work in Progress
This basically means as a group you set a limit to the 'in progress' tab. I took the example I just showed and drew a red line at the bottom of the in progress tab. This way the work in progress tab stays clean. The work in progress limit depends on how big your group is. For example if you have a group of five people you want to have arround 6/10 tasks.

![image](https://user-images.githubusercontent.com/74303221/173594939-4a81c8eb-25bc-40ed-a2c3-3610b2294112.png)

#### Manage Flow
Through the process you check how your requirements go through the kanban board. If there are requirements stuck on in progress for a while you might reconsider if the requirement is setup right.

#### Define when a requirement is done
When working on a requirement you might just keep going on forever not knowing when to stop. That's why you should add definition of done's to yourr requirements. This way you can check you checklist and know when a requirement is done.

#### Apply Feedback
It's important to ask and apply feedback within the group, within the group members and also with the product owner. You can setup feedback loops you do every x time, where you discuss a list of things or for example do code reviews. 

#### Improvement
It's important to keep improving throughout the process. You don't just make you're requirements, setup the board and just work till then end. Whenever you can improve something in the project, its important to improve it.

## Learning Outcome 5: Cultural Differences and Ethics
*You **recognize** and **take into account** cultural differences when working with multi-site teams and are aware of ethical aspects in software development.*

Clarification:

**Recognize**:  Recognition is based on theoretically substantiated awareness of cultural differences and ethical aspects in software engineering.

**Take into account**: Adapt your communication, working, and behaviour styles to work with other developers from different cultures; 
Address one of the standard Programming Ethical Guidelines (e.g., ACM Code of Ethics and Professional Conduct) in your work.  

### Coding Together
We didn't have very strict coding standards in our team. We did have one rule and that is to code everything in English. 

If multiple people worked on one repository we made branches and push the branches to GitHub. finally we merge them to the master. Working like this we avoid pushing our code to the master branch which could be very fatal.

## Learning Outcome 6: Requirements
*You translate (non-functional) requirements to extend existing (architectural) designs and can validate them using **multiple types of test techniques**.*

Clarification:

**Multiple types of test techniques**: You apply user acceptance testing and stakeholder feedback to validate the quality of the requirements. You evaluate the quality of the design (e.g., by testing or prototyping) taking into account the formulated quality properties like security and performance.

### Quality Requirements
Before we started coding, we showed our user stories to the stakeholders. When they agreed to the user stories we started working on them. In a sprint delivery we didn't only deliver all our products but also did we show our stakeholder which user stories we would work on next sprint. This is very good to do since if they don't like a part of a user story or the priority of a user story they tell it us. Sadly we don't have footage of the stakeholders giving us feedback, but we do have the minutes of every meeting. Here are some example of feedback we wrote down during meetings/sprint deliveries.

In blue you can see their feedback on all our user stories. Since it's a lot I'll translate a few. *add the user story that adds the functionality to place an order*, *user story 12 'actions' isn't clear for us, and what do you guys consider as a mistake?*, *in lots of user stories you guys use the format 'As a User ... because ...' , you guys can leave away the 'because' if it's not necessary.* 
![image](https://user-images.githubusercontent.com/74303221/173034408-4500e704-bafe-476f-a42b-fa1a3fadbe93.png)

In blue it says, *It's not important to focus on the paying process*, underneath the blue sentence they gave us advice on functionalities they would like to see instead, for example, *Make it impossible for outsiders to reach our website*, *saving a session to the backend*, *show all orders in the management portal* and *completing an order*.
![image](https://user-images.githubusercontent.com/74303221/173032795-1fd22516-dc6e-421c-824a-2c7d2a544552.png)

### User Stories and Non-Functional Requirements
We kept track of all our user stories and non-functional requirements using Jira. Here are all our user stories and non-functional requirements. User stories are green, non-functional requirements are blue.

![image](https://user-images.githubusercontent.com/74303221/173355981-5ee09425-6218-42fe-84a2-ab1d6141d9a7.png)

![image](https://user-images.githubusercontent.com/74303221/173356292-7b775bae-221e-4652-9d94-43491b633049.png)

![image](https://user-images.githubusercontent.com/74303221/173356101-94592784-36dd-43e6-a3d1-91e049febd0a.png)


### Security and Performance
We had a few security issues in our project. For example, its possible to place an order, eat your food, remove your cookies on the browser. and it doesn't say you have to pay anymore. Our solution for this would be to save the cookies in the backend. At this moment we only save it in the frontend. Another security flaw is that it's possible to place an order while you aren't even near the restaurant. We wanted to solve this problem by making it impossible to reach the URL if you are on a different IP, but that required WI-FI. And using a restaurant WI-FI isn't the most user friendly solution. so for this flaw we didn't find an solution yet. Sadly we ran out of time to build the functionalities.

### Technical Decisions and Architecture
For our technical decisions and architecture I strongly recommend to visit our applications documentation.

[Restaurant Order System Documentation](https://github.com/fontys-group3)

## Learning Outcome 7: Business processes
*You can explain **simple** business processes and **relate** them to the development of your software project.*

Clarification:

**Simple**: predominantly sequential processes with one or two alternative paths.

**Relate**: understanding the relationships between the process and software.

### Ordering Process
In our business process we visualized the entire process of making an order digital and analog. You see 3 phases in this process, these are placing the order, prepare the order and finishing the order. Let's go through 2 quick examples. 

### Non-Digital
John enters the restaurant and takes a seat. Now the ordering process takes place. In the order process John orders a burger and a coke. The waiter writes it all down and brings the order to the kitchen and bar. This is where the preparing phase starts. The kitchen makes a burger and the bar prepares a coke. When everything is prepared, the waiter takes it to John's table. If John is done dining, the ending phase starts. In this phase the cashier types in the amount of money John has to pay. John pays for the food. If John gave too much money he also gets his change from the cashier. Now the cashier asks John if he wants the receipt. John decides he wants the receipt, and leaves the restaurant.

### Digital
John enters the restaurant and takes a seat and scans the QR code to open up the menu. Here the process of ordering will start. John clicks on a burger and a coke, and places the order. Now the preparing phase starts. Kitchen and bar employee claim the burger and the coke in their interface respectively. When both are ready to serve, they drag the order to done in their interface. Then the waiter gets the order and serves it out to John. If John is done eating, the ending phase starts. He gets an invoice to his phone, after paying he can choose if he wants the receipt and he's free to go.

### Key Differences
Let's go through the biggest differences between non-digital and digital together. 

#### Ordering
When ordering non-digital the waiter can accidentally write down an order wrong just because he misunderstood the customer. When done digitally, the customer chooses what he wants to eat using software. Before ordering you can double check everything what you've selected. After placing the order the waiter brings it to the kitchen and bar, this could also go wrong in multiple ways. The waiter might have to help a customer on its way to the kitchen or the bar. also can he mix up what has to go to the bar and what has to go to the kitchen. Digitally this all goes automatic.

#### Preparing the order
In an non-digital situation, the order comes in and the employee takes the order and prepares it. This is very similar to how it would go digitally. When using our software you replace the paper with technology.

#### Payment
In an non-digital situation you have to go to the checkout. Here they get your bill, and type it in on the cash register. Digitally you can just stay on your place, pay and leave. The cashier could possibly give you the wrong bill giving a bad customer experience. When paying digital, this can't occur.

*Business process for making an order*
![image](https://user-images.githubusercontent.com/74303221/173024638-a51d2346-4b31-43a5-b7ad-1ce023b01e67.png)


## Learning Outcome 8: Professional (GP)
*You act in a **professional manner** during software development and learning.*

Clarification:

**Professional manner**: You develop software as a team effort according to a prescribed software methodology and following team agreements. You are able to track your work progress and communicate your progress with the team. You actively ask and apply feedback from stakeholders and advise them on the most optimal technical and design (architectural) solutions. You choose and substantiate solutions for a given problem.

### Team Communication
Inside our group we used Teams and Discord to communicate. We started off in Teams, but after a while we only used the Teams for files and we permanently switched to Discord. In our group project we had a set of rules about presence.

*Rules of Presence*
![image](https://user-images.githubusercontent.com/74303221/172949644-04301849-de14-4ae8-b7b8-f988d8f2ef1b.png)

For the English readers, this says. *Be present at 09:00, after 09:10 you will be considered as late, if you know you will be late let us know 1 day before. If you don't let us know anything, you are late and you don't have a valid reason to be late, we give you a strike. All the rules that apply to being to late also apply to not showing up at all. If you get you're third strike we inform the teacher about your presence. 

Always if i knew i would be late i let my group know but to prove it here are some messages of me letting my group know i will be too late.

![image](https://user-images.githubusercontent.com/74303221/172952242-3fc00baa-3ed7-4e82-8ae6-3f1f81da832b.png)
![image](https://user-images.githubusercontent.com/74303221/172952188-a35c89c3-2e90-468e-9be0-0e4e525bf3b3.png)
![image](https://user-images.githubusercontent.com/74303221/172952157-a3bf6c8e-2f65-412a-8499-e911c2bad0e0.png)
![image](https://user-images.githubusercontent.com/74303221/172952128-d5dea735-1c1e-4233-a8c6-55e5a5ed2a42.png)
![image](https://user-images.githubusercontent.com/74303221/172952108-61ab7cb4-30cf-45f9-82ee-94bb2c2578d0.png)

Again for the English readers, these are just messages like, *I will be x minutes later, I got to go to the family doctor, I had a bloody nose so I will be later.*

### Communication with the Stakeholders
Not only is the communication in our group solid, but also the communication between us and the stakeholders. As soon as something unexpected happens we've let them know, for example. When a group member decided to stop we've let them know as soon as possible and also sent them the current state of our user stories.

![image](https://user-images.githubusercontent.com/74303221/172954296-68a9f5d1-df14-4668-9c32-50241f31f021.png)

### What are the others doing?
On our Jira board I could always see what the others were doing for the project. In the following picture I can see that Cas is currently working on 2 user stories and Tim is working on a task. Mike isn't assigned to an user story or task yet. I assume he finished his most recent user story recently. Since everyone is always working on something.

![image](https://user-images.githubusercontent.com/74303221/172953466-a102c551-0f8c-4077-8ba9-071b1cd4685b.png)

### Ask for feedback
After every sprint delivery we got feedback from the stakeholders and from the teacher. But this is only once every 3 weeks. We also often mailed our stakeholders to ask for feedback on user stories we were still working on. Here follows some proof.

![image](https://user-images.githubusercontent.com/74303221/172954438-de04f77b-ffb3-468c-ad17-51a4dbe20fcc.png)

![image](https://user-images.githubusercontent.com/74303221/172954933-1a472fc4-1d5f-41b8-9ab4-215f73518b2b.png)

### Technical Decisions
For our technical decisions I strongly recommend to visit our applications documentation.

[Restaurant Order System Documentation](https://github.com/fontys-group3)

# Research

## Which database is most suitable for my application?
For this research I made use of the [DOT framework](https://ictresearchmethods.nl/The_DOT_Framework).

**What**: I want to research which database fit my application the best.

**Why**: Instead of choosing a random database, I'd like to know which database fits my application the best. Because if you realize you chose the wrong database in the middle of the project it might cost a lot of time, effort and money(for a company, I'm just a student).

**How**: Find multiple articles about how to choose the right database for your application, validate them, and use them for my project.

I've put the document with the research in it in my portfolio, Because its so big you have to download it.

[Database Research](https://github.com/CrossyChainsaw/Portfolio/tree/master/Database%20Research)

## How do I protect the URLs my microservices use to communicate?
For this research I made use of the [DOT framework](https://ictresearchmethods.nl/The_DOT_Framework).

**What**: I want to research how I can protect my URLs against everyone except my services.

**Why**: If i don't protect the URLs, people can DOS attack my services, which take down my application.

**How**: Trying to understand what all the risks are of not protecting the URLs, and finding out how to protect the URLs making use of reliable sources and validation.

I've put the document with the research in it in my portfolio.

[Security Research](#blank) (blank)

# Reflection
Here I'll explain what I would do different the next time. Here you will find out stuff about my semester you might have never even known, pretty fun section. Enjoy.

## Planning
My planning this semester was terrible, honestly I don't know how I ended up in this state. In the final week I got my stuff together and made a planning for myself. In the planning it says everything I still have to do/make. This is what my planning currently looks like. In the last week it really felt like all my structure I usually have came back.

![image](https://user-images.githubusercontent.com/74303221/173577617-be6f2748-156c-43df-9338-52afac4153c3.png)

## Research
In my database research I've done a few things I will do different next time. 

#### Filtering Sources
The way I decided which sources to use was. I looked up a source. Researched the person that wrote it. If the person was well known and had a database background I gave it a high trust level, if not I gave it a low trust level. Why won't I do this next time? If someone is well known to a lot of people and has 10 years of experience with databases, it doesn't mean he has a good understanding of databases. A better strategy would be to find multiple sources, and use the infromation I encounter the most. If multiple people say the same stuff it sounds more reliable to me.

#### Drop Databases for the wrong reasons
In my research I dropped a few databases for controversial reasons. I dropped a database that had extra functionalities that I didn't need. But in the and all databasese have that so that was quite unnecessary. I dropped 2 database types because they dont directly support a key functionality I need. But by using a workaround I could actually make them work. As soon as I saw the key functionality was missing I instantly dropped it, but I shouldve given it a chance to the end. This is a good way to start the next topic.

#### Random Conclusions 
I randomly had a few conclusions throughout the research. Usually you have a conclusion at then end, but I had multiple at random spots. This usually means I have researched topics inside of my research, I kept researching and researching. This blends in nicely with the next topic.

#### Kept Researching
I kept researching everything. That's not bad, but I also kept researching topics that didn't fit in my database research at all. For example I researched how reliable people are that write online guides.

#### Time
The next time I will start earlier, I kept procastinating since I didn't know what I wanted to research, and because I found the DOT-framework very vague. In the end I started researching in the last week. This was a strange experience for me since I usually plan everything perfectly.

## Don't just listen/do what others say
In this semester for example, my teacher would tell me I had to create a login, importing Auth0 and all that. I had never read that anywhere on canvas, but honestly I didn't read canvas that well. Also something really stupid of me this semester. But I just accepted I had to do it. Luckily another teacher told me later on it wasn't necessary. And i did a security research instead of building a login.

Also teacher A said he recommended us to learn Java, so we learn a different language. Then teacher C asked me why I decided to learn Java and my response was, 'Because the teacher recommended it'. It would've been better if I would've thought more about that decision. In the end i'm quite happy i worked with java but still. Next time just think more before instantly making a choice. 

Also did I think I had to build a microservice application for my individual, but that wasn't even the case. Also kinda adds up to all this.

## Start taking GP more seriously
in semester 2 we had a really nice and kind man as product owner. It felt like he was just a classmate of us. With the same mindset i went in S3 and I felt like I was a bit too comfortable with the product owners. I started to just have a chat with them that they looked like some celebirity. But I surely wouldn't do that next time hahah.

*I showed an image of this guy to the product owner saying he looked like him*
![image](https://user-images.githubusercontent.com/74303221/173576715-3ad7f388-29c3-43bf-99db-420e54b68de6.png)

## Bad First Impression
Our first impression with the product owners was horrible. We had to ask them question about the case they've send us. But only or two people of our group did actually read it. That was a terrible experience. At first it felt like our group tried to keep it secret, but I just told them we didn't read it at all nor had we seen it. Our teacher sent it so us over Teams so that was really on us. To do this better next time I should read Teams more frequently. But the issue with that is, I get so much garbage over teams for some reason. So maybe I should just clean that.

## Code Tools used too late
So I have to use all kinds of tools that help improve my code, for exmaple the CI pipeline and code analysis. Instead of using these tools to improve my code. I added them in the end of the semester showing the teachers I can use them.
