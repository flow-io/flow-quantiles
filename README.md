flow-quantiles
==============

Reduce transform stream which computes the quantiles over a stream of numeric data.

Note: in order to calculate the quantiles exactly, all data must be buffered into memory. As a result, this stream acts as a sink. Use caution when applying the transform to large datasets.


## Installation

``` bash
$ npm install flow-quantiles
```


## Examples

``` javascript
var eventStream = require( 'event-stream' ),
	qStream = require( 'flow-quantiles' );

// Create some data...
var data = new Array( 1000 );
for ( var i = 0; i < data.length; i++ ) {
	data[ i ] = Math.round( Math.random() * 100 );
}

// Create a readable stream:
var readStream = eventStream.readArray( data );

// Create a new stream:
var stream = qStream()
	.quantiles( 10 )
	.stream();

// Pipe the data:
readStream.pipe( stream )
	.pipe( process.stdout );
```

## Tests

Unit tests use the [Mocha](http://visionmedia.github.io/mocha) test framework with [Chai](http://chaijs.com) assertions.

Assuming you have installed Mocha, execute the following command in the top-level application directory to run the tests:

``` bash
$ mocha
```

All new feature development should have corresponding unit tests to validate correct functionality.


## License

[MIT license](http://opensource.org/licenses/MIT). 


---
## Copyright

Copyright &copy; 2014. Athan Reines.

