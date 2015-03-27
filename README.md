# aws-sign

Simple module to calculate `Authorization` header for Amazon AWS REST requests, for Parse.com.


## Usage

1. Put 'aws-sign.js' file into your 'cloud/modules/' folder.
2. Require module in Cloud Code.

# Examples

```js
var AwsSign = require('cloud/modules/aws-sign.js');
var signer = new AwsSign({ 
	accessKeyId: 'AKIAIOSFODNN7EXAMPLE',
	secretAccessKey: 'wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY'
});

var opts = {
	method: 'PUT',
	url: 'http://johnsmith.s3.amazonaws.com/photos/puppy.jpg',
	headers: { ... },
	... // Other request options, ignored by AwsSign.
	body: {}
	success: function() {},
	error: function() {}
};
signer.sign(opts);

Parse.Cloud.httpRequest(opts);
```

The following keys are mandatory: 

* `method`
* `url`

Others are optional. A date header (`headers.date`) will be added for you if it is not already set.