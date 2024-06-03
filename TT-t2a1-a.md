# Tom Tutone T2A1-A Workbook Part A

- Due 9.6.24 (2 weeks)

## Q1. Describe the architecture of a typical API project, such as a Flask application. /6

### -> ONLY Q to hold off on

- detailed explanation of the architecture of an application, at least one example or reference with descriptions of main components of an application

- high level view, what are the components relationships and how do they work together

Mozilla (n.d.) _[Explanation of a web framework](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Web_frameworks)_, MDN Web Docs website, accessed 31 May 2024.

- routing (Flask), Object-Relational Mapper (ORM) database layer that abstracts database read, write, query and delete operations (Django provides one, SQLAlchemy is an alternative), generating HTML?

Cindric, V. (2021) _[The Basics of Designing An API Architecture](https://hackernoon.com/the-basics-of-designing-an-api-architecture)_, Hackernoon website, accessed 31 May 2024.

Defining the methodology for running the API, API gateway, API portal

Architectural styles: Web API, Rest

Azure Devops (n.d.) _[Design APIs for microservices](https://learn.microsoft.com/en-us/azure/architecture/microservices/design/api-design)_, Microsoft website, accessed 31 May 2024.

- front end or backend - front end will use REST
- REST (http verbs) vs RPC (operations or commands)
- interface definition language (IDL) - define the methods and parameters and return values
- serialisations - how are objects serialised
- framework and language support - what language
-

Azure Article (2023) _[RESTful web API Design](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design)_, Microsoft website, accessed 31 May 2024.

- platform independence
- service evolution -> API should keep working even as app upgrades
- build around resources, resources have unique URI identifier, clients interact bt exchanging representations of resources HTTP requests, uniform interface standard HTTP verbs, stateless request model resources are the only place where information is stored increases scalability
- consistent naming convention in URIs, plural nouns for URIs that reference collections, plural/id
- relationship between types of resources such as '/customers/5/orders might represent orders for customer 5
- API is an abstraction of the database, separated from the database layout and each table data
- define API operations in terms of HTTP methods e.g./ /customers has a post get put and delete http action
- HTTP status codes
- versioning - making it so apps don't break as databases/API changes

### References

programmers.io (2023) _[The Basics of Designing An API Architecture](https://programmers.io/blog/basic-designing-of-api-architecture/)_, PostgreSQL website, accessed 31 May 2024.

## Q2. Identify a database commonly used in an API project (such as a Flask application) and discuss the pros and cons of this database. /6

- detailed explanation of identified database, detailed information about the pros and cons of this database supported by multiple references

- something like Postgres

SQL:

- a programming language for recording and interpreting data in a relational database
- uses rows and columns for different data attributes and to link relationships between value data
- SQL queries allow you to interrogate data in a database
- Amazon link here

PostgreSQL:

- open-source object-relational database system
- uses SQL language
- runs on all major OS
- can define your own data types
- write custom functions even ones in other languages than SQL and C, passed to a handler that knows the language, including Python, called procedural languages
- features many data types
- PostgreSQL about here

[PostgreSQL vs SQL Server: What are the key differences?](https://cloud.google.com/learn/postgresql-vs-sql)
[PostgreSQL About](https://www.postgresql.org/about/)
[What is SQL?](https://aws.amazon.com/what-is/sql/)

(<https://books.google.com.au/books?hl=en&lr=&id=jfKoCwAAQBAJ&oi=fnd&pg=PP1&dq=postgresql&ots=n3F3phg6TP&sig=6xnQ9Vt-ZvWQckrVpqcG3cbnSZ4#v=onepage&q=postgresql&f=false>)
(<https://www.prisma.io/dataguide/postgresql/benefits-of-postgresql>)
(<https://www.linkedin.com/pulse/postgresql-practical-guidefeatures-advantages-brainerhub-solutions>)

### References

(Amazon Web Services, 2024)
Amazon Web Services (2024) _[What is SQL?](https://aws.amazon.com/what-is/sql/)_, AWS website, accessed 24 May 2024.

PostgreSQL (n.d.) _[PostgreSQL About](https://www.postgresql.org/about/)_, PostgreSQL website, accessed 24 May 2024.

## Q3. Discuss an implementation of an Agile project management methodology for an API project. /6

- high detail description of agile project managment methodologies, more than one reference and example

- what is agile proj managements, how does it work, how can it be applied to an api project

- Agile management is breaking down work into objectives and dividing responsibilities to individuals
- it requires a project manager who can support the team members with expert knowledge
- requires consistent feedback to reflect on what is working and what is not
- demands face-to-face communication
- often contains a Kanban board which contains a physical and visual representation of goals
- in terms of API -> the objects would be broken down -> database, routing, database interaction, database updating, testing, API infrastructure and data returning format
- each of these would be broken down again and compartmentalised so that they can link up when neccessary
- deadlines would be emphasised on the things that need to be completed first such as the API infrastructure and database formatting

Agile project management is a collection of techniques used to break down the steps required to achieve a large goal. Broadly, agile projects begin with a team describing the steps neccessary to reach a goal, estimating the resources needed to achieve these sub-goals including time and personnel distribution, deciding which goals are most urgent, dividing the responsibilities amongst team members and constantly evaluating how each sub-goal is tracking (Moe, et. all, 2014). With these calculations, the team schedules iterations which are deadlines for an outcome to be achieved. In agile planning, a project manager is an active participant in the work who provides expert feedback on work and helps solve problems (Fernandez & Fernandez, 2008). However, agile methods also prioritise giving team members autonomy in their own time management and objectives. Agile projects also schedule feature regular face-to-face feedback loops where team members check-in on eachother's work, share their progress and difficulties and reflect upon their processes to identify what is working and what needs altering moving forwards. Finally, a typical feature of agile projects is a kanban board where team members write sub-goals on sticky notes and track their progress by moving them into sections such as "to do", "in progress", "need help", "review" and "finished". The kanban board is updated as team members reach challenges or during feedback sessions (Moe, et. all, 2014).

Utilising agile project management to create an API would require a team to first break down the process into features and components. For an API this would include API infrastructure and the decision of what software and modules will be used, database initialising and seeding, routing, database interaction functions from the app such as adding data, testing of the app, testing of the database and standardising data returns. The highest priority task would be to decide upon the API infrastructure and which software will be used. In an agile project, it would likely be beneficial if all team members have a chance to weigh-in on the tech stack. After this is decided, the team would estimate how long each task would take and create a kanban board to monitor progress. The project manager would lead the team in defining iterations and deadlines for the team to achieve. These deadlines would prioritise the objectives which are neccessary for other sub-goals including the database initialisation which needs to be completed so that the routing can connect to it. With the kanban board created and iterations defined, the team members would divide the work amongst themselves, with input from the project manager. The project manager would also schedule regular check-ins so that the team members can update eachother on their progress and voice challenges. As the team members meet, challenges would be shared and the team could continually adjust its goals, potentially changing their responsibilities or collaborating on specific tasks if they are overwhelming an individual. In addition, the project manager would continually evaluate the relevance of each feature and consider adding or removing any features.

## Need to include one example!!??

### References

Brede Moe, N., Dingsøyr, T., Dyba, T. (2014) 'Agile Project Management', in Ruhe, G., Wohlin, C. (eds.) _Software Project Management in a Changing World_. Berlin: Springer-Verlag, pp. 277-300.

Fernandez, D. J. and Fernandez, J. D. (2008) ‘Agile Project Management —Agilism versus Traditional Approaches’, Journal of Computer Information Systems, 49(2), pp. 10–17. doi: 10.1080/08874417.2009.11646044.

_[Agile Project Management?](https://d1wqtxts1xzle7.cloudfront.net/44069317/Agile_Project_Management20160324-890-sd99on-libre.pdf?1458831422=&response-content-disposition=inline%3B+filename%3DAgile_Project_Management.pdf&Expires=1717157391&Signature=J4wZBGad5~Fd1PJxz-9cQ4aEJenS-85l2KN1ApVUhztbTBbxxX4QQCXX6pyRC-B0BRdsJFvKp4EKck5lDf~FBSWevLmbStde2feg3Poc8oBwGeOoWhv~G2L4vXVe67PWspjG9jGHZM61f1wTA1SlbQalavfTq9ja-j3DNBszoXQBc6G3YJUa0oQ4nYl3LNUz~b3LIS-K2C5Fj~Da38t06kkdhiywj-J7YbqE4qtqT5ob7jfKmmJTJuSPLYaryztiCqWrDtGAtSjIgI-JyII2FrNQjqThAnUeMhURlPNMLNIvvIYp53n7wtjQPbH17D5rSCxp0tsWHhxr9whRqP1Epw__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA)_

- Complexity and uncertainty in software projects are particularly pertinent p279, difficult for  project team to consider tech organd environ states that affect the value of the outcome, need to ensure exrapolating past trends or relying on past experience
- AGILE strives towards a shorter time frame between planning and execution, planning an action does not provide all details of implementation
- self-management by teams besides a facilitator organising meetings and helping plan overcomming of obstacles
- a shift from up-front planning to focusing on the decisions made during the execution of a project
- still requires formal and informal modes of control hence team divisionbut with more self-management
- requires clear direction, supportive context, available coaching, team must be able to define strategies and process goals and resource allocation, share decision authority
- standup meetings to coordinate and plan daily work, short, quick decisions, identify and remove impediments
- frequent feedback loops, planning length/duration of an iteration, prioritise specific features, assign people to specific tasks
- assign goals by project leader in Scrum
- retrospectives - father data, what went well, what could be improved, changes to plans are made
- Kanbans - visual boards, highlights what is being worked on and to depict progress, to do, analysis, development, review, integration test, ready for deployment

_[AGILE PROJECT MANAGEMENT - AGILISM VERSUS TRADITIONAL APPROACHES](https://d1wqtxts1xzle7.cloudfront.net/60877253/Agilism_versus_Traditional_Approaches20191012-90316-mo9hff-libre.pdf?1570870002=&response-content-disposition=inline%3B+filename%3DAGILE_PROJECT_MANAGEMENT_AGILISM_VERSUS.pdf&Expires=1717157732&Signature=c39hTBCdQEQ9nGYC8zv~lLsluEaSbBqGbB-a2GEKpXuNtOERqew4Q81s7qSDiFy1KkoHEA6ZnFHaHJqvhSIPSGd3koNDVmyycxXcrXu8-hqn6p-U9wSquC9MeP4KV7hKSGaMEAOMXjyQtgvTIcX~1wSN1mqsIDk0AP7jSlpG0ijpQ5wPBmCDkdoBwLGoSKKcRVpU-6ZQOPUpQfuQkk8S8Ve2~EVenG3ftSTqliZcBpFE7WNDYsJOYuP5-Ng8zEcrmZNSfvX0B8~UCXAXhQp2o03qBpOh-UC-K~D7buC4-gW8QBp~yu7-ru1M-rEi5OY1NYfZtb5ygrbptlxLvqcV5w__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA)_

- 'distribute responsibility and initiative in support of adaptation' p 10
- distributing responsibility and initiative from manager
- simplicity, embrace change, focus on next effort, incrementally change, manage with a purpose, rapid feedback, small incremental deliverables, fluid requirements, face-to-face communication is best for information communication, deadline impacts the approach
- less defined features, do the project in iterations
- agile managers focus on deliverables
- useful when goals and solutions are unclear with high volatilaty

PostgreSQL (n.d.) _[PostgreSQL About](https://www.postgresql.org/about/)_, PostgreSQL website, accessed 24 May 2024.

## Q4. Provide an overview and description of a standard source control process for an API project. /6

- high detail, more than one reference and example

- process keyword

- leaf, branch, trunk, route analogy??

When initialising an API, it is vital that a source control strategy is designed and implemented because, eventually, clients and other applications will significantly depend on an API functioning in a predictable way. With this context in mind, it is standard for an API's source control process to be structured in a way that preserves the API's initial RESTful state on a main branch. Typically, any subsequent new features should be developed on forks of the main branch, with each fork representing a user story and use case (ozanseymen, 2016). These forks can be hosted in the main repository so that other developers can contribute to them also. It is imperative that these forks are continually merged with the main branch, as frequently as daily, so that they do not diverse from the released API's code and become redundant. Forking into separate branches stories allows for powerful source control as updates can be released only once they are safe to deploy and it also allows developers to work on features that depend on yet-to-be released features as well. Importantly, forks should not be merged to the main branch until they have been reviewed and tested extensively by a significant to prevent breaking the API.

In an API context, source control management often encapsulates versioning. Versioning is strategising that ensures an API preserves its RESTful quality and allows users to predictably interact with it (Kleier, 2020). APIs depend on stable data contracts between clients and servers any updates to APIs should eliminate or minimise changing these contracts, particularly without warning. When updating an API, changing a property name, response format or request convention or deleting an attribute can all break a user's application. Considering the sweeping impacts of these simple changes, an API's source control must segregate these alterations from the main branch and these types of changes should be considered when approving whether a fork is merged to the main branch. Alternatively, if breaking changes must be made, the API can be versioned in a way that preserves the main branch and the routing that any clients use. An API can be versioned by altering the routing conventions for new versions of the API such as "v2/users/<id>" or incorporating query parameters such as "api/tools?version=3" that new developers can use when engaging the API (Kleier, 2020). In this instance, the source control must consider these conventions by preserving the original main branch and creating a new main branch for features relating to the new format. Again, it is essential that any subsequent forks continually merge with the correct main branch at frequent intervals.

## CONSIDER THIS LINK for more references

[Semantic versioning guidelines](https://semver.org/)

ozanseymen (2016) _[Source Control for API Proxy Development](https://www.googlecloudcommunity.com/gc/Cloud-Product-Articles/Source-Control-for-API-Proxy-Development/ta-p/75620)_, Google Cloud Community website, accessed 31 May 2024.

- must define a repository strategy, how you will segregate different versions
- branching strategy - feature brances for individual user stories
- master branch - start and finish development of a new feature, should only accept merges from other branches as they are approved, should only contain stable code, can release after any commit on the mast branch
- feature branch - fork the master branch but keep it in the same repository so all members can work on it, once it is implemented and tested it can be merged with the master, allows programmers to delay the integration of a feature if it is not ready or its dependencies are not, stops erors too as other code is tinkered, master must frequently be merged with feature branch so it doesn't fall too far behind, merge with master at least once a day
- environment branches - environments that test the API emulating how it will be used upon release, branches should go through environment branches to ensure the changes hold up
- pull/merge requests - proposed changes should be reviewed before integration, the entire team should review and discuss the proposed changed, can also be used to trigger feedback
- commit messages - reflect the intention of the implemented changes rather than the contents, why rather than what
- squash multiple smaller commits into bigger ones for cleaner change history

Kleier, T (2020) _[How to Version a REST API](https://www.freecodecamp.org/news/how-to-version-a-rest-api/)_, FreeCodeCamp website, accessed 31 May 2024.

- API versioning is the practice of transparently managing changes to the api, so consumers know what to expect from it
- altering data contracts - the agreement on the shape or general content of a request or response
- versioning is needed so that the alteration of routing or attribute titles doesn't break consumers applications
- breaking changes: XML - JSON, changing a property name, adding a required field on a request new header or property in a request body, removing a property from the response
- effective change management - continue support for existing properties endpoints, add new properties/endpoints rather than change, thoughtfully sunset obsolete properties/endpoints (e.g./ returning meta data that says an attribute is being retired at a date)
- consider scope - tree model - leaf altering an isolated endpoint, branch altering a group of endpoints, trunk an application-level change warranting a version change on most endpoints, root a change affecting access to all API resources of all versions
- at branch, can introduce a new name for the last/second last folder of directory
- trunk demands version change
- URI path - <www.example.com/api/v1/products>
- can include query parameters - <http://www.example.com/api/products?version=1>
- can feature version in headers of requests

## References

Kleier, T (2020) _[How to Version a REST API](https://www.freecodecamp.org/news/how-to-version-a-rest-api/)_, FreeCodeCamp website, accessed 31 May 2024.

ozanseymen (2016) _[Source Control for API Proxy Development](https://www.googlecloudcommunity.com/gc/Cloud-Product-Articles/Source-Control-for-API-Proxy-Development/ta-p/75620)_, Google Cloud Community website, accessed 31 May 2024.

## Q5. Provide an overview and description of a standard testing process for an API project. /6

- high detail explanation of standard testing process, more than one reference and example

- tests should be written and implemented at all stages of development and maintained so they can incorporate evolving functionality (myakundi)
- maintain and preserve mock data for testing (postman)
- testing involves trying to break a system in a way that a user might (soap ui)
- Jorgensen & Whitaker prescribe two testing methods and suggest their combination: category partitioning and Markov modelling, category partitioning is noting choices that trigger default responses, test those and the boundaries, write them into the test, incorporate Markov modelling too which is identifying the different conditions that affect an outcome, testing those with varied sequencing
- this Markov modelling mirrors end-to-end testing which is testing user journeys by chaining requests together (postman)
- testing should check for security vulnerabilities (soap, myakundi)
- authenticate before the data is sent, ensure a security token is passed with each API request (soap)
- ensure that SQL injection, the manual altering of SQL commands cannot occur (myakundi)
- contract testing and load testing
- testing tools include Insomnia, Postman, Soap UI (myakundi)

In application development, tests should be written and executed throughout all stages of development and maintainted to incorporate evolving functionality (Myakundi, 2022). In an API context, standard testing must contain contract testing and the stability of request and response formatting, singular end-point unit tests, user journey testing and the chaining of requests, as well as load testing and the API's ability to respond at an appropriate speed when faced with increased traffic (Postman, n.d. and SoapUI, 2024a).

When designing the specific tests, Jorgensen and Whitaker (2000) recommend category partitioning and Markov modelling to identify values to test with. Category partitioning recommends identifying all inputs that trigger default responses and testing at these boundaries. In an API interaction, this could refer to a required length or typing in a particular field. After identifying these breaking points, tests should submit these values as well as values that just qualify such as 0 and 1 for an input that must be greater than 1. They also recommend using Markov modelling which is identifying the different conditions that affect an outcome and testing those with varied sequencing. In an API context, this could refer to testing the result of a request when a user is authenticated versus not and then sequencing this with a different condition such as if the user's previous request was successful or not. Markov modelling is similar to end-to-end testing which tests user journeys and sequenced requests (Postman, n.d.).

In addition to typical functionality testing, it is also vital to test the security of an API (SoapUI, 2024b). The authentication process of an API must be tested to confirm that the API does not sent data before confirming the identity of a user and ensuring this process perseveres when the server is receiving increased requests. Security tests should also ensure that users cannot submit requests with abnormal frequency, a typically malicious practice. Finally, APIs should be investigated to ensure they do not allow SQL injection that sends custom requests to the database (Myakundi, 2022).

Overall, API testing must consider functionality, performance and security. To most effectively test these elements, developers should maintain specific tests that incorporate appropriate mock data to emulate user interaction with an API (Myakundi, 2022). Tools that can help with these tests include Insomnia, Postman and SoapUI.

## References

Jorgensen, A., Whittaker, J. (2000) _An API Testing Method_, Florida Tech.

Myakundi, H. (2022) _[API Testing Best Practices - How to Test APIs for Beginners](https://www.freecodecamp.org/news/rules-of-api-testing-for-beginners/)_, FreeCodeCamp website, accessed 31 May 2024.

Postman (n.d.) _[API Testing](https://www.postman.com/api-platform/api-testing/)_, SoapUI website, accessed 3 June 2024.

SoapUI (2024a) _[API Testing 101: Learn The Basics](https://www.soapui.org/learn/functional-testing/api-testing-101/)_, SoapUI website, accessed 3 June 2024.

SoapUI (2024b) _[State of API Security](https://www.soapui.org/learn/functional-testing/api-testing-101/)_, SoapUI website, accessed 3 June 2024.

SoapUI (2024a) _[API Testing 101: Learn The Basics](https://www.soapui.org/learn/functional-testing/api-testing-101/)_, SoapUI website, accessed 3 June 2024.

- tests should cover individual functionalities and series of functionalities checking how they work together
- does what it's supposed to do, can handle the load, find all ways the users can mess things up, APIs work across devices browsers and OSs
- create testing environments that emulate the requests
- all types of testing

SoapUI (2024b) _[State of API Security](https://www.soapui.org/learn/functional-testing/api-testing-101/)_, SoapUI website, accessed 3 June 2024.

- authenticate at the web server before data is transferred
- authentication is determining the identity of an end user
- the token is passed with each API request and validated before the request is processed
- use https
- can use API gateway, can implement quotas and throttling

Postman (n.d.) _[API Testing](https://www.postman.com/api-platform/api-testing/)_, SoapUI website, accessed 3 June 2024.

- contract testing - check the content and format of requests and responses
- unit testing - confirm a single endpoint returns a correct response to a given request including optional parameters and appropriate error message
- end-to-end testing - testing user journeys by chaining requests together
- load testing - testing large volumes of requests concurrently to check response times and error rates
- create testing enviroments with mock data
-

Jorgensen, A., Whittaker, J. (2000) _An API Testing Method_, Florida Tech.

- category partitioning - create a set of categories that describe properties of inputs, partition the categories into choices that trigger specific values that can be input, determine constraints that describe how the choices interact
- think of the attributes of an input such as length and data type and content, consider specific values that trigger a default response, test the boundaries e.g./ 0 and 1 if at least one is the minimum, combine rule breaks such as length 0 and no spaces make both occur, then write these values into test
- Markov modelling - identify the application the inputs, investigate possible operational modes that modify its behaviour, identify expected values based on the operational modes affecting the behaviour then test these, will generate many potential occurences such as how many files, read, write, does not exist, file 1/2, file 0/2 etc., test with varied sequencing of operational modes
- hybrid technique, combining category partitioning and markov modelling - consider limits and boundaries and different state concurrently

Myakundi, H. (2022) _[API Testing Best Practices - How to Test APIs for Beginners](https://www.freecodecamp.org/news/rules-of-api-testing-for-beginners/)_, FreeCodeCamp website, accessed 31 May 2024.

- manual testing involves tools such as Insomnia, Postman
- check for security vulnerabilities
- SoapUI, Runscope, Postman
- testing principles: continuous integration and delivery testing, tests should be easy to write and maintain, test at the boundary of the system, keep tests small and focused, make sure tests are deterministic
- test functionality, performance and security (such as SQL injection)

## Q6. Explain the three principles of information system security. /6

- three information system security requirements at a moderate level of detail, supporting the explanation with at least one reference or example

- A good one to answer early

Babenko, M., Schwiegelsohn, U., Talbi, E. & Tchernykh, A. (2019), 'Towards understanding uncertainty in cloud computing with risks of confidentiality, integrity, and availability'. _Journal of Computational Science_, vol. 36, DOI:[10.1016/j.jocs.2016.11.011](https://doi.org/10.1016/j.jocs.2016.11.011)

- Confidentiality, Integrity and Availability (CIA)
- cloud increases security risks by shifting traditional models
- confidentiality is limited access to information
- integrity as the assurance that the information is trustworthy and accurate
- availability as a guarantee of reliable access to the information by authorised people
- data encryption, user identity documents (IDs), passwords, cards, retina scans, voice recognition and fingerprints, security tokens, key fobs
- savailability can compromised by bottlenecks, redundancy, hardware failure, speed om retirm
- sharing resources with other virtual machines can slow, vms performance is unpredictable, physical hardware can slow vms even if a guaranteed speed is promised
- information security assumes defending information from unauthorized access, use, disclosure, disruption
- must consider accidental threats and failures
- these authors propose "accountability" to protect data by all users who process the data
- cryptographic protocol and error correction codes can reduce the risk
- accidental threats include user errors, carelesslness, curiosity
- check sums for monitoring obtained results
- challenges because resource scheduling is difficult when the resource is shared amongst unknown users
- data replication but is dangerous, secret sharing schemes (SSS) dealer distributes shares to recipients such that only authorised subsets of recipients can reconstruct the secret, can use homomorphic encryption which retains data encryption whilst it is encrypted public key to encrypt and corresponding private key can unlock but can have effects applied to it that maintains the relationship to the data computation can occur on ciphers which matches the result of operations performed on the original numbers,

Olivier, M. (2002), 'Database privacy: balancing confidentiality, integrity aand availability'. _SIGKDD Explorer Newsletter_, 4(3),  DOI:[10.1145/772862.772866](https://doi.org/10.1145/772862.772866)

- each considered individually is easy to solve its the intersection of all that is challenging
- without availability unplugging the database is sufficient, anonymity can be a solution if private data is not captured it cannot be abused but availability of private data is important banks etc
- privacy is not simple as availability of personal information is a consideration
- privacy should consider why data needs to be recorded and the fall out for the two parties if it was leaked
- database privacy needs to consider the purposes for which the data was collected
- consenting to data storage, opt-in or opt-out is binary and challenges when a service is mandatory
- challenge develop systems that can find a balance between confidentiality integrity and availability
- could contain the data and verify or scatter the data and give links to those that need

Mitchell, O., Osazuwa, C. (2023), 'Confidentiality, Integrity, and Availability in Network Systems: A Review of Related Literature'. _International Journal of Innovative Science and Research Technology_, 8(12),  DOI:[10.38124/ijisrt](https://doi.org/10.38124/ijisrt)

-

## References

## Q7. Provide an overview of what would need to be done within an API project to implement at least one of the principles explained in Question 6. /6

Covert, Q., Francis, M., Streff, K. (2020). _Towards a Triad for Data Privacy_, DOI: [10.24251/HICSS.2020.535](https://doi.org/10.24251/HICSS.2020.535)

- overview is correct, supported by more than one valid relevant code with a high level of detail

## Q8. Explain the legal obligations that developers of a social media website or social media application would have in regards to handling user data, with reference to any applicable laws or acts. /12

- more than one legal obligation relevant to handling user data explained in high amounts of detail including relevant references to support the explanation

- incorporate international legal obligations, social media hosted in multiple countries

- look at GDPR (Europe) obligations and mention those

- A good one to answer early

## Q9. Describe the structural aspects of the relational database model. Your description should include information about the structure in which data is stored and how relations are represented in that structure. /6

- detailed description of the structural aspects of a relational database model with detailed descriptions of all structural relationship types

- a good one to answer early

## Q10. Describe the integrity aspects of the relational database model. Your description should include information about the types of data integrity and how they can be enforced in a relational database. /6

- detailed description of the integrity aspects, at least one integrity technique explained and supported by a relevant code example

- a good one to answer early

## Q11. Describe the manipulative aspects of the relational database model. Your description should include information about the ways in which data is manipulated (added, removed, changed, and retrieved) in a relational database. /6

- detailed description, all common manipulative operations explained

- SQL code examples including joins

- a good one to answer early

## Q12. Conduct research into a web application (app) and answer each of the following sub-questions: /42

- if you can't find how it was built, pick a different app

- builtwith.com - explains tech stack of a website

- open-source apps are great for this q so you can see schema data and source code

Firefox. Open-source.
[Data stores](https://mozilla.github.io/firefox-browser-architecture/text/0010-firefox-data-stores.html),
[Data storage set-ups including ERDs](https://github.com/mozilla/firefox-data-store-docs),
[Mozilla Wiki](https://wiki.mozilla.org/Main_Page),
[Stack description](https://wiki.mozilla.org/EngineeringProductivity/Projects/Conduit/Tech_Stack),

Instagram.
[Techstack](https://stackshare.io/instagram/instagram)
[Info on Django](https://instagram-engineering.com/web-service-efficiency-at-instagram-with-python-4976d078e366)
[Presentation on Instagrams Django/Python usage](https://www.infoq.com/presentations/instagram-scale-infrastructure/)
[Linked in description of their tech stack](https://www.linkedin.com/pulse/choosing-right-tech-stack-instagram-example-vijay-mendiratta)
[Instagram developers blog tech stack](https://instagram-engineering.com/what-powers-instagram-hundreds-of-instances-dozens-of-technologies-adf2e22da2ad)

### 1. List and describe the software (tech stack) used by the app

- detailed description of the software, multiple references to support the description

### 2. Describe or make educated guesses about the hardware used to host the app

- detailed description, multiple references to support the description

- how much CPU would it need and network bandwidth

### 3. Describe the interaction of technologies within the app

- detailed description, identifies the roles and purposes of all technologies described

- can make educated guesses as well

- one thing assessed is logical deductions if data isn't explained

### 4. Describe the way data is structured within the app’s database(s)

- detailed understanding of the data structure and includes an example or reference about why the database structure was chosen for the real world application

- more of a high level assessment

### 5. Identify the entities/tables that are tracked within the app’s database(s)

- identifies all significant entities including additional entities required to optimise or normalise the db structure

- if the user can do this, then the database MUST store, front-end informing guesses to make it work

### 6. Identify the relationships and associations between the entities/tables identified in sub-question E

- identifies ALL relationships/associations in a sophisticated relational model

### 7. Design an entity relationship diagram (ERD) based on the answers provided to sub-questions 5 and 6. This must represent a relational database model, even if the app itself uses something other than a relational database model

- a normalised ERD (without data duplication) that facilitates full functionality of the app
