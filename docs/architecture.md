## Product Choice

Chosen product: Yandex Go

Link: https://taxi.yandex.ru/ru_ru/

Yandex GO app\website is useed for calling taxi, rent carsharing/scooters, etc.

## Main compoents

![Yandex GO architecture component diagram](<diagrams/out/yandex-go/architecture-component/Component Diagram.svg>)
[Architecture component code](diagrams/src/yandex-go/architecture-component.puml)

### Components:
1. Mobile app and Web app are used for interaction between user and the service.
2. API gateway is a "hub" which performs requests for different APIs and connects the to web/mobile.
3. Message broker makes delivery of messages between databases and APIs safe.
4. External services - other products of yandex, which are being connected to our project via APIs. These services reduces amount of tasks which should be done before deployment.
5. Core Services - microservices used in app.

## Data flow:
![d](<diagrams/out/yandex-go/architecture-sequence/Sequence Diagram.svg>)
[Data flow code](diagrams/src/yandex-go/architecture-sequence.puml)

### App initialization & authentification description:

User opens an app and the session validation occurs. Nextly, through the API gateway, authentification toke is being sent to the User Service API. User service performs request to the state cache which approves the session and sends an approvement back to the User Service API. Then, the API sends user data into API gateway and the authentification succeeds.

## Deployment
![alt text](<diagrams/out/yandex-go/architecture-deployment/Deployment Diagram.svg>)
[Deployment code](diagrams/src/yandex-go/architecture-deployment.puml)

### Description:

All APIs and services are being deployed in clusters, the API gateway deployed in Load Balancer and the apps deployed on smartphone or computer respectively.

## Assumpions:
I assume that it is definitely not a full descriptionns of the Yandex GO service.

## Open questions:
1. I don't fully understand, what happens on the payment and pre-ride steps of the Data flow(what do external APIs actually do).
2. There is no diagram for Web app data flow.