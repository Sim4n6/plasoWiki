This page contains some scribbles about events. It contains information about:

* What is an event?
* How can an event be defined?
* How are events defined in plaso?

## What is an event?
From [Wikipedia - Event (computing)](http://en.wikipedia.org/wiki/Event_%28computing%29)

> In computing, an event is an action or occurrence detected by the program that may be handled by the program. Typically events are handled synchronously with the program flow, that is, the program has one or more dedicated places where events are handled, frequently an event loop. Typical sources of events include the user (who presses a key on the keyboard, in other words, through a keystroke). Another source is a hardware device such as a timer. Any program can trigger its own custom set of events as well, e.g. to communicate the completion of a task. A computer program that changes its behavior in response to events is said to be event-driven, often with the goal of being interactive.

## How can an event be defined?
An event consists of the following types of information:

* date and time or duration of the event (event time);
* an indication of what the event time represents e.g. Creation Time, Program Execution Duration, etc.
* the source of the event e.g. the Windows Application Event Log C:\Windows\System32\config\AppEvent.evt or specific lines in the /var/log/messages
* data specific to the event e.g. in case of process execution this could be the path of the executable file and arguments
* contextual information about the event e.g. user comments or automatic generated tags (event source)

A more analysts view on how an event can be defined is:

* When or for how long this event happened (event time)
* Who/what did an action for the event to happen (actor or subject)
* What was the action that happened (action or predicate)
* Who/what affected the action (object)
* Where did we learn from that the event happened (event source)

### Different levels of events
**TODO: add description**

* source-level event
* system-level event
* user-level event

## How are events defined in plaso?
**TODO: add description**