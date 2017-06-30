# Event Handlers

Event handlers in Komada are not special or different. However, they are handled through separate files, rather than being added to the main file.

See [creating event handlers](creating-event-handlers.md) for more details on adding your own.

> **WARNING**: Only one event handler is accepted for each event name. You *do not need* to create your own message handler - just use [inhibitors](./inhibitors.md) and [monitors](monitors.md) to handle messages.