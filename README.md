filesource.js
============

Install:
npm install fileosurce

You can e.g. use it, if you want to offer a function, taking all possible types of data sources.

Here are some simple examples how to use it:

```javascript
var filesource = require('filesource');

// Converts web-source to raw data
filesource.getRawData("http://blabla.com/blabla.pdf", function(resp){
	if(!resp.success)
	{
		console.log("Sth. went wrong: " + resp.error);
		return;
	}
	
	console.log(resp.data);	// raw data
});

// Converts filepath to raw data
filesource.getRawData("/files/example.pdf", function(resp){
	if(!resp.success)
	{
		console.log("Sth. went wrong: " + resp.error);
		return;
	}
	
	console.log(resp.data);	// raw data
});

// Converts web-source to readable filepath
filesource.getDataPath("http://blabla.com/blabla.pdf", function(resp){
	if(!resp.success)
	{
		console.log("Sth. went wrong: " + resp.error);
		return;
	}
	
	console.log(resp.data);	// local filepath
	
	resp.clean();
});

// Converts raw data to readable filepath
var rawData = fs.readFileSync("/files/example.pdf");

filesource.getDataPath(rawData, function(resp){
	if(!resp.success)
	{
		console.log("Sth. went wrong: " + resp.error);
		return;
	}
	
	console.log(resp.data);	// local filepath
	
	resp.clean();
});
```