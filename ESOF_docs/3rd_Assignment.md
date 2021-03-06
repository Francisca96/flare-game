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

In this report, we will be presenting the 4 views regarding this view model:

* **Logical View**: is concerned with the functionality that the system provides to end-users. UML diagrams used to represent the logical view include activity diagrams, class diagrams, and state diagrams.

* **Implementation View**: illustrates a system from a programmer's perspective and is concerned with software management. This view is also known as the implementation view. It uses the UML Component diagram to describe system components. UML Diagrams used to represent the development view include the Package diagram.

* **Process View**: deals with the dynamic aspects of the system, explains the system processes and how they communicate, and focuses on the runtime behavior of the system. The process view addresses concurrency, distribution, integrators, performance, and scalability, etc. UML diagrams to represent process view include the activity diagram.

* **Deployment View**: depicts the system from a system engineer's point of view. It is concerned with the topology of software components on the physical layer as well as the physical connections between these components. This view is also known as the deployment view. UML diagrams used to represent the physical view include the deployment diagram.



##**Logical View** <a name ="log"></a>

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

As we can see, the diagram is simple because this is an offline game. Therefore we don't need more than one device to run it. Through the diagram it is possible to understand that flare-game can be played in several devices and operating systems. Originally, the game was only available to the PC (Windows and Linux) but, recently, the contributors started to develop an android and iOS version of the game. The app can be executing by running the correspondent scripts of each platform.


