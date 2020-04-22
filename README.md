
# Moving from Callbacks to Promises

Starting with diagram-js@7 and bpmn-js@7, using [promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) is the preferred way of using these libraries. Callbacks are deprecated and will likely be removed in future releases.

Switching from callbacks to promises is easy, as you'll see in this example. Even if your browser doesn't support promises, you can still [polyfill](https://developer.mozilla.org/en-US/docs/Glossary/Polyfill) them.

Following APIs return a Promise:

 - [importXML](#importXML)
 - [importDefinitions](#importDefinitions)
 - [open](#open)
 - [saveXML](#saveXML)
 - [saveSVG](#saveSVG)
 - [createDiagram](#createDiagram)

## importXML

### Before

```
const modeler = new BpmnJS();

modeler.importXML(xml, (err, warnings) => {
  // ...
});
```

### After

```javascript
const modeler = new BpmnJS();

try {
	const result = await modeler.importXML(xml);
	const { warnings } = result;
	console.log(warnings);
} catch (err) {
	console.log(err.message, err.warnings);
}
```

## importDefinitions

### Before

```
const modeler = new BpmnJS();

modeler.importDefinitions(definitions, (err, warnings) => {
  // ...
});
```

### After

```javascript
const modeler = new BpmnJS();

try {
	const result = await modeler.importDefinitions(definitions);
	const { warnings } = result;
	console.log(warnings);
} catch (err) {
	console.log(err.message, err.warnings);
}
```

## open

### Before

```
const modeler = new BpmnJS();

modeler.open(bpmnDiagram, (err, warnings) => {
  // ...
});
```

### After

```javascript
const modeler = new BpmnJS();

try {
	const result = await modeler.open(bpmnDiagram);
	const { warnings } = result;
	console.log(warnings);
} catch (err) {
	console.log(err.message, err.warnings);
}
```

## saveXML

### Before

```
const modeler = new BpmnJS();

modeler.saveXML(options, (err, xml) => {
  // ...
});
```

### After

```javascript
const modeler = new BpmnJS();

try {
	const result = await modeler.saveXML(options);
	const { xml } = result;
	console.log(xml);
} catch (err) {
	console.log(err);
}
```

## saveSVG

### Before

```
const modeler = new BpmnJS();

modeler.saveSVG(options, (err, svgString) => {
  // ...
});
```

### After

```javascript
const modeler = new BpmnJS();

try {
	const result = await modeler.saveSVG(options);
	const { svg } = result;
	console.log(svg);
} catch (err) {
	console.log(err);
}
```

## createDiagram

### Before

```
const modeler = new BpmnJS();

modeler.createDiagram((err, warnings) => {
  // ...
});
```

### After

```javascript
const modeler = new BpmnJS();

try {
	const result = await modeler.createDiagram();
	const { warnings } = result;
	console.log(warnings);
} catch (err) {
	console.log(err.message, err.warnings);
}
```

# License

MIT
