# Serverless Functions

Serverless functions reduce the barrier of entry for building more complex apps, because the maintenance of the [[server]] is not needed.

Functions also serve as middleman between multiple [[api's services]], making easier the manipulation of request and responses.

#### Limitations
- Not built for long running processes, more than 30secs need another approach like [[netlify#Background Functions|background functions]]
- primary stateless.
- cold start performance.


### Structure of  a Serverless Function
Each function should export a handler, this handler will be an async function and return a response object with a status code and a body. The body needs to be stringifyied 

```js
// common js
exports.handler = async function () {
 return {
	 statusCode: 200,
	 body: JSON.stringify({
		 message: "Hello World",
	 }),
 };
};

// esm
export async function handler() {
 return { 
	statusCode: 200,
 	body: JSON.stringify({
		message: "Hello World",
	}),
 };
}
```

Call serverless functions with the directory `/.netlify/functions/function` to avoid  clash names when using with [[netlify]]

Serverless Functions receives to parameters (is this independent of service or only on [[netlify]])
- Event (with the information of the request made)
- Context (information of the serverless function context)


##### Code Considerations
- Because serverless functions run on [[node]], browser api's like [[node#^a9e571|fetch]]  doesn't work.



#### Services
- [[netlify]]
- [[vercel]]
- [[aws lambda]]