# Gamepad API demo

This demo is for the [Gamepad API](https://w3c.github.io/gamepad/
"W3C Gamepad specification") ([Gamepad API documentation on MDN](
https://developer.mozilla.org/en-US/docs/Web/API/Gamepad_API)). It
demonstrates:

- Responding to `gamepadconnected` and `gamepaddisconnected` events
- Getting gamepad state information from `navigator.getGamepads()`
- The 16 buttons and two sticks (four axes) defined for the ["Standard Gamepad"
  layout](https://w3c.github.io/gamepad/#dfn-standard-gamepad
  "Definition of &quot;Standard Gamepad&quot; in the Gamepad specification")

Future enhancement of the demo might include:

- Reporting the value of analog buttons
- Checking for input updates using gamepad timestamps, rather than polling the
  gamepad with `requestAnimationFrame`

## Implementation notes

Firefox 98:

- `navigator.getGamepads()` only contains `Gamepad` objects, and only for
  gamepads that are actually connected.
- When handling a `gamepadconnected` event, the event's `gamepad` property is a
  live reference to the gamepad in question. It can be saved and used to check
  for future changes to the gamepad state.
- While handling a `gamepaddisconnected` event, the array obtained from
  `navigator.getGamepads()` will still include the gamepad being disconnected,
  but will report it as having 0 buttons and 0 axes.
- I have only ever seen index 0 be assigned to the first-connected gamepad.

Chrome 100:

- `navigator.getGamepads()` contains four items, which are `null` until a
  gamepad is actually connected. (I expect this is a minimum and the array will
  expand if you connect five or more gamepads, but I haven't tested it.)
- When handling a `gamepadconnected` event, the event's `gamepad` property is a
  snapshot of the gamepad in question *at that moment*. It cannot be used to
  check for future changes to the gamepad state.
- While handling a `gamepaddisconnected` event, the array obtained from
  `navigator.getGamepads()` will have `null` at the disconnected gamepad's
  index.
- I have sometimes seen index 1 be assigned to the first-connected gamepad,
  rather than index 0. I couldn't discern any consistent pattern, though, and
  index 0 seems to be used much more often.
