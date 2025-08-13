Understanding Akka Typed Actors: A Simple Example
This report explains a small Akka Typed Actors project in Java. The project demonstrates actor creation, message passing, actor hierarchy, and scheduled messaging. It is designed for those new to Akka to understand core concepts by example.

Project Overview
The project models a simple actor system with a root actor managing two child actors. Messages are sent as strings or integers, which are forwarded to specific child actors. The system also schedules periodic messages using Akka’s built-in scheduler.
Actor Hierarchy and Messages
RootActor
•	The root actor (RootActor) acts as a supervisor and message router.
•	It creates two child actors: ChildActor1 and ChildActor2.
•	It receives messages of types String, Integer, Message1, and Message2.
•	Based on message type, it forwards to the corresponding child actor.

Child Actors
•	ChildActor1 handles messages implementing Command1 interface. It specifically processes Message1 objects that carry a string message.
•	ChildActor2 handles messages implementing Command2 interface. It processes Message2 objects carrying an integer number.

Messages and Commands
•	Command1 and Command2 are marker interfaces for message types.
•	Message1 contains a string (msg) and implements Command1.
•	Message2 contains an integer (number) and implements Command2.

Main Application and Scheduling
The Main class creates the ActorSystem with RootActor as the root behavior. It immediately sends a string and an integer message to the system, demonstrating message routing.

Then, it schedules periodic messages every 5 seconds (after an initial 3-second delay) that send a Message1 and Message2 to the system repeatedly. After 5 executions, it gracefully terminates the system.

Summary and Key Learnings
•	ActorSystem represents the top-level container for all actors.
•	RootActor creates and supervises child actors.
•	Child actors handle specific message types with their own logic.
•	Messages are immutable objects implementing marker interfaces to allow strong typing.
•	Akka’s scheduler allows periodic tasks that send messages on a timed basis.
•	The actor model enables safe, asynchronous message passing and concurrency without explicit locks.

How to Use
1.	Clone the repository.
2.	Build the project with Maven or your favorite Java build tool.
3.	Run the Main class to see actors receiving messages and scheduled calls in the console.
4.	Explore modifying or extending actors and messages to understand deeper concepts.

