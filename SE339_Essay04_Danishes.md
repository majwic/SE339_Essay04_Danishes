# ReactiveUI and ReactiveX
##### _Mason, Caelan, Frank, Isaiah, Vibhu_

---

## Introduction
ReactiveX is a library for creating asynchronous and event-based programs using observable sequences. This approach is similar to how ReactiveUI handles updating the view as the user triggers events. ReactiveUI provides additional features tailored specifically for creating an application with a Model-View-ViewModel (MVVM) pattern. Nevertheless, ReactiveX and ReactiveUI share many similarities and differences between their observables and schedulers. These modules are the driving force behind reactive programming, and ReactiveX and ReactiveUI would not function without them.

## Reactive Programming Patterns
Both ReactiveUI and ReactiveX make use of the Observer pattern to handle asynchronous events. Both applications utilize similar functions to manipulate streams of ongoing events (((give examples of functions and events here))). One key difference is ReactiveUI's inclusion of Model-View-ViewModel elements which increases the portability and maintainability of potential applications. The MVVM pattern works by having observable properties and commands passed between the View and ViewModel while (((talk about ViewModel to Model))). One key part of a MVVM framework is the `ICommand` interface which allows the View to trigger logic defined in the ViewModel. ReactiveUI has `ReactiveCommand` which is an implementation of `ICommand`. ReactiveX has no implementation making it ineffective for developing a MVVM pattern.


https://reactivex.io/intro.html
https://www.reactiveui.net/docs/reactive-programming/
https://www.reactiveui.net/docs/getting-started/


## Observables

### _ReactiveUI's Observables_
ReaciveUI contains the basic `Observable` but also contains objects and methods to allow for the parts of MVVM architecture to interact with observables. One form of observable in ReactiveUI is the `ReactiveCommand<TInput, TOutput>`. It is created with methods taking parameters of input and output allowing for the definition of commands that may be executed synchronously or asynchronously. It can also be read as an `IObservable<TOutput>` of the ouput. It further has commmands that provide observers for data streams, such as `IsActive()`, which can be used to execute asynchronous commands. `ObservableAsPropertyHelper` is a class that creates a ViewModel property from an `IObservable` object and is useful if you do not plan to muatate the value. The class monitors the data stream for changes and the notifies the scheduler to update the property. It is also useful for exposing the latest value from observables that are derived from other properties. `WhenAny` and `WhenActive` are also obersvers that monitor observables and notify when a change occurs in the datat stream.

### _ReactiveX's Observables_
ReactiveX does not supply many implimentations of `IObservable`, instead providing a variety of methods to work with `IObserver`. ReactiveX still has 3 major observable implementations besides the basic `IObservable`. `IGroupedObservable` represents an observable sequence of elements that have a common key. `IQbservable` evaluates queries against a data stream and can also be subscribed too as an observable. There is also `Subject` which stores charecteristics like and Observable and can also publish to subscribers like an Observer. There are also three sub implementations of `Subject`. `ReplaySubject` caches all values and can replay them for late subscriptions, `BehaviorSubject` only stores the last value published, and `AsyncSubject` only stores the last value and only publishes when the sequence completes making it similar to `Task`. ReactiveX provides very basic Observables leaving it to the user to implement the chosen functionality.

### _Observables Comparision_
ReactiveUI's `ReactiveCommand`  is an implementation of `ICommand`, an essential part of the MVVM pattern. ReactiveX has no such implementation making it ineffective for developing a MVVM pattern on it's own. This is an example of how ReativeUI takes the base funtionality provided by Reactive Extensions and expands upon it to work with MVVM architecture. The `ReactiveCommand` object can take an `IObservable` as input with the `CreateFromObservable()` method, allowing it to accept manipulated data streams from Reactive Extensions commands. By subscribing to `ReactiveComand<TInput, TOutput>` you can use Reactive Extensions to manipulate a data stream and pass it back to the view. ReactiveUI and Reactive Extensions have similar observables but Reactive Extensions provides functionality to combine and manipulate data streams in a way that ReactiveUI does not. ReactiveUI takes the base function of Reactive Extensions and relates them to the MVVM architecture. ReactiveUI benifits heavily from the live data stream manipulation provided by using the  `WhenAny` and `WhenActive` family of functions with Reactive Etensions. 

## Schedulers

### _ReactiveUI's Schedulers_

### _ReactiveX's Schedulers_

### _Schedulers Comparision_

