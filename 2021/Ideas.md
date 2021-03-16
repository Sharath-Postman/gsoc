Postman in Google Summer of Code 2020 - Ideas
=============================================

## Project Ideas

We accept original ideas and proposals for every project. Following is a list of ideas which you can use as a reference.

### Newman 

* **Newman login**: Add support for a new `newman login` command to be an alternative to the conventional way of using cloud URLs to run collections. It will allows users to login with their API key from CLI and simply run collections by providing their unique IDs. This will also require dedicated security considerations to ensure safety of user's Postman API key.

* **Create new or update existing reporters**: Newman reporters provide information about the current collection run in a format that is easy to both: disseminate and assimilate. Create new external reporters or update existing reporters like `newman-reporter-html`. Working examples of how Newman reporters work can be found here - https://github.com/postmanlabs/newman/tree/develop/lib/reporters

* **Ability to execute individual requests**: Currently, you can run entire Postman collections. Add the capability the run a single request - not the whole collection.

### Collection SDK + Runtime
* **Support for more request bo**

### Code Generators

### Idea 1: Newman Request
Newman already makes it effortless for you to run Postman collections. It enables you to see the results with your favourite reporters on CLI, as JSON, HTML etc. making it easy to summarise data and at the same time, use it in automations and build systems. But currently, it is limited to only running a collection of requests. This project aims to enable users to use these same capabilities for a single request.

Expected outcome
Users can send a single request with Newman and show the request/response using a reporter of their choice.
Replacing curl with newman request in a curl command should run the send the request using Newman.
If user is logged in, the request should show up in Postman app’s History in sidebar.

Relevant skills
JavaScript language
Understanding of HTTP protocol.
curl

Complexity: low 

### Idea 2: Parallel Iterations in Newman
Newman supports running multiple iterations of a collection with different data provided in a CSV or JSON file, enabling users to test an API against multiple scenarios. But Newman executes each iteration serially and this can take a lot of time as the number of requests in a collection and iterations grow. This project aims to bring parallelism into Newman by splitting the iterations data into multiple chunks and running them as threads to bring down the total time roughly by a factor of n, where n is the number of threads.
Expected outcome
Newman can split iteration data and run multiple runs using this data.
Users can specific the number of parallel iterations that Newman can run.
Relevant skills
JavaScript language
Understanding of threads and processes communication
Complexity: low 

### Idea 3: Newman Dashboard
Newman has an array of reporters that consume the run data that Newman provides. These include viewing a run in the terminal using CLI, as JSON which can be easily transported by a build system, as an HTML summary webpage, and many more. However, Newman lacks a way to control the runs in a central dashboard. This project aims to create a dashboard on a browser which can be used to start, resume, pause and stop Newman runs.
Expected outcome
A dashboard can be opened on a browser which shows currently running Newman runs.
The dashboard can be used to start, stop, pause and stop any Newman run.
There is an option in Newman to connect to the dashboard and wait for run to be started by the dashboard.
Relevant skills
JavaScript language
Understanding of daemons and IPC (websockets is a plus).
Basic understanding of HTML, CSS
Complexity: medium

### Idea 4: API-First Blueprint for a Commerce API
Building out an OpenAPI, mock, documentation, testing, and deployment of a commerce (or other) API that uses the Schema.org as the underlying schema, providing a functioning and well documented example of what an API can be.
### Idea 5: API Conversion API
Aggregating all of the OpenAPI conversion tooling that exists out there into a single API conversion solution that will convert all API formats similar to API Transformer - https://www.apimatic.io/transformer/, publishing as a single API that can be hosted and operated by anyone as an open source conversion solution.

### Idea 6: Open API Postman Public Workspace
https://www.postman.com/api-evangelist/workspace/openapi/overview
 
### Idea 7: Simple schema registry
Provide a simple implementation of the schema registry API and showcase how this can be used with AsyncAPI document and schema references. It can do an in-memory persistence for schemas as it would be used purely for showcases, and learning materials.
Use case:
In AsyncAPI file you can provide schemas for the payload of the message. Those schemas can be shared between different applications, meaning, different AsyncAPI files. Schema registries that store such shareable schemas are becoming a de-facto standard. Would be great to have a simple mock implementation of such schema to show how would it work with AsyncAPI documents.
Required knowledge: 
You do not need any specific deep knowledge of any subject here. You will only have to provide an implementation of this API. It is not supposed to be a production-ready implementation, but only for testing and showcasing. Knowledge about how to use this registry with AsyncAPI is something that you can learn while working on the task with mentor support. There is not specific repository where you can place the code. It is something that can be decided anytime during development.

### Idea 8: Duplications discovery - optimizer
Build a library that code-first users would benefit from the most but not only. A library that as the input gets AsyncAPI document and as output provides optimized AsyncAPI document. For example:
Reuse of components
Duplicated schemas moved to components and ref-ed from a message
Remove not used components
The goal is to shrink the document to a minimum. There should be flags to disable specific parts of optimization, like removal of not used components for example.
Use case:
AsyncAPI offers many different ways to reuse certain parts of the document like messages or schemas definitions or references to external files, not to even mention the traits. There is a need for a tool that can be plugged into any workflows and optimize automatically documents that are generated from code. 
Required knowledge: 
This task will require from you learning some details about the AsyncAPI spec to 
understand what parts can be componentized and how reuse works in the spec. This knowledge will be essential to be able to apply optimizations. You will for sure have to go through our getting stated guides and later the spec. Mentors will be available for any questions and setting directions.
We already started work on the CLI so before summer there will be enough to plug in this functionality https://github.com/asyncapi/cli  

### Idea 9: AsyncAPI Diff
A library that as the input gets two AsyncAPI documents and shows changes between them. As an output, you get json pointers to sections that are different. The main purpose of such a tool is a changelog where you can present to the user what has changed between v1 and v2 of the document. Some ideas can be picked up from https://github.com/OpenAPITools/openapi-diff  
We basically need a library that can be later used to build such a UI
Use case:
The result of diff is a part of changelog/release notes, so users can easily spot what parts of the document changed so they can understand how affected they are by the change
Diff is needed in a review process, so the reviewer gets an overview of specification changes
Required knowledge:
There is not much knowledge about the spec itself needed. It is about pointing out differences in 2 different files, but not as pointing what lines changed but in general what objects changed. So if there was an update in payload, the library must specify what channel in what message got updated (with json pointers most probably). You can familiarize with other tools that do it already for other specifications.
We already started work on the CLI so before summer there will be enough to plug in this functionality https://github.com/asyncapi/cli

### Idea 10: AsyncAPI Applications Relations Finder
A library that as the input gets a list of AsyncAPI documents and analyzes them to get information about Applications described by those files:
If they subscribe or publish to the same channels
If one subscribes to a channel that the other one publishes to
If there are apps that are subscribed to channels that no one publishes too
As an output, we should get a format that can be used to generate a diagram of relations between applications with additional metadata information about them (message, schemas).
 
 
Use case:
Visualization of the architecture and understanding what happens with the system if one of the puzzles is removed.
Later on, we could use this library in AsyncAPI CLI and also the AsyncAPI Studio.
Required knowledge:
There is no need to have any experience in event-driven architecture. You do not even need to know AsyncAPI spec too much. It is a pure coding task where you will need to find matching patterns between different documents and return this information. You will have the full support of the mentor on the subject. Mentor will define requirements, etc.
There is no decision yet if this is a library that will have to live in a separate repository or be a part of an existing CLI or UI project.
We already started work on the CLI so before summer there will be enough to plug in this functionality
asyncapi/cli  
 
### Idea 11: AsyncAPI Extensions registry
Provide an implementation of the extensions registry for AsyncAPI. This task includes action points:
- improve the shape/definition of the single extension (describe it by JSON Schema) - reference
asyncapi/extensions-catalog
- like for schema registry: implement an extensions registry API
- add support in parser-js -
asyncapi/parser-js  - for validation of extension against provided extension schema
 
Required knowledge:
The main contribution will go into the parser. So you will have to first onboard on the project with few basic tasks handed over by the mentor. The rest will be explained by the mentor. 
### Idea 12:  Chatbot for AsyncAPI creators
Explore how we could help people to write the spec document without knowing the specification. Prepare a kind of prototype. Instead of learning the spec, users talk to a chatbot, and as a result of the conversation, they get an AsyncAPI document generated. The chatbot should learn from the specification what are the possible solutions and options.
Use case:
Learning the AsyncAPI spec can be a time-consuming process. This is what causes learning of every new specification hard. Let’s explore if we can have a machine that can consume the spec, its JSON schema and serve the users as an expert. Basing on a set of questions and answers it should generate an AsyncAPI document for the user.
Example conversation: (real-time we show a preview of the AsyncAPI document that will be generated)
Bot: what do you want to describe?
User: app that connects with kafka?
Bot: can you provide some more details about the kafka server? Like the url?
User: no
Bot: no problem, let us skip the server details for now. What topics does your app subscribe to?
 
Visible challenges:
Vocabulary: bot needs to know that AsyncAPI channels mean topic in Kafka
Real-time object generation
Vocabulary: understand that bot needs to ask questions “subscribe to” but in document write it as “publish” operation
 
Required knowledge:
This project requires you to have a basic knowledge about the location of spec related materials that could be used to feed the bot. This is a research task that only requires a prototype to see if this is even possible or what is missing to make it possible. As prerequisite you of course need to read about current technologies that are available for building a chatbot
Idea 13: AsyncAPI application simulation
A simulation library that can trigger events in your applications based on AsyncAPI definition(s). The main purpose is to stimulate your application(s) in a development environment (staging?). Use it for stress testing, hunting down concurrency problems, stimulating visual applications, finding scalability issues in your application and more.
You provide one or more AsyncAPI files
You decide which channel(s) and applications should be stimulated and with which parameters.
The library simulates messages to the application(s) based on the parameters, in the given protocol described in the AsyncAPI file. 
Inspect the application(s) and their state to figure out if errors occurred etc
 
Extra thoughts: 
Can it be used directly in a system test so you can decide on the expected outcome?
Required knowledge:
You need to learn the spec basics (what channels are). It will be useful to learn first how to setup environments with Docker compose and mocks and a proper testing environment will have to be created first to work on the implementation and load generation.

