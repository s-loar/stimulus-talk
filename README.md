# Stimulus Talk Outline

Want to cover the basics with some examples

## What Stimulus is
* Parts
  * Controllers
  * Targets
  * Actions
  * Lifecycle Events
  * Values

## What is Stimulus
* The handbook describes Stimulus as ‘... a JavaScript framework with modest ambitions.’ 
  * It is not a full blown framework like React, Angular or Vue
  * HTML centric
  * Connects HTML elements to JavaScript objects (controllers)
    * Controllers
    * Actions
    * Values
    * Targets

## In General
* Controllers need to be attached to something to get instantiated. They have access to elements within their scope.
* Actions are listeners which run actions in the controller they specify
* The event is passed to the action and we have access to that and to things within the controller’s scope, like targets and values.
* Targets are things that the controller can interact with, usually to change. Targets are controller specific. So if an element needs to be updated from more than one controller, just add more target attributes for each controller. And they need to reside within the scope of the controller’s element.
* Values are for storing state as element attributes. They are similar to Targets.

## Controllers
* Are the main objects for HTML interation.
  * Have scope to the element they are an attribute, and it’s children.
  * Controllers ignore the scope of controllers nested within their scope.
  * More than one controller can be associated with the same element.

## Targets
* Are primarily elements in the DOM to be interacted with by the controller.
  * Have to declare them in the controller, and have to be in scope in the HTML
  * Can be shared by multiple controllers
  * Have a plural form (s on the end) that returns an array of objects that have the target designation. Example: phraseTargets
  * Their presence can be checked with the prefix ‘has’ as in hasPhraseTarget.
  * Have special callbacks that fire when a target is connected, or disconnected from the controller’s scope. For example phaseTargetConnected() and phaseTargetDisconneted()

## Actions
* Are listeners that connects a controller’s action to an HTML element
  * Do not need to specify the trigger event for default actions, like ‘click’ for buttons. This gives data-action="speak#sayHello"
  * Actions can be on global events of the window and document.
  * Can end event handling 
    * event.preventDefault() - stops the event’s default behavior, like submitting a form.
    * event.stopPropagation() - stops the bubbling up of the event <- Use this one.
    * event.stopImmediatePropagation() - stops other actions, to the right, from executing on the same action.

## Lifecycle Events
* Events that you can utilize as things get connected or disconnected.
  * initialize() - the controller is loaded.
  * connect() - the controller is connected to something in the DOM
  * disconnect() - the controller is disconnected from something in the DOM
  * [targetName]TargetConnected() - The controller is connected to a target
  * [targetName]TargetDisconnected() - The controller is disconnected to a target

## Values
* Are a way to maintain state
  * Need an attribute in the element where the controller is set on an element
  * Need a definition in the controller similar to targets
  * Can set and get their value similar to targets
  * Can set defaults
  * Have a special callback to handle any state changes
  * [name]ValueChanged() which can receive 2 values.
  * Current value
  * Previous value

## CSS Classes
* Similar to the pattern above in setup and naming
  * Set them on an element in the controller’s scope as an attribute.
  * Declare them in the controller
  * You can add and remove classes to that element with
    * this.element.classList.add([the CSS class name])
    * this.element.classList.remove([the CSS class name])
