# Conceptual Architecture of a Modern Web Application

Over the past years, we have seen the rise of several new web frameworks.

In this section we propose a tentative conceptual model that characterizes
the functions of modern web applications without regard to their underlying internal structure and technology.

We follow the idea of the [OSI model](https://en.wikipedia.org/wiki/OSI_model) for networking.
A web application is dissected into functional abstraction layers.

### Physical layer

The physical layer is the Web as a development platform. That is: DOM, web components, html/css, http2, service workers and so forth.

### Rendering layer

The rendering layer has the function to synchronize the internal state of a webapp with DOM.
There are several techniques to implement this functionality. E.g., following [1], we could have:

* Server side rendering
* Manual rendering
* Data binding
* [Blaze transparent reactivity](blaze.md)
* [Virtual DOM](vitual-dom.md)
* Dirty checking

### Component layer

A [component](component.md) is an abstraction over the rendering layer. Today developers do not see the rendering layer because it is encapsulated inside the notion of component. This is not always true, sometimes there are good reason to adopt a lower level approach (e.g. [virtual-dom](https://github.com/Matt-Esch/virtual-dom)).

There is a huge debate about what a component is. I write about it [here](./component,md), but I believe that a component can be succinctly defined as a declarative description of a piece of user interface.

Moreover components have:
* lifecycle hooks,
* event binding,
* and (not always) an internal state.

Finally, components are usually composable. Component composability is mainly static or geometric, that is, it describes how components are juxtaposed and how parents pass data to their children.

### Network layer

The network layer is not built on the top of the component layer. The two layers are in some sense orthogonal. While the component layer describes how components are nested, the network layer says how they are wired together in terms of action or event flows [2].

The classical architecture is represented by [MVC](./mvc.md).

[Flux](flux.md) is an architectural style proposed by Facebook. Facebook engineers claim that MVC does not scale well and proposed Flux to structure the code in such a way to make it more predictable. The basic idea is to enforce a unidirectional data flow.

[Redux](redux.md)

[Relay](relay.md)

[Apollo](apollo.md) consists of a global store or cache (i.e. Redux by default) and a domain specific query language (i.e. GraphQL). On the contrary of previous approaches, the flow is transparent to developers. Components declare in GraphQL which data they are interested in. Essentially, each component has a view on the global store.

### Global store layers

Global stores are various source of data which are "global" to the whole application. E.g. router, account information and so on.


## Major technologies vs conceptual architecture

|           | React  | Angular  | Ember    |   |
|-----------|--------|----------|----------|---|
| Physical  |        | wc       |          |   |
| Rendering |  vdom  | dirty    | binding  |   |
| Component |  jsx   |          | templ    |   |
| Network   |  flux, redux      |          |          |   |
| Global    |  react-router     |          |          |   |
------------------------------------------------

React is less opinionated than Angular. Essentially, it can be reduced to vdom+jsx, but there are common libraries which are natural choices for react.


## References

[1] [Change and its detection in javascript frameworks](http://teropa.info/blog/2015/03/02/change-and-its-detection-in-javascript-frameworks.html)

[2] I feel a strong analogy with [bigraphs](https://en.wikipedia.org/wiki/Bigraph), a theoretical model of computation developed my Robin Milner.
