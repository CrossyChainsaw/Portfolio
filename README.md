# Portfolio Semester 3 - Kaan Gögcay

*Here you see an image of a few products i worked on this semester. Going from left to right, [AutoClicker](https://github.com/CrossyChainsaw/AutoClicker), [BattleSim](https://github.com/CrossyChainsaw/BattleSim), [Restaurant Ordering System](https://github.com/fontys-group3), [MoneySquadronVirus](https://github.com/CrossyChainsaw/MoneySquadronVirus), [Ranknir](https://github.com/CrossyChainsaw/Ranknir), [Reverse Hangman Online](https://github.com/Epic-Chainsaw-Massacre), *

![template (1)](https://user-images.githubusercontent.com/74303221/173811448-e70513a6-6dfd-4a5c-a1fa-eb41815771fb.png)

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
   - [Ranknir](#ranknir)
   - [Money Squadron Virus](#money-squadron-virus)
 - [Research](#research)
   - [Which database is most suitable for my application?](#which-database-is-most-suitable-for-my-application)
   - [How do I protect the URLs my microservices use to communicate?](#how-do-i-protect-the-urls-my-microservices-use-to-communicate)
 - [Reflection](#reflection)

# Preface
Whilst reading you might encounter certain terms like IP, GP and S3, these refer to the terms Individual Project, Group Project and Semester 3 respectively. I'll start with showing all products I made this semester and then we'll go into the researches I did. It gets mentioned pretty soon down here but maybe you only read the preface and skip some other things so keep in mind that a lot of my IP gets explained in my application's documentation. Usually I refer to the documentation but just to be sure, I've added it down here. Same goes for the GP. Nothing else to add, have fun reading.

[Reverse Hangman Online Documentation](https://github.com/Epic-Chainsaw-Massacre)

[Restaurant Ordering System Documentation](https://github.com/fontys-group3)

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
My project wasn't finished yet. So i couldn't let someone test my application. I asked my teacher for solutions, and he told me I could make wireframes and test the experience on users using my wireframes. I could also step it up and make a prototype of my application, and let users test my prototype, focussing on the process and gameplay over the looks and design, because in the end its just a prototype. Last semester I made an application called Reverse Hangman Desktop. Reverse Hangman Desktop is a prototype-ish application I made in WinForms. My entire individual project is based of the prototype-ish application. So my prototype application would be perfect for UX-testing.

#### Moderated User Testing
For my project I did a moderated user test. This means I let someone play through my application, whilst spectating. If my user had any questions about the application he could ask me. The more questions he would ask the more I should update. Let's actually look like what happened during the test, and how it went.

#### Jay Tests my Applciation
Some guy I found at school called Jay was willing to test my prototype application. By forehand I told Jay that anything he could mention anything that looked off. Having that said we started actually testing the game. We would play against each other. We would choose teamnames and start playing. I had to start choosing a word, and he had to start guessing. In this playthrough I chose the word 'Dongel' (Dutch word for Dongle). Here you see an image of Jay guessing the word.

*Image of Jay thinking*
![image](https://user-images.githubusercontent.com/74303221/173931794-31c3b963-ad19-4f3b-8b9e-c9e2eeab4c5a.png)

*Oopsie, the letter 'N' is in the word*
![image](https://user-images.githubusercontent.com/74303221/173931980-02e6dea7-a4a4-448f-aed8-fc7ea124742b.png)

Jay completed the first round gaining 2 points. Now it was his turn choosing a word.

*Jay typing a word :0*
![image](https://user-images.githubusercontent.com/74303221/173932093-a16db979-9ddb-4ec2-be3d-a80356c06c82.png)

Now it was my turn to guess the word, I failed and got 0 points. 

#### Feedback from Jay
After our quick playthrough I asked Jay for feedback about the application, things he liked, things he didn't like. He responded with the following. 'App werkt naar behoren' meaning, the app works like how it should work. He also said 'duidelijk maken dat je het verkloot hebt', meaning he wants it to be more clear when he made a mistake. Right now you lose a life, the letters shows, and you hear a fart sound effect. But I might reconsider how to show you made a mistake. 'instructies zijn duidelijk' this means he says the instructions are clear. Here's an example of an in-game construction.

*In the red square you see a instruction*
![image](https://user-images.githubusercontent.com/74303221/173932899-68e3a1e4-c588-4fcd-974b-212580a01e16.png)

A mistake I already made in the UX-Test is that I took a user that has already played it before on a whiteboard. So he did already know the basics of the game. Another thing he said was 'makkelijk te spelen', meaning its easy to play. And the last thing he said was how he like that the players can define the difficulty, if players are up for a real challenge they can choose harder words. In his words 'limiet ligt bij de gebruiker, je kan zelf bepalen hoe makkelijk of hoe moeilijk je het maakt'.

#### What now?
What do i do now? Do i adjust everything Jay said? No. I first want to do more UX-tests targeting different people, like different age, gender and culture. I think I might get more feedback like that. My idea is to apply the feedback I get multiple times of multiple people. If multiple people give me the same feedback its enough validation for me to update the game.

### Object Relational Mapping
In our GP we used an ORM for our menu-service. In our service we've created entities, with some annotations and configuration we set up that the entities we've created get created in a MySQL database. Here is an example of what an entity class looks like. 

![image](https://user-images.githubusercontent.com/74303221/173344401-af5e6d42-49b6-4505-95a2-c96be3813518.png)

This is what it looks like in MySQL if we run the application.

![image](https://user-images.githubusercontent.com/74303221/173344881-16332f66-b3d9-42ca-8dc5-958a8d745f00.png)

As you saw there's already data in it, we've done this by adding a data.sql file. In the red square you can see the lines of code that generate our data.

![image](https://user-images.githubusercontent.com/74303221/173345048-ed4d1e85-3cd3-4586-9eec-fdb036860ba1.png)

### Architecture
Looking for architecture? Click on the link below.

[Reverse Hangman Online Documentation - Architecture](https://github.com/Epic-Chainsaw-Massacre#architecture)


## Learning Outcome 2: Software Quality
*You use software **tooling and methodology** that continuously monitors and improve the software quality during software development.*

Clarification:

**Tooling and methodology**: Carry out, monitor and report on unit integration, regression and system tests, with attention for security and performance aspects, as well as applying static code analysis and code reviews.

### Testing
In this semester I have to make use of 4 types of tests, unit, integration, regression and system tests. If i have a good explanation for it I may decide to not use certain types of tests.

### Static Code Analysis
For code analysis i've made use of SonarCloud. I chose SonarCloud since a classmate of mine told me it is pretty easy to setup via SonarCloud. After a pull request to master, the SonarCloud code analysis get executed. Using code analysis i can easily find vulnerabilities in my code.

![image](https://user-images.githubusercontent.com/74303221/173247608-e802e311-4316-4a2a-96d0-318d8b2dcf75.png)

Right now I only got the SonarCloud code analysis working on 2 out of 4 repositories. My goal is to have code analysis in every repository, so all of my repositories will have better code. Update, I got it working on all 4 :D

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
I also added Continous Delivery to all of my repositories. This means that, after a pull request on the master everything gets deployed on dockerhub. From Docker desktop if I go to remote repositories I can indeed see that the images have been pushed to dockerhub.

![image](https://user-images.githubusercontent.com/74303221/173250305-8d6d2b01-faec-4ed3-bb0f-29a94ca0c52b.png)

But huge issue, they weren't getting deployed. To deploy all my applications I copy pasted the Dockerfile of a classmate of mine. This made 2/5 images actually run, but 3/5 weren't running. 

![image](https://user-images.githubusercontent.com/74303221/174109810-dde544a6-52ed-4f4e-a856-3ec8ac65bd68.png)

To fix this i probably have to change something in my dockerfile, one issue, since I copy pasted everything, I have no idea what's happening. I know why it stop's running. But I don't know how to fix it. So I decided to put a hard focus on learning docker.

#### Learning Docker
To learn docker I followed the [tutorial on Docker's website](https://docs.docker.com/get-started/). After learning the basics there about docker, I wanted to focus my actual problem. I didn't know how to setup a dockerfile. I tried looking up tutorials but everyone just breezes through the dockerfile without explaining it. Then I realized something. The docker error I got was always exactly the same. No matter what I did. If my dockerfile looked like the following
```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime
WORKDIR /src
COPY ["GameStatisticsService/GameStatisticsService.csproj", "GameStatisticsService/"]
ENTRYPOINT ["dotnet", "GameStatisticsService.dll"]
```
or if it looked like this
```
FROM mcr.microsoft.com/dotnet/sdk:6.0-focal AS build
WORKDIR /source
COPY . .
RUN dotnet restore "./GameStatisticsService/GameStatisticsService.csproj" --disable-parallel
RUN dotnet publish "./GameStatisticsService/GameStatisticsService.csproj" -c release -o /app --no-restore

# Run
FROM mcr.microsoft.com/dotnet/aspnet:6.0-focal
WORKDIR /app
COPY --from=build /app ./

ENTRYPOINT ["dotnet", "GameStatisticsService.dll"] 
```
I got the same error. That made me realize, I wasnt updating my local docker images. everything kept getting pushed to dockerhub, but if I ran them locally I kept running the 4 line dockerfile. Once i realized that everything was pretty easy to setup. Just look up for dockerfiles, copy paste, and everything runs in a compose file.

*Evidence of everything running*

https://user-images.githubusercontent.com/74303221/174286904-65b6127e-f612-4519-9a7a-3227df9b4956.mp4

[//]: # (### Failed to Fetch
Everything runs, great, but the api requests between my applications don't work. My frontend can't seem to reach my backend and vice versa. To fix this I will configure them on the same IP.)


## Learning Outcome 6: Design
*You translate (non-functional) requirements to extend existing (architectural) designs and can validate them using **multiple types of test techniques**.*

I've split this learning outcome into 2 parts. In this section I'll focuss more on the design. If you are looking for the requirements part of this learning outcome, have a look at the GP version of this learning outcome.

[Learning Outcome 6: Design](#learning-outcome-6-design)

### Architecture
Looking for architecture? Click on the link below.

[Reverse Hangman Online Documentation - Architecture](https://github.com/Epic-Chainsaw-Massacre#architecture)

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

### Researches
Researches are mentioned in the bottom of the document, click on the click to teleport there.

[Research](#research)

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

I did a small research to the other agile methods, I did this by searching multiple resources online. Usually about 3 to 6 websites.

### Kanban
I'll go briefly through the practises of the Kanban methodology. 

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

### Extreme Programming
Extreme programming, also known as XP, exists of short developement cycles wherin you define the requirements and assign them, its as if you set up a sprint right before it starts if you compare it to Scrum. Just like any other agile methodology, XP comes with some practises, 12 to be exact. Since 12 is quite a lot we'll split them in 4 groups.

![image](https://user-images.githubusercontent.com/74303221/173691785-a12e36de-e21f-44d2-8e9a-b12ff6729b6e.png)

#### Fine-scale feedback
Pair programming is one of the practises, that means when 2 people team up on one device. One of the 2 writes the code also called the 'Driver' while the other observes the code also called 'observer' or 'navigator'. The goal is that the observer gives feedback to the driver. Usually the roles get switched frequently. Another practise is the planning, you should plan together with the product owners when which products should be released, also should you guys as a team plan who works on what and when. In the second phase the product owner isn't evolved. Writing tests is also a practise pretty straight forward, write tests for your code. At last the product owner should always be contactable during the working process.

![image](https://user-images.githubusercontent.com/74303221/173691621-c0645897-1322-4b2e-b1f2-c3feff1aca6d.png)

#### Continuous process
in this section falls the practise the have everyone code on the same shared space and merge the code several times a day. Refactoring is also a part of all this. This means you improve the code without adding or removing functionality. As last its important to have releases thoughout the project. Small releases so that the product owner knows the current state of the project. Its also important that the code isnt from someone, the code is from the entire team. Everyone is allowed to make changes to the code. Everything should be writtin as simple as possible, if you have a funtionality with 100 lines of code that could be writtin in 60 lines of code you should shorten it. As last its important that everyone can read the code, inclusing people that don't code. Tou can achieve this be giving everything names that explain them selves as good as possible, for exmaple good variable names, good class names, good method names etcetera. 

#### Shared understanding
Use the same coding standards for exmaple code in the same language like dutch, english, german, im not talking about same coding language, altough that would also be pretty important if you work on the same piece lol. For another example lets look at C#, its pretty well known in C# that you do pascal casing on methods and start private fields with an underscore. 

#### Programmer welfare
its important that the developers dont work more than 40 hours a week. if there happens to be overtime one week it doesnt mean you can skip the overtime you did in the next week. Because XP consists of small processes. If you dont work for a while you can miss alot since the processes are so small.

### Waterfall
Just like lots of other agile methodologies, waterfall exists of making requirements, design (models), implementation, verification or testing and deployment and maintenance in this order. I'll explain them all briefly.

*Waterfall methodology flows down in this image like a waterfall :0*

![image](https://user-images.githubusercontent.com/74303221/173694949-4fab62c2-e7b1-46c5-a530-468a542b244f.png)

#### Requirements
In waterfall it's important to have all your requirements defined at the start. Also is it important to plan how long everything will take so you can tell the customer the costs by forehand.

#### Design Models
With design we aren't talking about the user interface, but stuff like class diagrams architecture models flow of the app stuff like that. After you've made these you can move on to the next part

*Example of a flow diagram, a flow diagram is one of the many diagrams that could be made in the design process*

![image](https://user-images.githubusercontent.com/74303221/173695265-858682df-bfa9-49dc-b5a2-0c57abe7b740.png)

#### implementation
In this phase the team codes the application. They write code based of the requirements.

#### Verification
Here the team tests their code to see if it does satisfy the requirements.

#### Deployment and Maintenance
After deploying the project, the team should maintain the project. If any bug/issue gets found, they solve it.

## Learning Outcome 5: Cultural Differences and Ethics
*You **recognize** and **take into account** cultural differences when working with multi-site teams and are aware of ethical aspects in software development.*

Clarification:

**Recognize**:  Recognition is based on theoretically substantiated awareness of cultural differences and ethical aspects in software engineering.

**Take into account**: Adapt your communication, working, and behaviour styles to work with other developers from different cultures; 
Address one of the standard Programming Ethical Guidelines (e.g., ACM Code of Ethics and Professional Conduct) in your work.  

### Cultural Differences
For this section I will answer 5 questions.

#### What is culture? 
Culture is shortly, activities, behaviour and practises of a group. For example the dutch are very direct. Its important to take this into account, since usually they don't try to be mean but it sounds like they try to be mean a lot. but thats just how they are. Another example of culture is that the turkish people organize a big party if they marry.

#### Which are well-known dimensions on cultural differences? 
the 4 dimensions are power distance (PDI), individualism (IDV), uncertainty avoidance (UAI) and masculinity (MAS). I'll describe them down here.

##### Power Distance (PDI)
Power distance is the degree a society accept or rejects unequal power distribution. For example in the netherlands everyone behaves another equally. But for example in Japan they show lots of respect for older people, people with a higher status and people with titles. You can already see how this could go wrong. If a young dutch developer, and an older japanese developer work together. The dutch might behave unrespetfull in the eyes of the japanese man. This is why its important to understand each others' culture.

*In this image you see the differences between japanase bows, these get mixed up a lot. Usuaully people think there is just one bow, but there are multiple.*
![image](https://user-images.githubusercontent.com/74303221/173791109-7a9a2b23-c718-443a-9434-920864cb93a3.png)

##### Individualism (IDV)
Individualism is the degree a human prioritizes his own, indivual accomplishments. the counterpart is collectivism, this is that you care more about the group accomplishments

##### Uncertainty Avoidance (UAI)
Uncertainty Avoidance is the degree a society tolerates risks. An example of a country with a high uncertainty avoidance culture is France. this means that if you have a french worker in your group, he will expect structure and predictability.

##### Masculinity-Femininity (MAS)
Masculinity-Femininity is the degree a society values assertiveness and materialism versus feelings, relationships, and quality of life. I found an interesting table where they put masculinity against feminity. This table explains it better than me so have a look.

![image](https://user-images.githubusercontent.com/74303221/173784309-b9497c83-48c9-418b-9be4-d79cdc288d2c.png)

##### Can you give examples for cultural differences that you have experienced in your study or life? How do you explain these differences?
Actually, no. I have never really experienced these cultural differences at work nor did I experience them at school. This is probably because im very integrated in the dutch culture. The only really difference i noticed that i take into account, is that sometimes people with autism get on my nerves. But I try to ignore it since they can't do a thing about it. And till now its going pretty good, but that's not a cultural difference, maybe i have autism too.

##### What is your culture?
My culture in short consists of a few practises and norms. Every friday i try to go to the mosque for my religion. I have respect for everyone, doesn't matter if its a kid that's 4 years old or an elder, i threat them both the same most respectful way i can. Justice is somthing i find very important, threat others with justice. Threat others like you want to be threated, thats like on of the most important sentence in life for me. I like a good structure, i'm **usually** good at planning. I dont like it if theres no structure. i can tell more and give more examples, but everything i want to write down ends up with 'threat others like you want to be threated'. for example, if i dont help my sis with moving out. I wouldn't expect her to help me moving out. And at last parents come before anything.

##### What did you  do to improve the group communications with respect to cultural differences? 
Since i cant give examples in the group project ill take examples of real life. If i see a family member i always try to start the conversation by saying 'salaam wa alaikum'. Its just a respectfull way to greet muslims. If someone says it to you, you respond with 'Wa alaykumu s-salam'. A huge cultural difference I'm confronted with in the netherlands is going out to party and drinking beer and all that. I don't drink, I have no interest in it and its also forbidden in my religion. going out to a club looks very wrong to me so i always pass. Just the stories you hear the videos you see. To me it all feels very wrong and it doesnt fit into my culture.

### Ethics
I've split this section up in 7 questions.

#### What is ethics in software engineering?
Ethics is software engineering mean that, engineers should think about the consequences of their product. They should avoid giving a group of people bad consequences.

#### Why is ethics important in software engineering? 
Over the years the impact of software on our lives has grown on an insane level. everywhere around you is software. Engineers should take ethics into account, because they could mess up people their lives. How you would ask? For exmaple lets look at factories. Over the years more and more processes in factories got automised. This resulted in people losing their jobs. Losing your job unexpectedly as an adult could be very fatal since you have lots of charges you gotta pay, and as an adult its not always easy to find a job.

#### What do you have to do as a software engineer to address ethical aspects in your work? 
As a software engineer you should inform your product owner about the negative aspects/consequences of your work.

#### How do you know that your ethical considerations match with those of other software engineers? 
To understand other engineers their view you, for example in your team. Everyone can share their view and opinions about ethics and the ethical consequences of the project.

#### Which ethical aspects play a role in your project? + Do you foresee ethical conflicts caused by your software? What kind of?  
In our group project the biggest ethical aspect is the following. We take a process that gets exectued by humans, waiters to be more specific. Waiters wander arround and take orders from the customers, they bring the order to the kitchen, and finally they serve out the food. So actually a waiter has 3 tasks. Lets we build an application for a restaurant where they have 3 waiters. each waiter has its own task. one waiter gets orders, one brings orders to the ktichen, and one serves out the food. If the fictional restaurant i just described uses our application it woulf have the following results. 2 out of 3 waiters would be unnecessary. since the orders get taken automatically, and the orders get to the kitchen automatically. this means only the food has to get served out. ethically this is a bad application for the waiter since it creates a decent chance of them losing their job.

#### Can you do something to avoid or minimize these conflicts? 
We could build the application slightly different, so that the customers dont use the app but the waiters use the app. In our fictional restaurant app it saves one waiter from its job. But in the end we build the application to automise the process. What's the use in having the waiters do a task with our application, if you can also give it in the hands of the customers. This is a dillemaa you can think about for quite a while. for example, does the product owner just wanna get rid of the employees to save money? will he use the employees for something different. This ethical problem summons lots of questions. So yes you could avoid the conflict by giving waiters another task in the restaurant or building the app in a way that they have to use it. Or you minimize it by keeping a part automised and a part not automised. But how usefull is that really.

*image of a waiter using our application to take an order*
![image](https://user-images.githubusercontent.com/74303221/173804913-5b326448-4a96-43f9-9d47-b3c44deb10eb.png)

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

### Researches
Researches are mentioned down below, click the link to go there.

[Research](#research)

# Ranknir
Ranknir is a discord bot I made for fun. The discord I made it for showed a list of players in a certain clan and their rank points. The thing that bugged me was, they only showed all players their 1v1 stats. I thought this wasn't fair for the hardcore 2v2 players so I decided to make it myself.

*The 1v1 list that already existed in the discord*

![image](https://user-images.githubusercontent.com/74303221/174409799-1a1b909b-1f41-48f7-b631-3a998bc491e0.png)

*The 2v2 list that I made, as you can see it fits the style of the already existing one*

![image](https://user-images.githubusercontent.com/74303221/174409895-5fe193b8-2532-4f58-a3d8-1e2c89a86ef1.png)


To accomplish this, I first needed an API key of the game in question, Brawlhalla. I looked up how to get an API key and it was pretty clear, you just had to mail them explaining why you want the API key and what your plans are. So I explained exactly that.

*Me asking the game people behind Brawlhalla for an API key*

![image](https://user-images.githubusercontent.com/74303221/174409298-7444b8fd-67bb-4f8b-a270-89bc46bf113a.png)

*Them approving the request, and giving me an API key*

![image](https://user-images.githubusercontent.com/74303221/174409420-2466e854-d71c-4a8f-b54d-6f40dc0a55d1.png)

The code isn't too interesting, I improved my python skills. Besides that did it give me a good practise with JSON data. I thought this was a pretty interesting project to execute, also to show in my portfolio. The entire proces of mailing a popular game, them responding, all that, it was a fun and cool project.

[Ranknir Documentation](https://github.com/CrossyChainsaw/Ranknir)

# Money Squadron Virus
A less interesting project I worked on this semester is Money Squadron Virus. MSV is a meme bot created in python. Other than practising python this project didn't really add up to my skills as an software engineer, but in the end I did spend quite some time on this project, maintaining it, so I thought it deserved a spot in here. 

Here are a few of my favourite memes.

![image](https://user-images.githubusercontent.com/74303221/174412150-4f81bda6-7937-4654-b9d2-e1a5b70b312a.png)

![image](https://user-images.githubusercontent.com/74303221/174412110-13f5d68d-fa67-41d0-8d01-0b00c75ae59c.png)

![test](https://i.imgur.com/nJ1Ag2V.gif)

![image](https://user-images.githubusercontent.com/74303221/174411850-7b02c8df-4828-4b00-a0dc-f5db604aa88b.png)

![image](https://user-images.githubusercontent.com/74303221/174411832-1b76623e-5584-4f51-8b5a-23a8cbceb259.png)

[![image](https://user-images.githubusercontent.com/74303221/174412423-5b6d0471-9ec9-4a55-a268-0d4999c7213b.png)](https://www.youtube.com/watch?v=yQQNZTEnl6o)


Everytime I want to add a meme I have to edit the code, I tried to import [Imgur](https://imgur.com/a/l2wygcj) in my python code, so that I only have to add a meme to imgur and my application would automatically pull the image, but no succes sadly. Bot was made to mock a discord server called Money Squadron. But the hype came to an end. Bot is still up tho. For more information check out the documentation.

[Money Squadron Virus Documentation](https://github.com/CrossyChainsaw/MoneySquadronVirus)

# Research

## Which database is most suitable for my application?
For this research I made use of the [DOT framework](https://ictresearchmethods.nl/The_DOT_Framework).

**What**: I want to research which database fit my application the best.

**Why**: Instead of choosing a random database, I'd like to know which database fits my application the best. Because if you realize you chose the wrong database in the middle of the project it might cost a lot of time, effort and money(for a company, I'm just a student).

**How**: Find multiple articles about how to choose the right database for your application, validate them, and use them for my project.

I've put the document with the research in it in my portfolio, Because its so big you have to download it.

[Database Research](https://github.com/CrossyChainsaw/Portfolio/tree/master/Database%20Research)

## How do I protect the URLs my microservices use to communicate?
First I asked myself 3 questions. What do i wanna research, why do i wanna research it, and how do i wanna research it.

**What**: I want to research how I can protect my URLs against DDoS attacks.

**Why**: If i don't protect the URLs, people can DDoS attack my services, which slow down my application or can even take it down.

**How**: Trying to understand what all the risks are of not protecting the URLs, and finding out how to protect the URLs making use of reliable sources and validation.

I've put the document with the research in it in my portfolio.

[Security Research](https://github.com/CrossyChainsaw/Portfolio/blob/master/Security%20Research/DDoS%20URL%20Research.pdf)

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

## UX-Tests
Do more UX-tests, start earlier, target multiple kinds of people. I let a user test my application that already had a good understanding of the game, that comes with pros and cons. Since he already knows whats coming, he can be more ciritcal, but because he already knows it, everything is clear to him. So UX-testing 1 person definitely won't do the job

My teacher also gave me feedback to observer my user. Try to look at his behaviour. From someone's behaviour you can also conceive information. Do confirm your conceptions with your user. Like this my UX-tests will be more efficient.

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

## Wednesday
I usually did nothing on wednesday. This was because me and my mom watched a series that always dropped at Tuesday 23:30. The episode usually lasted like 150 minutes. so I would always sleep way too late. Since I still wanted to sleep properly I woke up pretty late. This made me tired the entire day. And then I did nothing the entire day. This is how every wednesday went. This was very unprofessional behaviour of me.

## Videos in Portfolio
I just absolutely forgot this was a thing sadly, The last 3 days someone reminded me it was a thing and i added for example docker running in a video so you can see its not fake. but other than that I wanted to focus more on finishing everything instead of taking videos of everything. 

# Epilogue
In the end it was an ok semester. I've had semesters that were more fun. Everything this semester just went vague or unstructured. I didn't necissarily reached/learned cool things, neither did I make cool things. Let's hope I don't have to do it all over again.

Kaan Gögcay
