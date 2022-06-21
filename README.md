# Event Stream Application Workbench

## Overview

ESAW helps you design applications built around Event Streams like you find in [Apache Kafka](https://kafka.apache.org). Traditional applications are typically modeled around domain objects and actions on those obects.  An alternative way to look at applications is as an ongoing stream of events.  For example, a user creates an account, the account is verified, and the user then makes a purchase.  
| Action | Legacy Application | Event Stream Application |
| ---- | ----| ---- |
| User creates an account | User Object created and persisted | USER.created Event |
| User's account is verified | User Object is updated as 'verified' | USER.verified Event |
| User makes a purchase | Purchase object is created and persisted | ORDER.created Event |

A key concept in Event Stream application is "the log is truth." 

## ESAW Concepts

### Application

At the highest level of abstraction, you are creating what we call an application.  Usually what we consider an application is the output of a single team of developers.

Applications are a collection of [Processors](#processors) which consume inputs and create outputs.

An application has the following properties...

| Name | Purpose |
| ---- | ------- |
| Name | The application name |
| Processor Repositories | List of repositories that define processors used by this application. |
| Event Definition Repositories | List of repositories that hold event definitions used by the processors in the application. |
| Payload Definition Repositories | List of repositories that hold payload definitions used by processors and event definitions. |

An application may have local processors, event definitions and payload definitions or it may share those entities from other applications.

### Processors

Processors are the code that do things.  You can think of these as microservices.  A processor will have an input and an output.  Input may be either a REST actions like POST, PUT, or DELETE, or it may be an Event Topic subscription.  Output may be either a REST GET or an Event Topic production.  The Processor code processes input and produces output.

### Event Definitions

Events are the entities that are put on the Event Stream.  They have a type, name and payload.

### Payload Definitions

Payloads are the actual data entities carried by Events and worked on by Processors.  These are generally JSON objects but need not be.

## Development

### Installing

```bash
$ npm install
```

### Running The App
**Dev** on port 3000.

```bash
$ npm run dev
```

**Production** on port 3001.

```bash
$ npm run build
$ node server/server.js
```
