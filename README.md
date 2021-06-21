
# Moving from Callbacks to Promises

Starting with [diagram-js](https://github.com/bpmn-io/diagram-js)@7, [bpmn-js](https://github.com/bpmn-io/bpmn-js)@7, and [dmn-js](https://github.com/bpmn-io/dmn-js)@11, using [promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) is the preferred way of using these libraries. Callbacks are deprecated and will likely be removed in future releases.

Switching from callbacks to promises is easy, as you'll see in this example. Even if your browser doesn't support promises, you can still [polyfill](https://developer.mozilla.org/en-US/docs/Glossary/Polyfill) them.

Following APIs return a Promise:

- [bpmn-js](#bpmn-js)
  - [importXML](#importXML-bpmn-js)
  - [importDefinitions](#importDefinitions-bpmn-js)
  - [open](#open-bpmn-js)
  - [saveXML](#saveXML-bpmn-js)
  - [saveSVG](#saveSVG-bpmn-js)
  - [createDiagram](#createDiagram-bpmn-js)
- [dmn-js](#dmn-js)
  - [importXML](#importXML-dmn-js)
  - [open](#open-dmn-js)
  - [saveXML](#saveXML-dmn-js)
  - [saveSVG](#saveSVG-dmn-js)

## bpmn-js

<a name="importXML-bpmn-js"></a>
### importXML

#### Before

```
const modeler = new BpmnJS();

modeler.importXML(xml, (err, warnings) => {
  // ...
});
```

#### After

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

<a name="importDefinitions-bpmn-js"></a>
### importDefinitions

#### Before

```
const modeler = new BpmnJS();

modeler.importDefinitions(definitions, (err, warnings) => {
  // ...
});
```

#### After

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

<a name="open-bpmn-js"></a>
### open

#### Before

```
const modeler = new BpmnJS();

modeler.open(bpmnDiagram, (err, warnings) => {
  // ...
});
```

#### After

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

<a name="saveXML-bpmn-js"></a>
### saveXML

#### Before

```
const modeler = new BpmnJS();

modeler.saveXML(options, (err, xml) => {
  // ...
});
```

#### After

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

<a name="saveSVG-bpmn-js"></a>
### saveSVG

#### Before

```
const modeler = new BpmnJS();

modeler.saveSVG(options, (err, svgString) => {
  // ...
});
```

#### After

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

<a name="createDiagram-bpmn-js"></a>
### createDiagram

#### Before

```
const modeler = new BpmnJS();

modeler.createDiagram((err, warnings) => {
  // ...
});
```

#### After

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

## dmn-js

<a name="importXML-dmn-js"></a>
### importXML

#### Before

```
const modeler = new DmnJS();

modeler.importXML(xml, (err, warnings) => {
  // ...
});
```

#### After

```javascript
const modeler = new DmnJS();

try {
  { warnings } = await modeler.importXML(xml);
  console.log(warnings);
} catch (err) {
  console.log(err.message, err.warnings);
}
```

<a name="open-dmn-js"></a>
### open

#### Before

```
const modeler = new DmnJS();

modeler.importXML(xml, (importErr, importWarnings) => {

  modeler.open(modeler.getViews()[0], (err, warnings) => {
    // ...
  });

});
```

#### After

```javascript
const modeler = new DmnJS();

try {
  await modeler.importXML(xml);
  const { warnings } = await modeler.open(modeler.getViews()[0]);
  console.log(warnings);
} catch (err) {
  console.log(err);
}
```

<a name="saveXML-dmn-js"></a>
### saveXML

#### Before

```
const modeler = new DmnJS();

modeler.importXML(dmnXml, (importErr, importWarnings) => {

  modeler.saveXML(options, (err, xml) => {
    // ...
  });

}
```

#### After

```javascript
const modeler = new DmnJS();

try {
  await modeler.importXML(dmnXml);
  const { xml } = await modeler.saveXML(options);
  console.log(xml);
} catch (err) {
  console.log(err);
}
```

<a name="saveSVG-dmn-js"></a>
### saveSVG

#### Before

```
const modeler = new DmnJS();

modeler.importXML(xml, (importErr, importWarnings) => {

  modeler.saveSVG(options, (err, svgString) => {
    // ...
  });

}
```

#### After

```javascript
const modeler = new BpmnJS();

try {
  await modeler.importXML(xml);
  const { svg } = await modeler.saveSVG(options);
  console.log(svg);
} catch (err) {
  console.log(err);
}
```

# License

MIT
