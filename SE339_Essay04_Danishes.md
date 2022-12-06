# ReactiveUI and ReactiveX
##### _Mason, Caelan, Frank, Isaiah, Vibhu_

---

## Introduction
ReactiveX is a library for creating asynchronous and event-based programs using observable sequences. This approach is similar to how ReactiveUI handles updating the view as the user triggers events. ReactiveUI provides additional features tailored specifically for creating an application with a Model-View-ViewModel (MVVM) pattern. Nevertheless, ReactiveX and ReactiveUI share many similarities and differences between their observables and schedulers. These modules are the driving force behind reactive programming, and ReactiveX and ReactiveUI would not function without them.

## Reactive Programming Patterns
Both ReactiveUI and ReactiveX make use of the Observer pattern to handle asynchronous events. Both applications utilize similar functions to manipulate streams of ongoing events (((give examples of functions and events here))). One key difference is ReactiveUI's inclusion of Model-View-ViewModel elements which increases the portability and maintainability of potential applications. The MVVM pattern works by having observable properties and commands passed between the View and ViewModel while (((talk about ViewModel to Model))). One key part of a MVVM framework is the `ICommand` interface which allows the View to trigger logic defined in the ViewModel. ReactiveUI has `ReactiveCommand` which is an implementation of `ICommand`. `ReactiveCommand` is compatible with ReactiveX to help create MVVM applications but ReactiveX doesn’t have that functionality on its own.


https://reactivex.io/intro.html
https://www.reactiveui.net/docs/reactive-programming/
https://www.reactiveui.net/docs/getting-started/


## Observables

### _ReactiveUI's Observables_

### _ReactiveX's Observables_

### _Observables Comparision_

https://reactivex.io/documentation/observable.html

https://www.reactiveui.net/docs/handbook/when-any/

## Schedulers

### _ReactiveUI's Schedulers_

### _ReactiveX's Schedulers_

### _Schedulers Comparision_

