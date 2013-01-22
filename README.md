guichan-hakase
==============

Additional widgets and utilities for [Guichan](http://gitorious.org/guichan). 

## Utilities ##

### FunctorActionListener ###
An adapter that glues together `std::function` and `gcn::ActionListener` which 
allows the client to attach arbitrary functions as callbacks to handle 
`ActionEvent`s without implementing the `gcn::ActionListener` interface in their
 own class. Favors composition over inheritance.