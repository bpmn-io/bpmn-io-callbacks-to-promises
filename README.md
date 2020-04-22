# Moving from Callbacks to Promises

Starting with diagram-js@7 and bpmn-js@7, using [promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) is the preferred way of using these libraries. Callbacks are deprecated and will likely be removed in future releases.

Switching from callbacks to promises is easy, as you'll see in this example. Even if your browser doesn't support promises, you can still [polyfill](https://developer.mozilla.org/en-US/docs/Glossary/Polyfill) them.

## Before

```
const modeler = new BpmnJS();

modeler.importXML(xml, (err, definitions) => {
  // ...
});
```

## After

```
const modeler = new BpmnJS();

modeler.importXML(xml).then((err, definitions) => {
  // ...
});
```

# License

MIT