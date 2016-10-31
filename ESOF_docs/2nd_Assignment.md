# Second Report  ESOF FEUP

## Index

1. [Requirements: Introduction, Purpose/Scope, and Description](#intro)
2. [Specific Requirements and Features](#req)  
  1.[Functional requirements](#func)  
  2.[Non-functional requirements](#non)
3. [Use Cases](#use)
4. [Domain Model](#dom)


##**Requirements: Introduction, Purpose/Scope, and Description** <a name ="intro"></a>

Flare Game is a game based on Flare Engine which was basically designed as a simple basis to create multiple free RPG 2D games. The main requirement of the engine was that it was built so that, to create a game, you would only need to change configuration files.  
After this, the developers created a [TO-DO](http://flarerpg.org/todo) list with the requirements they had planned for the engine and game. New features were added to this list with appearances of user requests or GitHub issues that pointed out bugs.  
The main factor in the decision of which issues/user requests should be listed as a requirement on the TO-DO list was the main developer's opinion on whether it was fulcral to the engine or it was unnecessary. 

##**Specific Requirements and Features** <a name ="req"></a>
###**Functional requirements** <a name ="func"></a>

Flare Game should be abstract enough to be able to allow the creation of an engine (Flare Engine) with the basis of this game.
Flare Engine should be a reusable engine able to create multiple different RPG games.  
Flare Engine should be powerful enough to create multiple games without the need of extra code, only changing configuration files.

###**Non-functional requirements** <a name ="non"></a>

Flare Engine code should be written with the C++ programming language.  
Flare Engine shall be an Open Source project, as well as all public games created with it.

##**Use Cases** <a name ="use"></a>

![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/use_case.PNG)

##**Domain Model** <a name ="dom"></a>

As the Flare Game project does not contain any code, only configuration files for the engine, and the engine is a project with classes too specific and not related at all with usability, we couldn't build a Domain Model for this project.
