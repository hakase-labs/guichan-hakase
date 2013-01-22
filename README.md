guichan-hakase
==============

Additional widgets and utilities for [Guichan](http://gitorious.org/guichan). 

## Utilities ##

### FunctorActionListener ###
An adapter that glues together `std::function` and `gcn::ActionListener` which 
allows the use of arbitrary functions as callbacks to handle `ActionEvent`s 
without having to implement the `gcn::ActionListener` interface. Favors 
composition over inheritance.

```c++
//
// Create a button first
//
std::unique_ptr<gcn::Button> startButton(new gcn::Button("Start"));

//
// Now you can use lambdas to handle events...
//
gcn::FunctorActionListener lambdaButtonListener([](const gcn::ActionEvent& actionEvent) {
    std::cout << "Button clicked! " << actionEvent.getId() << std::endl;
});

//
// ...or you can use free functions to handle events
//
void handleButtonClick(const gcn::ActionEvent& actionEvent) {
    std::cout << "handleButtonClick [" << actionEvent.getId() << "]" << std::endl;
}

gcn::FunctorActionListener freeFunctionButtonListener();
freeFunctionButtonListener->setCallback(gcn::ActionListenerCallback(handleButtonClick));

startButton->addActionListener(&lambdaButtonListener);
startButton->addActionListener(&freeFunctionButtonListener);
```