
```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

Enterprise_Boundary(pizzaEnterprise, "PizzaShop") {

  System_Boundary(platform, "Platform") {
    ContainerQueue(serviceBus, "Service bus", "RabbitMq")
  }

  System_Boundary(orderSystem, "Order System") {
    Container(orderApi, "Order Api", ".NET Web Api", "Processing order status")
    ContainerDb(orderDb, "Orders", "PostgreSql")

    BiRel(orderApi, orderDb, "Order details")
  }

  Rel(serviceBus, orderApi, "order details", "messaging")
  Rel(orderApi, serviceBus, "delivery request", "messaging")
}
@enduml
```
