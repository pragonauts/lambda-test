# Lambda test

Simple Serverless tester, which works like this:

```javascript

const lambdaTest = require('lambda-test');
const { getById } = require('../../routes/users.js');

describe('GET /users/{id}', () => {

    it('should get user by id', async () => {
        const response = await lambdaTest(getById)
            .pathParameters({ id: 123 })
            .run();
    })
});

```

or much more sophisticated with Api Blueprint check

```javascript

const assert = require('assert');
const { LambdaTest } = require('lambda-test');
const { updateById } = require('../../routes/users.js');

// in project root
const tester = new LambdaTest('./apiBlueprint.apib');

describe('UPDATE /users/{id}', () => {

    it('should get user by id', async () => {
        const response = await tester.test(updateById, '/users/{id}', 'UPDATE', 200)
            .pathParameters({ id: 123 })
            .queryStringParameters({ fields: 'name' })
            .headers({ Authorization: 'secret' })
            .body({ name: 'John Doe' })
            .verify();

        assert.equal(response.body.name, 'John Doe');
    });

});

```

# API
<a name="HandlerTester"></a>

## HandlerTester
**Kind**: global class

* [HandlerTester](#HandlerTester)
    * [new HandlerTester(handler, [statusCode], [httpMethod], [route], [api])](#new_HandlerTester_new)
    * [.queryStringParameters(query)](#HandlerTester+queryStringParameters) ⇒ <code>this</code>
    * [.body(body)](#HandlerTester+body) ⇒ <code>this</code>
    * [.headers(headers)](#HandlerTester+headers) ⇒ <code>this</code>
    * [.pathParameters(params)](#HandlerTester+pathParameters) ⇒ <code>this</code>
    * [.run()](#HandlerTester+run) ⇒ <code>Promise.&lt;Object&gt;</code>
    * [.verify()](#HandlerTester+verify) ⇒ <code>Promise.&lt;Object&gt;</code>

<a name="new_HandlerTester_new"></a>

### new HandlerTester(handler, [statusCode], [httpMethod], [route], [api])

| Param | Type | Default |
| --- | --- | --- |
| handler | <code>function</code> |  |
| [statusCode] | <code>number</code> \| <code>null</code> | <code></code> |
| [httpMethod] | <code>string</code> \| <code>null</code> | <code>null</code> |
| [route] | <code>string</code> \| <code>null</code> | <code>null</code> |
| [api] | <code>ApiBlueprint</code> \| <code>null</code> | <code></code> |

<a name="HandlerTester+queryStringParameters"></a>

### handlerTester.queryStringParameters(query) ⇒ <code>this</code>
Sets query string

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| query | <code>Object</code> \| <code>null</code> | <code></code> | the query string |

<a name="HandlerTester+body"></a>

### handlerTester.body(body) ⇒ <code>this</code>
Sets request body

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| body | <code>Object</code> \| <code>string</code> | <code></code> | request body |

<a name="HandlerTester+headers"></a>

### handlerTester.headers(headers) ⇒ <code>this</code>
Set request headers

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)

| Param | Type | Default |
| --- | --- | --- |
| headers | <code>Object</code> \| <code>null</code> | <code></code> |

<a name="HandlerTester+pathParameters"></a>

### handlerTester.pathParameters(params) ⇒ <code>this</code>
**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)

| Param | Type | Default |
| --- | --- | --- |
| params | <code>Object</code> \| <code>null</code> | <code></code> |

<a name="HandlerTester+run"></a>

### handlerTester.run() ⇒ <code>Promise.&lt;Object&gt;</code>
Send request

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)
<a name="HandlerTester+verify"></a>

### handlerTester.verify() ⇒ <code>Promise.&lt;Object&gt;</code>
Send request

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)

-----------------

# API
<a name="HandlerTester"></a>

## HandlerTester
**Kind**: global class  

* [HandlerTester](#HandlerTester)
    * [new HandlerTester(handler, [statusCode], [httpMethod], [route], [api])](#new_HandlerTester_new)
    * [.queryStringParameters(query)](#HandlerTester+queryStringParameters) ⇒ <code>this</code>
    * [.body(body)](#HandlerTester+body) ⇒ <code>this</code>
    * [.headers(headers)](#HandlerTester+headers) ⇒ <code>this</code>
    * [.pathParameters(params)](#HandlerTester+pathParameters) ⇒ <code>this</code>
    * [.run()](#HandlerTester+run) ⇒ <code>Promise.&lt;Object&gt;</code>
    * [.verify()](#HandlerTester+verify) ⇒ <code>Promise.&lt;Object&gt;</code>

<a name="new_HandlerTester_new"></a>

### new HandlerTester(handler, [statusCode], [httpMethod], [route], [api])

| Param | Type | Default |
| --- | --- | --- |
| handler | <code>function</code> |  | 
| [statusCode] | <code>number</code> \| <code>null</code> | <code></code> | 
| [httpMethod] | <code>string</code> \| <code>null</code> | <code>null</code> | 
| [route] | <code>string</code> \| <code>null</code> | <code>null</code> | 
| [api] | <code>ApiBlueprint</code> \| <code>null</code> | <code></code> | 

<a name="HandlerTester+queryStringParameters"></a>

### handlerTester.queryStringParameters(query) ⇒ <code>this</code>
Sets query string

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| query | <code>Object</code> \| <code>null</code> | <code></code> | the query string |

<a name="HandlerTester+body"></a>

### handlerTester.body(body) ⇒ <code>this</code>
Sets request body

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| body | <code>Object</code> \| <code>string</code> | <code></code> | request body |

<a name="HandlerTester+headers"></a>

### handlerTester.headers(headers) ⇒ <code>this</code>
Set request headers

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)  

| Param | Type | Default |
| --- | --- | --- |
| headers | <code>Object</code> \| <code>null</code> | <code></code> | 

<a name="HandlerTester+pathParameters"></a>

### handlerTester.pathParameters(params) ⇒ <code>this</code>
**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)  

| Param | Type | Default |
| --- | --- | --- |
| params | <code>Object</code> \| <code>null</code> | <code></code> | 

<a name="HandlerTester+run"></a>

### handlerTester.run() ⇒ <code>Promise.&lt;Object&gt;</code>
Send request

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)  
<a name="HandlerTester+verify"></a>

### handlerTester.verify() ⇒ <code>Promise.&lt;Object&gt;</code>
Send request

**Kind**: instance method of [<code>HandlerTester</code>](#HandlerTester)  
