# Pointer Lock API Demo

This demo is for the [Pointer Lock API](https://w3c.github.io/pointerlock/
"W3C Pointer Lock specification") ([Pointer Lock API documentation on MDN](
https://developer.mozilla.org/en-US/docs/Web/API/Pointer_Lock_API)). It
demonstrates:

- Requesting pointer lock with `Element.requestPointerLock` in response to user
  action (in this case, a `click` event)
- Releasing pointer lock, both with `document.exitPointerLock` and with the
  [“default unlock gesture”](
  https://w3c.github.io/pointerlock/#dfn-default-unlock-gesture
  "Definition of “default unlock gesture” in the Pointer Lock specification")
- Responding to `pointerlockchange` and `pointerlockerror` events
- Using `document.pointerLockElement` to identify the element that has pointer
  lock
- Reading `movementX` and `movementY` properties from a `pointermove` event
  while pointer lock is active

Future enhancement of the demo might include:

- Interaction of pointer lock with fullscreen

## Implementation notes

Firefox 100:

- A `pointerlockchange` event listener can be placed on the window or on the
  document.
- Attempting to obtain pointer lock without user action (immediately on DOM
  load) gives this error:
  > Request for pointer lock was denied because Element.requestPointerLock()
  > was not called from inside a short running user-generated event handler,
  > and the document is not in full screen.

  If the browser console has focus, the error is this instead:
  > Request for pointer lock was denied because the document is not focused.
- Pointer lock can be reacquired immediately after being released.
- Right-click is not registered as a `click` event while pointer lock is
  active.

Chrome 102:

- A `pointerlockchange` event listener must be placed on the document, not the
  window.
- Attempting to obtain pointer lock without user action (immediately on DOM
  load) gives this error:
  > A user gesture is required to request Pointer Lock.

  If the browser console has focus, the error is this instead:
  > The root document of this element is not valid for pointer lock.
- There is a delay ([apparently 1.25 seconds](
  https://bugs.chromium.org/p/chromium/issues/detail?id=1127223
  "Chromium issue 1127223: “requestPointerLock immediately after
  exitPointerLock fails”")) after releasing lock before it can be reacquired.
  This appears to only apply when using the unlock gesture, not
  `exitPointerLock`.
- Right-click is registered as a `click` event while pointer lock is active.
