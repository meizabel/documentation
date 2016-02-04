# Process Manager 

Process Manager is an independent component that reacts to domain events in a cross-aggregate, eventually consistent manner.
It maintains the state of the business process and determinethe next processing step based on intermediate results.
You can find more details on why we picked Process Manager vs Saga [here](http://stackoverflow.com/questions/15528015/what-is-the-difference-between-a-saga-a-process-manager-and-a-document-based-ap).