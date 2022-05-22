# Pointer Lock API Demo

This demo is for the [Pointer Lock API](https://w3c.github.io/pointerlock/
"W3C Pointer Lock specification") ([Pointer Lock API documentation on MDN](
https://developer.mozilla.org/en-US/docs/Web/API/Pointer_Lock_API)). It
demonstrates:

- Requesting pointer lock with `Element.requestPointerLock` in response to user
  action (in this case, a `click` event)
- Releasing pointer lock, both with `document.exitPointerLock` and with the
  ["default unlock gesture"](
  https://w3c.github.io/pointerlock/#dfn-default-unlock-gesture
  "Definition of &quot;default unlock gesture&quot; in the Pointer Lock specification")
- Responding to `pointerlockchange` and `pointerlockerror` events
- Using `document.pointerLockElement` to identify the element that has pointer
  lock
- Reading `movementX` and `movementY` properties from a `pointermove` event
  while pointer lock is active

Future enhancement of the demo might include:

- Interaction of pointer lock with fullscreen

## Implementation notes

Firefox 100:

- Attempting to obtain pointer lock without user action (immediately on DOM
  load) gives this error:
  > Request for pointer lock was denied because Element.requestPointerLock()
  > was not called from inside a short running user-generated event handler,
  > and the document is not in full screen.

Chrome 101:

- Attempting to obtain pointer lock without user action (immediately on DOM
  load) gives this error:
  > Uncaught (in promise) DOMException: A user gesture is required to request
  > Pointer Lock.
