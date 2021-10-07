# Stimulus Talk Outline

Stimulus... a JavaScript framework with modest ambitions.

## Current version: v3.0.1 - released 10/7/2021
## What is Stimulus
* The handbook describes Stimulus as ‘... a JavaScript framework with modest ambitions.’ 
  * It is not a full blown framework like React, Angular or Vue
  * HTML centric
  * Connects DOM elements to JavaScript objects
    * Controllers
    * Actions
    * Targets
    * Values

## In General
* Controllers are attached to something in the DOM. They are limited by their scope.
* Actions are methods in the controller. They are often event listeners.
* Targets are "significant" things in the DOM that the controller can interact with.  
* Values are for storing state.

## Controllers
* Are the main objects for DOM interaction. Work kinda like controllers of other frameworks. 
  * Its behavior is encapsulated.
  * Have scope to the element on which they are an attribute, and it’s children.
  * Controllers ignore the scope of any controllers nested within their scope.
  * More than one controller can be associated with the same element.

## Targets
* Are elements in the DOM to be interacted with by the controller.
  * Have to declare them in the controller, and have to be in scope in the HTML
  * Can be shared by multiple controllers
  * Have a plural form (s on the end) that returns an array of objects that have the target designation. Example: phraseTargets
  * Their presence can be checked with the prefix ‘has’ as in hasPhraseTarget.
  * Have special callbacks that fire when a target is connected, or disconnected from the controller’s scope. For example phraseTargetConnected() and phraseTargetDisconneted()

## Actions
* Are listeners that connects a controller’s action to a DOM element
  * Do not need to specify the trigger event for default actions, like ‘click’ for buttons. This gives data-action="speak#sayHello"
  * Actions can be on global events of the window and document.
  * Can stop further event handling 
    * event.preventDefault() - stops the event’s default behavior, like submitting a form.
    * event.stopPropagation() - stops the bubbling up of the event <- Use this one.
    * event.stopImmediatePropagation() - stops other actions, to the right, from executing on the same action.

## Lifecycle Events
* Events that you can utilize as things get connected or disconnected.
  * initialize() - the controller is loaded.
  * connect() - the controller is connected to something in the DOM
  * disconnect() - the controller is disconnected from something in the DOM
  * \[targetName\]TargetConnected() - The controller is connected to a target
  * \[targetName\]TargetDisconnected() - The controller is disconnected to a target

## Values
* Are a way to maintain state
  * Need an attribute in the element where the controller is set on an element
  * Need a definition in the controller similar to targets
  * Can set and get their value similar to targets
  * Can set defaults
  * Have a special callback to handle any state changes
    * \[name\]ValueChanged() which can receive 2 values.
      * Current value
      * Previous value
