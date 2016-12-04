# Fourth Report - ESOF FEUP

## Index
1. [Verification and Validation - Introduction](#intro)
2. [Software Testability and reviews](#test_rev)  
  i. [Controllability](#cont)  
  ii. [Observability](#obs)  
  iii. [Isolateability](#iso)  
  iv. [Separation of concerns](#conc)    
  v. [Understandability](#und)  
  vi. [Heterogeneity](#het)  
3. [Test Statistics and analytics](#test)
4. [Bug Identification](#bug)

##**Verification and Validation - Introduction** <a name ="intro"></a>

In this report, we will analyze flare-game and flare-engine per its current state with respect to verification and validation.
In the first part, we will talk about the testability of the game, i.e., how easy it is to test the different components of the game, and how the test methods could have been enhanced. In the second section, we will report the test statistics and analytics, regarding the game and the engine. Lastly, we will talk the process of identification of a bug reported in the project.


##**Software Testability and reviews** <a name ="test_rev"></a>

If we analyze the game and the engine, we can conclude that in this project there isn’t any unit test.
So, we asked the main contributor of the project if they had any tests at all. His answer was that, in the beginning, he was developing solo and almost never broke the build. He tested along the way and fixed any known bugs before moving on. That happened because he knew the entire codebase. Although there were no tests, he said that, when the project started to have more contributors, they did some informal kinds of testing. When they were working on core features, they did a lot of cross-testing to each other’s features before checking into the main code base. Of course, GitHub and Pull Requests made that easy. Also, they set up an automatic build checker that would report any warnings and errors anytime new code was added. They used tools like [Valgrind](http://valgrind.org/) to check the general health of the code for things like memory leaks and buffer overruns.
In the end, he admitted that when the project started to grow, new programmers didn’t automatically know how all parts worked together, so a test suite would be great for catching mistakes. 

####**Controllability** <a name ="cont"></a>

In terms of the controllability of the components that are under test, it depends on each component. We can have two approaches, one if the component is an engine component, and other, if the component is a game component.
If it is about an engine component, it is most likely to have reduced controllability, because the engine can interact with a variety of games. Therefore, it is harder to predict all the possible outcomes.
If the component under test is a game component, it should present higher controllability, because its interaction is limited to the other components of the same game and to the engine. 
Besides that, in this project there is no way of testing the components of the game and the engine separately, because one can’t run without the other. This is bad, because it makes testing a lot harder. A solution to this problem would be making the game and the engine abstract. If this happened, we would be able to test the engine individually.

####**Observability** <a name ="obs"></a>

As said before, Flare only uses one tool for testing named Valgrind. Valgrind is an instrumentation framework for building dynamic analysis tools. The problem with this tool is that it isn't unit testing. Unit tests are atomic tests, that test each functionality by itself, theorically independently from any other functionality. With Valgrind this doesn´t work. It can only test components as you play the game. For example, if the Play Button didn’t work, Unit Testing would return an error in this component but would still run and test all other components. On the other hand, Valgrind would return the error on the Play Button, but wouldn´t test all other components, because we couldn’t run the game.
So, we can conclude that the observability of the results is very bad, because the used tool doesn´t allow to test every component independently of any other components. We would need to run the game long enough to test all its components and if any component fails, all the components dependent of that one can't be tested.


####**Isolateability** <a name ="iso"></a>

Isolateability is related with controllability. We can say that it is not correct to determine the isolateability in Flare, because there is no way to test each component individually. First, because Valgrind doesn’t allow it, and second because, as said before, the engine and the game only work as one, and we can’t test one without the other.

####**Separation of concerns** <a name ="conc"></a>

In terms of code organization, the separation of concerns is well defined, as mentioned in the last report.
In terms of testing, once again, it is not well defined, because we need to mix the game and the engine to be able to test the components.

####**Understandabilty** <a name ="und"></a>

All modules on Flare are well documented. Moreover, this is a pre-requisite specified on a [Codingstyle.txt](https://github.com/clintbellanger/flare-engine/blob/master/Codingstyle.txt) file on the engine. The code is documented using Javadoc style comments on the functions, especially if they are non-obvious. Every submission that doesn’t respect the requisites on this file is at risk of being rejected.

####**Heterogeneity** <a name ="het"></a>

Flare is a project with some heterogeneity, in a way it uses some external technologies to make the game possible.  The main libraries used are the [2.0 Development Libraries for SDL](http://www.libsdl.org/download-2.0.php):

* **[SDL_image](https://www.libsdl.org/projects/SDL_image/)**: an image file loading library that loads images as SDL surfaces;

* **[SDL_mixer](https://www.libsdl.org/projects/SDL_mixer/)**: a sample multi-channel audio mixer library;

* **[SDL_tff](https://www.libsdl.org/projects/SDL_ttf/)**: a sample library which allows the user to use TrueType fonts in SDL applications.

##**Test Statistics and analytics** <a name ="test"></a>

In this topic, we will analyse all the statistics collected either in the game or in the engine.

As we said before, none of the game components have tests (neither the game or the engine), so the coverage of the tests is null. So we based our analitics in Codacy results, that is a code reviewer.

![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/percentages_engine.png)
![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/percentages_game.png)

The first image, the one with an A on the top, is about engine and the other with a B has the percentages about flare game. Basing ourselves in this percentages, we can prove stuff witch we have previously stated. 
The main developer told us, in the first e-mail, that he doesn't need tests while he was coding alone. As we can see, both components have excellent quality pointers, even without develop any tests. So he was not very wrong.

Despite the documentation field is empty ("no patterns") the code is documented in javadoc. The code reviewer that we used also couldn't analyse the code complexity. In the unused code field we can note an high difference between both components (engine - 99%/ game - 0%), this is only for one reason, like we have said in other assignments, the flare-game does not have code.


##**Bug Identification** <a name ="bug"></a>

For this assignment, we were supposed to discover and correct a bug (an error, something that is unexpected behaviour) on the Flare-Game + Flare-Engine application.  
When you have a big and correctly working project like Flare, finding a bug shouldn't be an easy task. Despite that, after some manual testing (in another words, playing the game), we found out that for most environments, in the character menu, the characteristic (Mental, Physical, Defense,..) labels and buttons weren't being placed correctly - they were overlapping each other in the top left corner of the menu.  
Unfortunately enough, this bug was corrected while we were studying the codebase to find out how to correct it - on this [commit](https://github.com/clintbellanger/flare-engine/commit/2b7f9fbaab4ba67c6b7bc7ec7d2be7bbd2a048f8).  
Unfortunately, even though all the testing we did (trying to crash the game in all ways possible), we couldn't find another bug. While there are some issues with the bug label open on the Flare-Engine repository, we found out that they are open but the bugs are fixed, there just wasn't the effort to close the issues.
