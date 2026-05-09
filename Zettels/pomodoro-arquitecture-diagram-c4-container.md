---
id: 20250824223321
tags: 
---

---

# Pomodoro Arquitecture Diagram c4 container
 

## C4 Client component
```mermaid
C4Container
title Pomodoro Arquitecture container
    
    System_Boundary(Persons, "Persons"){
    Person(User, "User", "The person who manages his time using pomodoro technique")
    
    Rel(User, CLI, "uses")
    Rel(User, Web, "uses")
    }
    
    System_Boundary(ClientApps, "Pomodoro Client Apps") {
	Container(CLI, "CLI", "The CLI adapter")
	Container(Web, "Web", "The web adapter")
	Container(Controller, "Controller", "Shared logic for clients<br> notify clients finished pomodoro")
	ContainerDb(LocalDB, "Local DB", "Stores session <br> data & logs")
	Container(Sync, "Sync", "Sync client localdb <br> with the API")
	
	Rel(CLI, Controller, "uses")
	Rel(Web, Controller, "uses")
	
	Rel(Controller, LocalDB, "Sends data & logs")
	
	Rel(Sync, LocalDB, "Reads data & logs")
	
	Rel(Controller, Auth, "User auth request <br> recibes user profile")
    }
    Rel(Sync, APIGateway, "sync data <br> upload logs")
    
    System_Boundary(firebase, "Firebase"){
    Container_Ext(Auth, "Auth", "Auth service <br> for all clients")
    }
    
     System_Boundary(PomodoroSystem, "Pomodoro System"){
    Container(APIGateway, "API Gateway", "Routes request to <br> pomodoro system microservices")
    Rel(Controller, APIGateway, "saves/request user profile")
    }
    
    System_Boundary(Logging, "Logging Backend"){
    Container_Ext(Logging, "Logging", "Recives logs from<br>pomodoro system and client apps")
    Rel(APIGateway, Logging, "Logs client logs")
    }
```


## Backend c4 container diagram
```mermaid
C4Container
    title Pomodoro Arquitecture container
    
    
    System_Boundary(PomodoroSystem, "Pomodoro System"){
    
    System_Boundary(UserBackend, "User Backend"){
    Container(Users, "Users", "Users profile")
    ContainerDb_Ext(UsersBD, "UsersBD", "Users firestore BD")
    
    Rel(Users, UsersBD, "stores users")
    
    }
    
    Container(APIGateway, "API Gateway", "Routes request to <br> pomodoro system microservices")
    Rel(APIGateway, Tasks, "calls")
    Rel(APIGateway, Analytics, "calls")
    Rel(APIGateway, Config, "calls")
    Rel(APIGateway, Users, "saves/read profile")
    
    System_Boundary(PomodoroBackend, "Pomodoro Backend"){
	Container(Analytics, "Analytics", "stores pomodoro data <br> filtered by a date or date range")
	ContainerDb_Ext(AnalyticsBD, "AnalyticsBD", "Analytics firestore BD")
	Container(Config, "Config", "Pomodoro timer <br> duration config")
	ContainerDb_Ext(ConfigBD, "ConfigBD", "Config firestore BD")
	
	Container(Tasks, "Tasks", "Tasks & projects")
	ContainerDb_Ext(TasksBD, "TasksBD", "Tasks firestore BD")
    
    Rel(Tasks, TasksBD, "stores Tasks")
    
    }
    
    Rel(Analytics, AnalyticsBD, "stores analytics")
    Rel(Config, ConfigBD, "stores config")
    
    %% Logging %%
    Rel(Config, Logging, "sends logs")
    Rel(Analytics, Logging, "sends logs")
    Rel(Users, Logging, "sends logs")
    Rel(Tasks, Logging, "sends logs")
    }
    
    System_Boundary(Logging, "Logging Backend"){
    Container_Ext(Logging, "Logging", "Recives logs from<br>pomodoro system and client apps")
    }
    
    
```

# More info
- Arquitectura offline-first
## Client
- Stores and reads session in localDB
- The local pomodoro config will be used on client and synced in microservices
### Sync
- syncs between localDB and microservices
- Client components have his own timestamp: So all the events for diferent clients can be synced without problems, using Last-write-wins

## Backend
- Al microservices stores the uuid that the client send
- firebase for store the db
### Analytics
- Stores pomodoro duration, started and ended timestamp, message
- Filter by start / end timestamp

## Config
- microservice for store user config for sync between different clients

### Logging
- Recives pomodoro system microservices logs
- Recives logs from clients:
	- clients store logs on localBd
	- sync reads logs from bd 
	- sync sends logs to APIGateway
	- APIGateway sends logs to logging microservice


---

## Connections:
- [[]]

---

## Questions for Further Exploration:
- 