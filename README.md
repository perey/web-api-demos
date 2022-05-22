# Web API Demos

This is a collection of demonstrations of web APIs. I write these demos to
learn how APIs work, and because it's fun seeing little demos that give
visual feedback.

## Licence

All demos in this collection are free and open-source software, under the
Expat/MIT licence. You may reuse and modify demo code and documentation, as
long as you retain the copyright and permission statement.

See the file `LICENSE`, and the individual demos, for full details.

## Contributing

Contributions of new demos, or of improvements to existing demos, are welcome!
Take a look at existing demos, and these few guidelines, for an idea of what
I'm looking for.

- Contributions must be under the Expat/MIT licence, or a compatible licence.
- Demos should be self-contained in a single HTML file, unless that's
  unreasonable for a particular demo (e.g. it demonstrates an API involving
  multiple files).
- Each demo should be limited in scope, showing off a few related API calls and
  relevant events.
- User interaction should give visual feedback. More detailed information may
  be logged to the console.
- Demos should be tested and working in recent versions of browsers that
  support the relevant standard. Workarounds for cross-browser support or older
  versions (e.g. prefixes like `moz` and `webkit`) should not get in the way of
  a simple demo; if it can be left out, it should be.
  * Demos may require loading the file from a web server, rather than a local
    file. I use a simple Python server (`python -m http.server 8080`) for
    my testing.
- New demos should be accompanied by a README explaining what they show.
