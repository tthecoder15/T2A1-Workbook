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

When initialising an API, there is a variety of paid and open-source software that can be used to create and link a database. These include relational and non-relational databases. Two of the most popular open source databases are the relational databases PostgreSQL (Postgres) and MySQL. Both use SQL to interact with stored data and each has benefits in how they are designed. A key feature of Postgres is its default robustness, installing with many features which must be adding with additional modules an packages in MySQL. Postgres has MVCC (multiversion concurrency control) built into it which is a key benefit in many usage context. MVCC configures Postgres to access snapshots of data rather than access the live data specifically. This means that data is not locked when it is being accessed, either queried or written to, so that multiple transactions can place concurrently (PostgreSQL Documentation, n.d.). This is beneficial in many API contexts where data could be required by two or more systems at once. Postgres is also ACID (Atomicity, Consistency, Isolation, Durability) compliant so that errors will not corrupt data (Amazson Web Services, 2024). Another benefit of Postgres is that it allows for parent-child relationships and inheritance without installing additional packages. These are some of the distinct advantages of Postgres over its competitors.

In terms of negatives, a key consideration when choosing Postgres versus an alternative is a higher overhead cost to initialise and utilise Postgres (Amazon Web Services, 2024 & Hanlon et al., 2011). Because Postgres is strict when inputting data, formatting schema and seeding data, users must be experienced in how the system works to use it effectively. In addition, tuples cannot be seeded unless they completely alligns with the data structure of the database meaning that data will often have to be screened or edited before it can be saved. This is a negative in more dynamic data storage environments where saving results is the first priority. This, again, becomes a problem when migrating data from and old or different system to be stored in Postgres (Hanlon et al., 2011). Postgres is also resource intensive and returns read queries slower than MySQL or alternative, non-relational databases such as CouchDB (Amazon Web Services, 2024 & Hanlon et al., 2011).

In totality, Postgres strictness and robustness is a signature strength of the database but also causes some drawbacks. It is important to consider the frequency and type of requests an API will receive when choosing a database for it.

Amazon Web Services (2024) _[What's the Difference Between MySQL and PostgreSQL](https://aws.amazon.com/compare/the-difference-between-mysql-vs-postgresql/)_, AWS website, accessed 6 June 2024.

- Postgres is an object-relational database management system rather than just relational database
- Postgres has more data types, scalability and data integrity
- open-source, free to update software versions
- Postgres is fully ACID compliant in all installations where as MySQL, a main alternative requires additional installations
- Again, Postgres features multiversion concurrency control without additional installs, MySQL locks rows when writing
- Postgres supports parent-child relationships and inheritance as well as arrays and XML which MySQL does not
- Postgres allos users to store procedures written in languages other than SQL

Cons:

- Postgres requires more technical set up and configuration set-ups and advanced commands
- MySQL reads faster

Hanlon, M., Dooley, R., Mock, S., Dahan, M., Nuthulapati, P. & Hurley, P. (2011). _Benefits of NoSQL databases for portals & science gateways_. DOI:[10.1145/2016741.2016780](https://doi.org/10.1145/2016741.2016780).

- overhead of SQL databases is expensive, data-intensive interfaces, data not fitting the models cannot be fit in and must be redesigned or augmented, must migrate old data from old systems to new systems
- these authors argue for NoSQL platforms or non-relational databases in certain circumstances because it loads faster
- alternatives are platforms like CouchDB which delivers a RESTful API

PostgreSQL Documentation (n.d.) _[13.1 Introduction: Chapter 13 Concurrency Control](https://www.postgresql.org/docs/16/mvcc-intro.html)_, PostgreSQL website, accessed 6 June 2024.

- multiversion concurrency control means that each SQL statement accesses a snapshot of data rather than the current state which prevents queries from accessing updating data but allowing users to access data at a given moment rather than being locked out for changes

### References

Amazon Web Services (2024) _[What is SQL?](https://aws.amazon.com/what-is/sql/)_, AWS website, accessed 24 May 2024.

Hanlon, M., Dooley, R., Mock, S., Dahan, M., Nuthulapati, P. & Hurley, P. (2011). _Benefits of NoSQL databases for portals & science gateways_. DOI:[10.1145/2016741.2016780](https://doi.org/10.1145/2016741.2016780).

PostgreSQL Documentation (n.d.) _[13.1 Introduction: Chapter 13 Concurrency Control](https://www.postgresql.org/docs/16/mvcc-intro.html)_, PostgreSQL website, accessed 6 June 2024.

## Q3. Discuss an implementation of an Agile project management methodology for an API project. /6

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

The three principles of information system security are confidentiality, integrity and availability. These principles are commonly valued when creating data services and implementing security measures to protect them.

Confidentiality considers the legal and ethical obligations of data stoage to protect data from being released to inappropriate viewers (Mitchell and Osazuwa, 2023). In a medical database, an individual's name, birthdate, ailments and treatment history could be stored and an individual has a right to keep this information private. However, when receiving treatment, it is appropriate for a doctor to access this data to help their assessments. Confidentiality also considers when an individual has the right to consent or not consent to their data being stored or accessed (Olivier, 2002).

Integrity in information system security refers to data being trustworthy and accurate (Babenko et al., 2019). This means that data should not be alterable in unauthorised or disingenuous ways and, as such, security systems should only allow authorised users to alter data (Mitchell and Osazuwa, 2023). For example, a medical practitioner could be allowed to update an individuals health records so that they accurately reflect a new set of blood tests or diagnoses. Evidently, integrity and confidentiality are interconnected as anyone updating a piece of data manually would then know the new value recorded.

Availability is ensuring data can be accessed by authorised individuals when it is required (Babenko, et al., 2019). Availability can be considered as a right of the user when they consent to their data being stored as, otherwise, it may have been inappropriate to store that data (Olivier, 2002). Notably, availability is threatened by the failure of webservices or server functions due to hardware faults, clogged communication channels and the lack of a fallback strategy to access the information (Mitchell and Osazuwa). In a medical field, availability could refer to a doctor having access to a patient's allergies when giving them medication.

Notably, confidentiality, integrity and accessibility are interconnected and must be balanced if they are to co-exist. Individually, any principle could be prioritised but it would come at the expense of another such as keeping a server offline which could preserve integrity but would significantly limit availability (Olivier, 2002).

Babenko, M., Schwiegelsohn, U., Talbi, E. & Tchernykh, A. (2019)

- Confidentiality, Integrity and Availability (CIA)
- cloud increases security risks by shifting traditional models
- confidentiality is limited access to information
- integrity as the assurance that the information is trustworthy and accurate
- availability as a guarantee of reliable access to the information by authorised people
- data encryption, user identity documents (IDs), passwords, cards, retina scans, voice recognition and fingerprints, security tokens, key fobs
- availability can compromised by bottlenecks, redundancy, hardware failure, speed om retirm
- sharing resources with other virtual machines can slow, vms performance is unpredictable, physical hardware can slow vms even if a guaranteed speed is promised
- information security assumes defending information from unauthorized access, use, disclosure, disruption
- must consider accidental threats and failures
- these authors propose "accountability" to protect data by all users who process the data
- cryptographic protocol and error correction codes can reduce the risk
- accidental threats include user errors, carelesslness, curiosity
- check sums for monitoring obtained results
- challenges because resource scheduling is difficult when the resource is shared amongst unknown users
- data replication but is dangerous, secret sharing schemes (SSS) dealer distributes shares to recipients such that only authorised subsets of recipients can reconstruct the secret, can use homomorphic encryption which retains data encryption whilst it is encrypted public key to encrypt and corresponding private key can unlock but can have effects applied to it that maintains the relationship to the data computation can occur on ciphers which matches the result of operations performed on the original numbers,

Olivier, M. (2002)

- each considered individually is easy to solve its the intersection of all that is challenging
- without availability unplugging the database is sufficient, anonymity can be a solution if private data is not captured it cannot be abused but availability of private data is important banks etc
- privacy is not simple, availability of personal information is a consideration
- privacy should consider why data needs to be recorded and the fall out for the two parties if it was leaked
- database privacy needs to consider the purposes for which the data was collected
- consenting to data storage, opt-in or opt-out is binary and challenges when a service is mandatory
- challenge develop systems that can find a balance between confidentiality integrity and availability
- could contain the data and verify or scatter the data and give links to those that need

Mitchell, O., Osazuwa, C. (2023)

- CIA triad - confidentiality, integrity and availability
- confidentiality refers to the ethical and legal need to protect sensitive information from disclosure
- organisations may experience financial losses, reputational harm or legal consqeuences due to data breaches
- appropriate authority to alter the data, hash functions and digital signatures are cryptographic methods for data iintegrity
- unforseen periods of operational inactivity arising from technological malfunctions or cyber intrusions imprede organisational processes, require failover methods
- the triad is interlinked and a failure of any would cause a failure in the others
- mirrored systems ensure redundancy, load-balancing techniques that distribute traffic, disaster plans all preserve availability
- phishing is confidentiality threat, data breaches
- availability denial-of-service (DOS), DDOS is the same but numerous sources do the attack
- recommendations: incorporate emerging technologies, holistic approach to security, cross-disciplinary collaboration (policy makers & tech experts),

## References

Babenko, M., Schwiegelsohn, U., Talbi, E. & Tchernykh, A. (2019), 'Towards understanding uncertainty in cloud computing with risks of confidentiality, integrity, and availability'. _Journal of Computational Science_, vol. 36, DOI:[10.1016/j.jocs.2016.11.011](https://doi.org/10.1016/j.jocs.2016.11.011)

Mitchell, O., Osazuwa, C. (2023), 'Confidentiality, Integrity, and Availability in Network Systems: A Review of Related Literature'. _International Journal of Innovative Science and Research Technology_, 8(12),  DOI:[10.38124/ijisrt](https://doi.org/10.38124/ijisrt)

Olivier, M. (2002), 'Database privacy: balancing confidentiality, integrity aand availability'. _SIGKDD Explorer Newsletter_, 4(3),  DOI:[10.1145/772862.772866](https://doi.org/10.1145/772862.772866)

## Q7. Provide an overview of what would need to be done within an API project to implement at least one of the principles explained in Question 6. /12

## BIG ONE

- overview is correct, supported by more than one valid and relevant relevant code example with a high level of detail

Covert, Q., Francis, M., Streff, K. (2020). _Towards a Triad for Data Privacy_, DOI: [10.24251/HICSS.2020.535](https://doi.org/10.24251/HICSS.2020.535)

- JWT
- bcrypt

## References

## Q8. Explain the legal obligations that developers of a social media website or social media application would have in regards to handling user data, with reference to any applicable laws or acts. /12

## BIG ONE

- more than one legal obligation relevant to handling user data explained in high amounts of detail including relevant references to support the explanation

- incorporate international legal obligations, social media hosted in multiple countries

- look at GDPR (Europe) obligations and mention those

- A good one to answer early

## Q9. Describe the structural aspects of the relational database model. Your description should include information about the structure in which data is stored and how relations are represented in that structure. /6

- detailed description of the structural aspects of a relational database model with detailed descriptions of all structural relationship types

The relational model is a format for describing and storing data in a standardised table format. The relational model is utilised in relational databases which contain collections of tables to be accessed in flexible ways whilst preserving the data's integrity (Jatana et al., 2012). These tables, also known as relations, feature columns which describe attributes of an entity, formatted in defined data types, and are seeded with rows that represent individual sets of data, also known as tuples (Geeks for Geeks, 2024a). A table and the columns it features is referred to as the relation schema.

Relations are configured with primary keys, values that are unique to a specific tuple and make each row distinct (Oracle, n.d.). The relational model also allows distinct tables to be linked by sharing a primary key from one table to be used as a primary key in a different table. The borrowed primary key is called a foreign key. Tables can also be configured so that their primary key is comprised of two values combining to make a unique identifier. This is called a composite key. Finally, two or more tables can also contribute foreign keys to create a primary key in another table called a compound key (BBC, n.d.).

Primary keys, foreign keys, composite keys and compound keys allow for the different types of cardinal relationships. In a database, a single foreign key can by used to represent a one-to-one relationship such as an individual's name being linked to a single customer ID in a database. Alternatively, a composite key comprised of a foreign key and a separate attribute can be used for one-to-many relationships such as a single customer's ID being linked to multiple orders with unique order numbers. Finally, a compound key of foreign keys can represent many-to-many relationships such as an inventory of items that can be optionally ordered by multiple customers (Geeks for Geeks, 2024b).

## References

BBC (n.d.) _[Design: Types of keys](https://www.bbc.co.uk/bitesize/guides/z4wf8xs/revision/4#:~:text=In%20a%20relational%20database%2C%20keys,and%20identify%20relationships%20between%20them.)_, BBC website, accessed 4 June 2024.

Geeks for Geeks (2024a) _[Relational Model in DBMS](https://www.geeksforgeeks.org/relational-model-in-dbms/)_, Geeks for Geeks website, accessed 4 June 2024.

Geeks for Geeks (2024b) _[Relationships in SQL - One-to-One, One-to-Many, Many-to-Many](https://www.geeksforgeeks.org/relationships-in-sql-one-to-one-one-to-many-many-to-many/)_, Geeks for Geeks website, accessed 4 June 2024.

Jatana, N., Puri, S., Ahuja, M., Kathuria, I., & Gosain, D. (2012). A Survey and Comparison of Relational and Non-Relational Database. _International journal of engineering research and technology_, 1.

Oracle (n.d.) _[What is a Relational Database (RDBMS)?](https://www.oracle.com/au/database/what-is-a-relational-database/)_, Oracle website, accessed 4 June 2024.

BBC (n.d.)

- keys enable rows to be uniquely identified or tables to be linked and related
- foreign keys allows the linking of tables
- surrogate key - an auto generated number to make a row unique
- composite key - the combination of two values to make a primary key
- compound key - two or more primary keys from different tables are foreign keys in a table that takes data from both

Geeks for Geeks (2024)

- a collection of tables to represent data and the relationships among the data, multiple columns, unique names, tables are relations, each table contains records of a particular type, fixed number of fields or attributes
- attribute, relation schema the structure of a table and the umbrella of attributes that make a table if more than one relation its a relational schema, tuple each row in a table is a tuple, degree the number of attributes in a table, cardinality the number of tuples in a relation, relation key the keys used to identify rows uniquely or linking tables, primary key the key that is distinct of a row, foreign key

Geeks for Geeks (2024b) _[Relationships in SQL - One-to-One, One-to-Many, Many-to-Many](https://www.geeksforgeeks.org/relationships-in-sql-one-to-one-one-to-many-many-to-many/)_, Geeks for Geeks website, accessed 4 June 2024.

Oracle (n.d.)

- in a relational database, each row in the table is a record with a unique ID called a key
- columns hold attributes of the daya
- different tables can be linked by a primary key, called a foreign key in the secondary table
- relational databases are structured so that the logical data structures (tables, views, indexes) are separate from physical storage structures, renaming a database does not rename the tables stored within it
- relational databases establish and follow integrity rules such as duplicate rows are not allowed
- the relational model is a standardised way to represent and query data, allows the use of SQL which is built upon relational algebra
- atomicity is the strict rulings that govern how data is allowed to be updated, a relational database won't commit changes until it is sure linked tables allow it
- ACID atomicity - all elements that make up a complete databse transaction, consistency - the rules for maintaining data points after a transaction, isolation keeps the effect of a transaction invisible until it is commited to avoid confusion, durability - changes are permanent
- relational databases allow stored procedures which are reusable blocks using an app call
- database locking prevents users from accessing data while it is being updated, different apps lock tables or rows

Jatana, N., Puri, S., Ahuja, M., Kathuria, I., & Gosain, D. (2012).

- database = application that allows storing and retrieving data rapidly
- a collection of data iitems organised in described tables that can be accessed or reassembled in different ways
- a set of tables with data in columns, rows contain unique instances of data set
- the database can be viewed in many ways
- benefits of a relational model database is the data is stored in the db rather than an app, easy to add update delete data because its centralised, the nature of the database is predictable
- shortcomings of relational database: they struggle to scale at a particular point because the database must be distributed, data can become highly complex, SQL can be complex, joining tables in distributed servers is difficult
- data can be cached
- eliminates record duplication and prevents inconsistent data from occupying the db

## Q10. Describe the integrity aspects of the relational database model. Your description should include information about the types of data integrity and how they can be enforced in a relational database. /6

The relational model is designed to ensure data integrity by featuring keys. Primary keys being mandated ensures that data is uniquely identifiable and also prevents a single instance of data from being entered multiple times (Levene and Loizou, 2001). By making each entry unique, data loss from disorganisation is reduced and users accessing or updating the data are ensured that they are not missing any stored information which can happen in non-relational data storage. Foreign keys also preserve integrity by maintaining relationships between different tables and attributes so that data is not lost.

At a database level, relational models are programmed with safeguards to ensure data remains trustworthy. Relational databases lock tables or rows data when it is being updated so that it cannot be queried whilst incomplete or incorrect. Similarly, relational databases make database changes permanent enforcing updates as definitive to ensure data is accurate when it is submitted (Oracle, n.d.). User roles, passwords and privileges can also be implemented to restrict data editing to qualified, trustworthy individuals too (Babenko et al., 2019). Restricting columns from allowing non-null values and accepting only specific data types is another simple measure to ensure that any entered and queried data is complete and, therefore, trustworthy (Levene, Loizou, 2001).

Using Postgres, the integrity measures of establishing a unique serial value as a primary key, requiring a column value and specifiying data types can executed as so:

``` Postgres
    CREATE TABLE example (id SERIAL PRIMARY KEY, name TEXT NOT NULL, age INT);
```

Once this table is generated, an attempt to seed the table without a name value or by inputting an age value as a text string will fail:

![Error messages from inapproriate data seeding into "example" table](/docs/postgres_integrity_eg1.png)

By extension, correct data entries will have a uniquely generated primary key in a column named "id" ensuring that similar entries are segregated:

![Distinct entries from similar data](/docs/postgres_integrity_eg2.png)

These measures, whilst simple, are fundamental to relational databases' integrity.

## References

Babenko, M., Schwiegelsohn, U., Talbi, E. & Tchernykh, A. (2019), 'Towards understanding uncertainty in cloud computing with risks of confidentiality, integrity, and availability'. _Journal of Computational Science_, vol. 36, DOI:[10.1016/j.jocs.2016.11.011](https://doi.org/10.1016/j.jocs.2016.11.011)

Levene, M. and Loizou, G. (2001) ‘A Generalisation of Entity and Referential Integrity in Relational Databases’, RAIRO - Theoretical Informatics and Applications, 35(2), pp. 113–127. DOI:10.1051/ita:2001111[https://doi.org/10.1051/ita:2001111].

Oracle (n.d.) _[What is a Relational Database (RDBMS)?](https://www.oracle.com/au/database/what-is-a-relational-database/)_, Oracle website, accessed 4 June 2024.

- entity and referential integrity are the most fundamental constraints
- primary key and referential integrity from the choice of foreign keys are the most fundamental constraints
- primary key's cannot be missing
- relational databases must not allow null values to ensure entity integrity, they should have default "surrogate" values alternatively such as 'value is unknown' or 'inapplicable'

Oracle (n.d.) _[What is a Relational Database (RDBMS)?](https://www.oracle.com/au/database/what-is-a-relational-database/)_, Oracle website, accessed 4 June 2024.

- in a relational database, each row in the table is a record with a unique ID called a key
- columns hold attributes of the daya
- different tables can be linked by a primary key, called a foreign key in the secondary table
- relational databases are structured so that the logical data structures (tables, views, indexes) are separate from physical storage structures, renaming a database does not rename the tables stored within it
- relational databases establish and follow integrity rules such as duplicate rows are not allowed
- the relational model is a standardised way to represent and query data, allows the use of SQL which is built upon relational algebra
- atomicity is the strict rulings that govern how data is allowed to be updated, a relational database won't commit changes until it is sure linked tables allow it
- ACID atomicity - all elements that make up a complete databse transaction, consistency - the rules for maintaining data points after a transaction, isolation keeps the effect of a transaction invisible until it is commited to avoid confusion, durability - changes are permanent
- relational databases allow stored procedures which are reusable blocks using an app call
- database locking prevents users from accessing data while it is being updated, different apps lock tables or rows

Babenko, M., Schwiegelsohn, U., Talbi, E. & Tchernykh, A. (2019), 'Towards understanding uncertainty in cloud computing with risks of confidentiality, integrity, and availability'. _Journal of Computational Science_, vol. 36, DOI:[10.1016/j.jocs.2016.11.011](https://doi.org/10.1016/j.jocs.2016.11.011)

- Confidentiality, Integrity and Availability (CIA)
- cloud increases security risks by shifting traditional models
- confidentiality is limited access to information
- integrity as the assurance that the information is trustworthy and accurate
- availability as a guarantee of reliable access to the information by authorised people
- data encryption, user identity documents (IDs), passwords, cards, retina scans, voice recognition and fingerprints, security tokens, key fobs
- availability can compromised by bottlenecks, redundancy, hardware failure, speed om retirm
- sharing resources with other virtual machines can slow, vms performance is unpredictable, physical hardware can slow vms even if a guaranteed speed is promised
- information security assumes defending information from unauthorized access, use, disclosure, disruption
- must consider accidental threats and failures
- these authors propose "accountability" to protect data by all users who process the data
- cryptographic protocol and error correction codes can reduce the risk
- accidental threats include user errors, carelesslness, curiosity
- check sums for monitoring obtained results
- challenges because resource scheduling is difficult when the resource is shared amongst unknown users
- data replication but is dangerous, secret sharing schemes (SSS) dealer distributes shares to recipients such that only authorised subsets of recipients can reconstruct the secret, can use homomorphic encryption which retains data encryption whilst it is encrypted public key to encrypt and corresponding private key can unlock but can have effects applied to it that maintains the relationship to the data computation can occur on ciphers which matches the result of operations performed on the original numbers,

## Q11. Describe the manipulative aspects of the relational database model. Your description should include information about the ways in which data is manipulated (added, removed, changed, and retrieved) in a relational database. /6

- detailed description, all common manipulative operations explained

- SQL code examples including joins

In the relational database model, data can be manipulated when entered, via updates and deletion as well as through queries. In PostgreSQL, these functions can be achieved by using SQL commands via an interface such as psql, a terminal-based front-end application (PostgreSQL Documentation, n.d.a).

Before data is entered, it can be manipulated upon entry by configuring the tables to alter it. Defining a data type will format the data to that type. For example, by defining "int" as a column's data type, it will be recorded as a number value rather than a string. Similarly, a column can be assigned a default value if it is not specified. This decision impacts how the data is recorded and how it can be queried. A table that manipulates data in this way could be coded like this:

```Postgres
CREATE TABLE shoes (
    id SERIAL,
    brand TEXT NOT NULL,
    style TEXT NOT NULL PRIMARY KEY,
    price DECIMAL DEFAULT 99.99
);
```

Data can then be seeded into a table using "INSERT INTO". Data entered must conform to the column rules.

```Postgres
INSERT INTO shoes 
    (brand, style)
    VALUES ('Nike', 'Air Jordan 4');
    <!-- With no assigned "price", the shoes will be assigned the default value of 99.99. -->
```

Tuples in table can be manipulated permanently using the "UPDATE" functionality. In this example, tuples where the "brand" and "style" attributs of "Nike" and "Air Jordan 4" respectively have their "price" value set to "199.99".

```Postgres
UPDATE shoes 
    SET price = 199.99
    WHERE brand = 'Nike'
    AND style = 'Air Jordan 4';
```

Data can be removed at a tuple level by using "DELETE FROM". Adhering to the relational database model, PostgreSQL will prevent a user from deleting a tuple that contains a foreign key for another table unless both tuples are deleted simultaneously. Entire columns or tables can be deleted using "DROP COLUMN" and "DROP TABLE" respectively. To preserve the tables and other schema but delete all tuple entries, "TRUNCATE" can be used (Postgres Documentation, n.d.b).

```Postgres
    TRUNCATE shoes;
```

Querying the data can also allow for powerful temporary manipulation. "SELECT" is used to target and return specific tuples based on defined critera known as clauses. The following returns the style and price of all shoes with brand value "Nike".

```Postgres
    SELECT style, price
    FROM shoes
    WHERE brand = 'Nike'
```

Tables linked via matching values such as foreign keys can also be temporarily joined by comining a "SELECT" statement with one of the "JOIN" keywords. The type of join defines how the tables are returned. "JOIN" defaults to "INNER JOIN" which only returns tuples where the clause condition is true. Alternatively, "LEFT JOIN", "RIGHT JOIN" and "FULL JOIN" allign rows where the clause conditions match but also return values that do not match in the temporary table. For example, if a second table created and seeded that uses the style of shoe as a foreign key, the following would combine the tables with the style listed first then the price, colour way name, primary colour and secondary colour values listed left to right.

```Postgres
SELECT colour_ways.style, price, colour_way_name, primary_colour, secondary_colour FROM colour_ways INNER JOIN shoes ON colour_ways.style = shoes.style;  
```

Returns this:

![The results using "INNER JOIN" as described above](/docs/postgres_inner_join_eg1.png)

These keywords and techniques allow users to manipulate data in powerful ways that maintain the relational database model.

## References

PostgreSQL Documentation (n.d.a) _[psql](https://www.postgresql.org/docs/current/app-psql.html)_, PostgreSQL website, accessed 5 June 2024.

PostgreSQL Documentation (n.d.b) _[Truncate](https://www.postgresql.org/docs/16/sql-truncate.html)_, PostgreSQL website, accessed 5 June 2024.

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
