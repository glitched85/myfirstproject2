<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## DataSources

This module manages data sources within the editor.
Once the editor is instantiated, you can use the following API to manage data sources:

```js
const editor = grapesjs.init({ ... });
const dsm = editor.DataSources;
```

## Available Events
* `data:add` Added new data source.

```javascript
editor.on('data:add', (dataSource) => { ... });
```

* `data:remove` Data source removed.

```javascript
editor.on('data:remove', (dataSource) => { ... });
```

* `data:update` Data source updated.

```javascript
editor.on('data:update', (dataSource, changes) => { ... });
```

* `data:path` Data record path update.

```javascript
editor.on('data:path:SOURCE_ID.RECORD_ID.PROP_NAME', ({ dataSource, dataRecord, path }) => { ... });
editor.on('data:path', ({ dataSource, dataRecord, path }) => {
 console.log('Path update in any data source')
});
```

* `data:pathSource` Data record path update per source.

```javascript
editor.on('data:pathSource:SOURCE_ID', ({ dataSource, dataRecord, path }) => { ... });
```

* `data` Catch-all event for all the events mentioned above.

```javascript
editor.on('data', ({ event, model, ... }) => { ... });
```

## Methods

*   [add][1] - Add a new data source.
*   [get][2] - Retrieve a data source by its ID.
*   [getAll][3] - Retrieve all data sources.
*   [remove][4] - Remove a data source by its ID.
*   [clear][5] - Remove all data sources.

[DataSource]: datasource.html

## add

Add new data source.

### Parameters

*   `props` **[Object][6]** Data source properties.
*   `opts` **AddOptions**  (optional, default `{}`)

### Examples

```javascript
const ds = dsm.add({
 id: 'my_data_source_id',
 records: [
   { id: 'id1', name: 'value1' },
   { id: 'id2', name: 'value2' }
 ]
});
```

Returns **[DataSource]** Added data source.

## get

Get data source.

### Parameters

*   `id` **[String][7]** Data source id.

### Examples

```javascript
const ds = dsm.get('my_data_source_id');
```

Returns **[DataSource]** Data source.

## getValue

Get value from data sources by key

### Parameters

*   `key` **[String][7]** Path to value.
*   `defValue` **any**&#x20;

Returns **any** const value = dsm.getValue('ds\_id.record\_id.propName', 'defaultValue');

## remove

Remove data source.

### Parameters

*   `id` **([String][7] | [DataSource])** Id of the data source.
*   `opts` **RemoveOptions?**&#x20;

### Examples

```javascript
const removed = dsm.remove('DS_ID');
```

Returns **[DataSource]** Removed data source.

## fromPath

Retrieve a data source, data record, and optional property path based on a string path.
This method parses a string path to identify and retrieve the corresponding data source
and data record. If a property path is included in the input, it will also be returned.
The method is useful for accessing nested data within data sources.

### Parameters

*   `path` **[String][7]** The string path in the format 'dataSourceId.recordId.property'.

### Examples

```javascript
const [dataSource, dataRecord, propPath] = dsm.fromPath('my_data_source_id.record_id.myProp');
// e.g., [DataSource, DataRecord, 'myProp']
```

Returns **[DataSource?, DataRecord?, [String][7]?]** An array containing the data source,
data record, and optional property path.

## store

Store data sources to a JSON object.

Returns **[Array][8]** Stored data sources.

## load

Load data sources from a JSON object.

### Parameters

*   `data` **[Object][6]** The data object containing data sources.

Returns **[Object][6]** Loaded data sources.

[1]: #add

[2]: #get

[3]: #getall

[4]: #remove

[5]: #clear

[6]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object

[7]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String

[8]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array
