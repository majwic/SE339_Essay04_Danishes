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
ReaciveUI contains the basic `Observable` but also contains objects and methods to allow for MVVM implementation. One form of observable in ReactiveUI is the `ReactiveCommand`. It is created with methods taking parameters of input and output allowing for the definition of commands that may be executed synchronously or asynchronously. It is also representitive of an IObservable of the ouput. It further has commmands that provide observable data streams, such as `IsActive()`, which can be used to execute asynchronous commands with ReactiveX. `ObservableAsPropertyHelper` is a class that connects a property on the view and a data stream. The class reflects the latest value in the `Observable` and schedules changes to the property with the scheduler. 

### _ReactiveX's Observables_
ReactiveX does not supply many implimentations of `IObserver`, instead providing a variety of methods to work with `IObserver`. ReactiveX still has 3 major observable implementations besides the basic `IObserver`. `IGroupedObservable` represents an observable sequence of elements that have a common key. `IQbservable` evaluates queries against a data stream and can also be subscribed too as an observable. There is also `Subject` which stores charecteristics like and Observable and can also publish to subscribers like an Observer. There are also three sub implementations of `Subject`. `ReplaySubject` caches all values and can replay them for late subscriptions, `BehaviorSubject` only stores the last value published, and `AsyncSubject` only stores the last value and only publishes when the sequence completes making it similar to `Task`. ReactiveX provides very basic Observables leaving it to the user to implement the chosen functionality.

### _Observables Comparision_
ReactiveUI has `ReactiveCommand` which is an implementation of `ICommand`. ReactiveX has no implementation making it ineffective for developing a MVVM pattern on it's own. The `ReactiveCommand` object can take an `IObservable` as input with the `CreateFromObservable()` method allowing it to accept data streams from ReactiveX.`ReactiveComand<TInput, TOutput>`  is the same as `Iobservable<TOutput>` therfore by subscribing to the ReactiveCommand you can use Reactive Extensions on a data stream from the view. They have similar observables but Rx provides functionality to combine and manipulate data streams in a way that ReactiveUI does not.((Relate to iterator aspect of Rx)) ReactiveUI has many ways to connect observables to properties and relate them to the MVVM architecture. ReactiveUI benifits heavily from the data stream manipulation provided by Rx ((WhenAny and WhenActive))

https://reactivex.io/documentation/observable.html

https://www.reactiveui.net/docs/handbook/when-any/

## Schedulers

### _ReactiveUI's Schedulers_
ReactiveUI provides two app wide schedulers, `RxApp.MainThreadScheduler` and `RxApp.TaskpoolScheduler`, which specify where and/or when to execute tasks related to a corresponding `Observable`. The `RxApp.MainThreadScheduler` scheduler specifically executes tasks on the UI thread mainly for updating the layout of elements of an application. Next, the `RxApp.TaskpoolScheduler` scheduler executes code using the Task Parallel Libray (TPL) taskpool. The TPL is part of the .NET framework, and simplifies the process of adding parallelism and concurrency to applications. The TPL accomplishes this by dynamically scaling the degree of concurrency to use all available processors as efficiently as possible. Users of ReactiveUI can use these schedulers along with tasks relating to `Observables` and `ReactiveCommands` to increase their applications performance. 

### _ReactiveX's Schedulers_
ReactiveX has a main app wide scheduler named `AsyncScheduler` that performs the basic scheduler behaviors in which the scheduler queues up `Actions` when recieved and then asynchronously completes them. `Actions` are similar to tasks in that they are the product of `Observable` except for the fact they can be sent to a scheduler with instruction for executing the task more than once. In that way, if an action needs to be called often at specific time intervals, there is no need to send the same request multiple times thanks to the implementations of `Actions`. Various additional schedulers are derived from the `AsyncScheduler` in order to accomodate different needs during run time. The `AsapScheduler` prioritizes `Actions` marked as `AsapActions` and completes them as fast as possible in comparison to other schedulers. The `AnimationFrameScheduler` completes queued graphical `Actions` called `AnimationFrameActions` before the screen repaints the graphical interface. Finally, the `QueueScheduler` performs `Actions` called `QueueActions` synchrounously as scheduled during runtime. 
### _Schedulers Comparision_
Comparatively, ReactiveX's schedulers, such as `AnimationFrameActions` or `AsapScheduler`, are able to handle multiple different types of tasks in different mannerisms. However, ReactiveUI's usage of the TPL protocol instead of `Actions` allows the tasks generalized faster performance for all types of tasks due to the dynamic scaling of concurrency to use all processors as efficiently as possible. Essentially, the schedulers of ReactiveX can perform different sorts of tasks according to needs at runtime wheras ReactiveUI is able to ensure generalized good performance across the board.
## Conclusion
In essence, ReactiveUI and ReactiveX are fairly similar in that they both use an Observer pattern and that they utilize similar functions to manage streams of events, but they do differ in a few areas. A couple of noteable differences are that ReactiveUI uses MVVM while ReactiveX does not, and that ReactiveUI's schedulars allow for parallelism while ReactiveX focuses on handling different types of tasks in seperate schedulars.
