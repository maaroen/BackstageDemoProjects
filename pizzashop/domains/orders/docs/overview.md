# Order Domain

The order domain is focussed on order handling. From receiving orders, validating orders. It will not be handling payments, nor deliveries.

The process will look a bit like this, we are still discussing about the details of the domain:

```plantuml
@startuml
Customer -> Website: new order
Website -> OrderApi: new order
OrderApi -> PaymentApi: new order received, handle payment
PaymentApi -> Website: payment request
Website -> Customer: Please pay order
Customer -> Website: Order Paid
Website -> PaymentApi: Order Paid
PaymentApi -> OrderApi: Order Paid
OrderApi -> DeliveryApi: New order
@enduml
```