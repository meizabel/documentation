# Process Manager

Process Manager coordinates and routes messages between aggregates within a given Bounded Context (BC). It is A central processing unit which maintains the state of the business process and determines the next processing step based on intermediate results.

Event and Command Handlers are invoked by the ProcessManagerRepository which manages the instances of a Process Manager class.

“Process Manager” pattern was first defined and brought to the common vocabulary by Kyle Brown and Bobby Woolf under the guidance of Martin Fowler in the book [“Enterprise Integration Patterns”](http://www.enterpriseintegrationpatterns.com/patterns/messaging/ProcessManager.html).

Please see [more information](http://kellabyte.com/2012/05/30/clarifying-the-saga-pattern/) on Process Managers (and the important difference between Process Manager and Saga).
