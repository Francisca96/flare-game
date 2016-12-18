# Fifth Report - ESOF FEUP

[![BCH compliance](https://bettercodehub.com/edge/badge/andrebreis/flare-engine)](https://bettercodehub.com)

## Index
1. [Software Maintenance/Evolution - Introduction](#intro)
2. [Software Maintainability - SIG metrics](#sig)
3. [Better Code Hub analysis](#bch)
4. [Evolution Process](#evo)  
  i. [Identifying a possible feature](#ident)  
  ii. [Implementation of the feature](#imp)  
  iii. [Submission of the feature](#sub)  
5. [Contribution](#cont)
  
  
 ##**Software Maintenance/Evolution - Introduction** <a name ="intro"></a>
 
 After analysing this project's tests, we aim to analyze the software maintanability and evolution of Flare ([game](https://github.com/clintbellanger/flare-game) and [engine](https://github.com/clintbellanger/flare-engine)) and to improve it's functionality, by adding a new feature. In this report we will present some interesting metrics regarding the project, and will describe what feature we chose to make and how we implemented it.
 
 ##**Software Maintainability - SIG metrics** <a name= "sig"></a>
 
 [Software maintainability](http://www.castsoftware.com/glossary/software-maintainability) is defined as the degree to which an application is understood, repaired, or enhanced. Software maintainability is important because it consumes range between 40% to 80% of software costs in a project. Bellow we will present some curious metrics from the Software Improvement Group (SIG) of [Better Code Hub](https://bettercodehub.com). Better Code Hub is a web-based source code analysis service that checks the database for compliance with the ten guidelines presented in _Building Maintainable Software: Ten Guidelines for Future-Proof Code_ (BMS).
 
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/10guidelines.PNG)
  
  
  ##**Better Code Hub analysis** <a name= "bch"></a>
  
 
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/2.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/3.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/4.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/5.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/6.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/7.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/8.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/9.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/10.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/11.png)
  ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/12.png)
  

 ##**Evolution Proccess** <a name= "evo"></a>
 ###**Identifying a possible feature** <a name= "ident"></a>

  During our testing of the Flare Game, we found out that to users with lower mouse sensivity it was boring to turn off the sound, since it needed to set both sliders all the way to the left.

  We thought that, like many other applications, there could be a button that would toggle the sound - we did this with a checkbox.


 ###**Implementation of the feature** <a name= "imp"></a>
 
 To locate the parts in the source code that needed to be modified, we searched within the source code files for menus for the "Audio" word, since what we wanted to add was in the Audio tab of the configurations menu.  
 Then we found the __GameStateConfigBase__ header and source files, that contained most of the code envolving the configurations menu. As these files' code is very straightforward and easy to read, it was just a step until the configurations menu had the operating checkboxes.  
 After that, we needed to keep the checkboxes checked after closing the menu, that is, saving the checkboxes state, and while searching for that we found the _saveSettings_ function, which sent us to the __Settings__ header and source files, where we refactored our code a bit so it would save the checkboxes state and accept a default value coming from configuration files.
 The last step was adding the checkboxes to the game pause menu, that we found on the __MenuExit__ header and source files. As the code in these files was pretty similar to the __GameStateConfigBase__ files, it was easy to implement the checkboxes here too.  
 
 ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/main_menu_changes.png)
 ![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/pause_menu_changes.png)
 
 We leave a note that the similarity between these two files should cause a refactor so that the code can be shared between these files. However, we did not want to do this because it would make our pull request bigger and it would stop being focused on implementing one feature - it would implement a feature and refactor code - and this goes against the repository contribution convention (It's better to make many small pull requests than a big pull request).

  ###**Submission of the feature** <a name= "sub"></a>

  Our pull request can be found [here](https://github.com/clintbellanger/flare-engine/pull/1479).
  
##**Contribution** <a name ="contrib"></a>

[Andre Reis](https://github.com/andrebreis) -- 33%  
[Francisca Pauperio](https://github.com/Francisca96) -- 33%  
[Joao Chaves](https://github.com/JoaoChaves96) -- 33%  
