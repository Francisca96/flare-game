# Third Report - ESOF FEUP

## Index
1. [Introduction to Software Architecture and the 4+1 Architectural View Model](#intro)
2. [Logical View](#log)
3. [Implementation View](#imp)
4. [Process View](#pro)
5. [Deployment View](#dep)

##**Introduction to Software Architecture and the 4+1 Architectural View Model** <a name ="intro"></a>

This report aims to explain some aspects relating the software architecture of the Flare Game/Flare Engine projects. This software architecture is based on the [4+1 Mode of Software Architecture](http://cic.puj.edu.co/wiki/lib/exe/fetch.php?media=materias:mazeiar-kruchten-4_1.pdf).

According to this view model, the views are used to describe the system from the viewpoint of different stakeholders, such as end-users, developers and project managers. The four views of the model are logical, implementation, process and deployment view. The aditional view (+1) is related with the [use-cases](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/use_case.PNG), which diagram was already presented on the [last report](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/2nd_Assignment.md).

![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/4%2B1model.png)

In this report, we will be presenting the 4 views regarding this view model.



##**Logical View** <a name ="log"></a>

This kind of view concerns the functionality that the language provides to the end-user. The UML diagrams that can be used to represent the logical view are: Sequence Diagram, Communication Diagram and Class Diagram.

It is important to notice that, in this view, we focused mostly on the game, since the quantity and diversity of the modules that exist on the engine reduce the importance of their architecture.

![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/logical_view.png)

Note: In this diagram we opted to use defined groups of classes as packages (as we did in the last assignment's domain model), because there aren't packages in c++ projects.



##**Implementation View** <a name ="imp"></a>

Next is the analysis of the implementation view of the project. In this view, we detail the main components and interaction between in the context of the availability or use of interface by them.

![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/implementation_view.png)

As we can see, the only interaction that the game does is with the interface provided by the engine. ON the other hand, the egnine deals with all the rest. It provides an API for the modules (in order to increase their funcitonality without endangering the consistency of the game) and uses the interface "Context" in which take place the necessary dependencies that make the game possible.


##**Process View** <a name ="pro"></a>

Through the process view diagram we can easily understand the sequence of processes available in a game session.

![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/process_view.png)

As we can see, the start of the game initiates the engine, that creates the context. The context is responsible for interacting with all the other components of the game, the Graphics, GUI, World, Input and Module Loader. The next step, is to initialize the Menu GUI. From them, the user can either start a new game or end the app. In the game, the user interact with all the context components, because they are all necessary to play the game. From the game, the user can end the app or engage in another game, going back to the Menu GUI.



##**Deployment View** <a name ="dep"></a>

The deployment view UML models the physic distribution of artifacts in nodes.

![Image](https://github.com/Francisca96/flare-game/blob/master/ESOF_docs/res/deployment_view.jpg)


