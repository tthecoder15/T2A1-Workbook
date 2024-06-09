# Tom Tutone T2A1-A Workbook Part A

- Due 9.6.24 (2 weeks)

## Q1. Describe the architecture of a typical API project, such as a Flask application. /6

- detailed explanation of the architecture of an application, at least one example or reference with descriptions of main components of an application

- high level view, what are the components relationships and how do they work together

When creating an API, a web framework is an effective launching point as it provides tools and templates for routing and resource handling. Flask is a web framework written for Python that is database agnostic and lightweight. For this reason, Flask is quick to install and configure and allows developers to choose the rest of their stack piece by piece and install these extensions only when required keeping the sources codes file size down (MDN Web Docs n.d.). After choosing a web framework, a database software must be chosen. If PostgreSQL (Postgres) is chosen, Psycopg is an adapter that allows a Python application to interact with PostgreSQL databases. "psycopg2-binary" is a pip package that allows developers to connect the two with only minor configuration by providing a URI for the database that contains the user profile username and password to engage as when interacting with Postgres.

Once the database is connected, an Object Relational Mapper (ORM) allows a developer to generate SQL queries and objects in the application's language. SQLAlchemy provides a Python class that, once extended, contains tools to create models that mirror tables in a Postgres database. These models mirror the data formatting in the Postgres database and can be used, in the Python app, to generate correctly formatted SQL statements as well as return objects with row data from the Postgres database. SQLAlchemy is a useful ORM because it allows for varying data types, is database agnostic and can generate insert, update, delete or join statements (SQLAlchemy n.d.).

Whilst SQLAlchemy generated queries are formatted in familiar SQL syntax, the objects these queries return are not in easy to access Python objects. For this reason, an API will typically feature a data conversion package that transforms these objects into Python-native objects such as dictionaries. marshmallow is a popular data converter that can convert an SQLAlchemy object flexibly (marshmallow, n.d.). marshmallow requires a user to define a schema that mirrors the model object and contains fields that correlate to the columns in the table. After an SQLAlchemy object is returned, it can be passed to a marshmallow schema which converts selected fields into a Python dictionary.

In terms of security, flask_bcrypt is a package that can be istalled to hash and unhash data as it is sent and received from a database. Hashing data via bcrypt means that data can be stored in the Postgres database hashed and ineligible without conversion. A login route then be define which hashes the user's input and compares it to the hashed password to ensure they match without a user seeing the comparison. The next layer of security typically involves JWT tokens which can be generated in a Flask API using the flask_jwt_extended package. JWT tokens can be generated then returned to the user upon logging in. These JWT tokens can be generated with a defined lifecycle as well as embedded with a secret key. The secret key adds characters to the key which ensures that the token was generated via the application and was not altered in anyway before it was returned for authenication checks.

## References

marshmallow (n.d.) _[Why marshmallow?](https://marshmallow.readthedocs.io/en/latest/why.html)_, marshmallow Website, accessed 6 June 2024.

MDN Web Docs (n.d.) _[Explanation of a web framework](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Web_frameworks)_, MDN Web Docs website, accessed 31 May 2024.

Psycopg (n.d.) _[Psycopg 2.9.9 documentation: Installation](https://www.psycopg.org/docs/install.html)_, Psycopg Website, accessed 6 June 2024.

SQLAlchemy (n.d.) _[Features and Philosophy](https://www.sqlalchemy.org/features.html)_, SQLAlchemy Website, accessed 6 June 2024.

### Notes from references

Psycopg (n.d.) _[Psycopg 2.9.9 documentation: Installation](https://www.psycopg.org/docs/install.html)_, Psycopg Website, accessed 6 June 2024.

- most popular postgreSQL database adapter for python
- psycopg2-binary package

marshmallow (n.d.) _[Why marshmallow?](https://marshmallow.readthedocs.io/en/latest/why.html)_, marshmallow Website, accessed 6 June 2024.

- converts complex datatypes to and from native Python datatypes
- can convert SQLAlchemy objects to Python dicts
- database agnostic
- uses classes which are easy to reuse, can easily control which data is converted into a dict, can choose which will be converted and which won't

SQLAlchemy (n.d.) _[Features and Philosophy](https://www.sqlalchemy.org/features.html)_, SQLAlchemy Website, accessed 6 June 2024.

- Core allows SQL statements to be generated using python expresions
- ORM allows for user-defined classes that align witht the table to write or query
- allows for booleans, operators, functions, table aliases, selectable subqueries, insert/update/delete statements and joins among other features
- SQLAlchemy is non-opinionated doesn't generate default shcemas
- ORM

MDN Web Docs (n.d.) _[Explanation of a web framework](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Web_frameworks)_, MDN Web Docs website, accessed 31 May 2024.

- routing (Flask), Object-Relational Mapper (ORM) database layer that abstracts database read, write, query and delete operations (Django provides one, SQLAlchemy is an alternative), generating HTML?

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

- overview is correct, supported by more than one valid and relevant relevant code example with a high level of detail

When initialising an API, confidentiality, integrity and availability must be guiding influences on how the API stores, returns and protects data. Because all three principles are connected, different, simple measures can bolster an API's ability to make strides in all three.

Enforcing authentication and limiting authorisation is a principle measure that increases an APIs confidentiality and integrity. APIs are designed for to be accessed in varying user contexts such as a factory worker needing access to customer's name and address to create a postage label versus a marketing worker requiring the same customer's name and email address for promotional material. In contexts such as these, it would increase data confidentiality to only allow access to appropriate column data by each deparment. This can be enforced by creating unique user accounts per worker and granting distinct privileges to those users. Similarly, only certain workers should be allowed to alter tuple data to maintain database integrity. These systems can be set-up by creating log in routes that post a log in attempt to the API. The log in credentials can be checked against a hashed password storage to allow or block log in. When the worker logs in, they could be granted a JWT that is inspected on each request. Notably, it is important to implement session management and pass tokens with appropriate expiry times (Worksoft Corporate Blog, n.d.). This ensures that a user's session cannot be hijacked when they leave a workstation or lose a device. Below is an example of checking a user's login attempt using Flask with the flask_jwt_extended, sqlalchemy, marshmallow and flask-bcrypt packages with a set expiry time:

```Python
@app.route("/workers/login", methods=["POST"])
def login():
    params = UserSchema(only=["id", "password"]).load(
        request.json, unknown="exclude"
    )
    # creates a Python object with key pairs from the user's passed "id" and "password" using a defined marshmallow model schema
    stmt = db.select(User).where(User.id == params["id"])
    # creates an SQL query using a User model defined using SQLAlchemy that matches a database's table schema. Specifically requests the row where the "id" value matches the users input for "id"
    user = db.session.scalar(stmt)
    # assigns a local variable the returned object from the query or none if a user with the input "id" does not exist  
    if user and bcrypt.check_password_hash(user.password, params["password"]):
    # uses bcrypt to decode the stored hashed password in the database assigned to the input "id", compares it to the input password value
        token = create_access_token(identity=user.id, expires_delta=timedelta(minutes=30))
    # if the passwords match, a JWT is created with an expiration date of 30 minutes. This JWT confirms that the user logged in via the appropriate method and can be checked when requesting certain routes to confirm the user has appropriate authentication to access those resources
        return {"token": token}
    else:
        return {"error": "Invalid email or password"}, 401
    # if the user's input id or password are incorrect, they are returned a HTTP error code 401
```

Another way to improve ensure confidentiality is to never pass a user's data via urls (Amazon Web Services, 2024). If user's log in attempt or other private data is passed as a variable in a URL rather than in the body, the data would be accessible and obtainable from that user's browser history.

To improve an API's accessibility, it is vital to structure the API so that it is RESTful. Resource access and requests URLs need to be structured in a predictable way and semantic way that they describes the data branches they are accessing. Routing resources in a "collective noun/individual" instance structure such as "biographies/bio1" helps user's access data easily and logically.

## References

Amazon Web Services. (2024) _[Data protection in Amazon API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/data-protection.html)_, AWS website, accessed 7 June 2024.

Worksoft Corporate Blog. (n.d.) _[Data protection in Amazon API Gateway](https://www.worksoft.com/corporate-blog/api-security-testing-ensuring-the-integrity-and-confidentiality-of-your-apis)_, Worksoft website, accessed 7 June 2024.

## Q8. Explain the legal obligations that developers of a social media website or social media application would have in regards to handling user data, with reference to any applicable laws or acts. /12

- more than one legal obligation relevant to handling user data explained in high amounts of detail including relevant references to support the explanation

Social media websites and applications inherently require data of varying scopes to be stored. From email addresses, to names and optional personifiers such as date of birth, location data and images, social media companies request a lot of data but also receive a lot voluntarily. These companies must implement security practices to uphold confidentiality, integrity and availability of data and they must do so in a way that follows domestic as well as international laws. These laws specify how data can be stored and used as well as what constitutes a failure from the company's practices.

In Australia, data privacy regulations are derived from the Australian Privacy Act from 1988 as well as the thirteen Australian Privacy Principles which, together, dictate guidelines and rules for businesses to adhere to when storing user data (Australian Government Office of the Australian Information Commissioner, n.d.). The privacy principles outline data-based interactions and mandate that companies must be transparent in their storage policies, clarify when data is being stored and obtain consent when doing so, communicate with customers when their information is being shared with third-parties as well as allowing users to know what data is stored about them and give them the opportunity to correct any errors (principles 1, 5, 6, 12 and 13). Principles 2, 3, 4 and 7 outline that companies must offer individuals the ability to use their services without their data being stored or through using a pseudonym, not store particular data including race or union affiliation, destroy or de-identify irrelevant data and follow a set of rules when using direct marketing. Finally, principles 8, 9, 10 and 11 outline security procedures for sending data internationally, the restriction of releasing government ID data, how companies must reasonably attempt to keep data up to date and, vitally, that companies must implement protect data from unauthorised access. Notably, the Australian government is currently in the process of updating these laws and regulations to include stricter guidelines about depersonalising and destroying data after certain time periods and granting users the ability to oppose the storage of their data (Australian Government Attorney-General's Department, 2023).

In addition to Australian laws, an Australian-based social media company must consider foreign laws that apply to any international users that the company may acquire. The GDPR (General Data Protection Regulation) is a collection of regulations that enforce how EU residents' data may be collected and stored. Importantly, the GDPR applies to foreign businesses that offer goods or services or store behaviour data about individuals living in the EU including cookies (Wolford, B., n.d.). Whilst many GDPR regulations are mirrored by the Australian Privacy Act, there are notable instances where the GDPR has much stricter and more explicit requirements (Australian Government Office of the Australian Information Commissioner, 2018). Unlike Australian laws, data privacy laws apply to all scales of businesses, require all businesses to complete a compulsory data protection assessment and employ an appointed data protection officer. The regulation also features "right to erasure", a "right to data portability" and a "right to object" which gives individuals the means to have their data deleted upon request, receive stored data about them in a conventional and reasonable data format and the ability to challenge the storage of their data. It is vital that any social media consider security laws that can be enforced on behalf of foreign users.

Considering the widespread laws relating to data privacy, it is essential that a social media company creates a thorough plan for how it will handle user data. At a fundamental level, data must be stored in a way that protects individual privacy and companies should take measures to de-personalise, securely store or, simply, not store personal data where appropriate. It is also crucial that a social media company has an individual professionally responsible for the company's policies who understands the laws that affect the company. Because users must be able to access, alter or, as per the GDPR's "right to be forgotten", delete archived data, companies must develop techniques that easily allow these actions. Finally, data storage constent is a particularly prominent focus of the GDPR and Australian laws and companies must be deliberate in communicating users these options. In 2023, the GDPR issued Tik Tok, a predominately foreign company, a €345 million fine for presenting teenage users misleading consent options between July 2020 and December 2020. During this time, the app presented subtle and hard to comprehend optionality for making a user's account and videos private (EDPB, 2023). With such rulings as well as an imminent increase to Australian laws, a social media company must err on the side of communication in its data privacy practices and transparency with users.

### References

Australian Government Attorney-General's Department, (2023), _[Privacy Act Review Report](https://www.ag.gov.au/rights-and-protections/publications/privacy-act-review-report)_, Australian Government website, accessed 8 June 2024.

Australian Government Office of the Australian Information Commissioner, (2018), _[Australian entities and the European Union General Data Protection Regulation](https://www.oaic.gov.au/privacy/privacy-guidance-for-organisations-and-government-agencies/more-guidance/australian-entities-and-the-european-union-general-data-protection-regulation)_, Australian Government website, accessed 8 June 2024.

Australian Government Office of the Australian Information Commissioner, (n.d.), _[Australian Privacy Principles quick reference](https://www.oaic.gov.au/privacy/australian-privacy-principles/australian-privacy-principles-quick-reference)_, Australian Government website, accessed 8 June 2024.

EDPB (2023), _[Following EDPB Decision, TikTok ordered to eliminate unfair design practices concerning children](https://www.edpb.europa.eu/news/news/2023/following-edpb-decision-tiktok-ordered-eliminate-unfair-design-practices-concerning_en)_, GDPR website, accessed 9 June 2024.

Wolford, B. (n.d.), _[Does the GDPR apply to companies outside of the EU?](https://gdpr.eu/companies-outside-of-europe/)_, GDPR website, accessed 8 June 2024.

Australian Government Office of the Australian Information Commissioner, (2018), _[Australian entities and the European Union General Data Protection Regulation](https://www.oaic.gov.au/privacy/privacy-guidance-for-organisations-and-government-agencies/more-guidance/australian-entities-and-the-european-union-general-data-protection-regulation)_, Australian Government website, accessed 8 June 2024.

- businesses may need to comply with the GDPR if they offer goods and services in the EU
- data breach notification (GDPR and privacy act)
- processng activities of business regardless of size - controler says how data is processed, processor acts on behalf of thhe controller, process
- Aus businesses affected: Aus businesses with an office in EU, webbsite targets EU customers enabling them to order goods or services in a Euro language or enabling euro payment, business mentions customers or users in the EU, business that tracks EU individuals using data processing/profiling
- personal data: racial origin, political opinions, religious beliefs, trade union membership, genetic data, biometric dayas, health or sex life data
- must comply with Article 5 of the GDPR 'Principles relating to the processing of personal data'
- Article 24 ensure data protection policies comply with these
- Article 5 - data protection by design and by default
- minimise personal data storage, pseudonymising personal data, transparency to functions and processing, individual may monitor processing
- controllers and processes must in certain circumstances appoint a data protection officer to monitor and advise compliance with GDPR with internal policies and procedures
- controllers must undertake a compulsory data protection impact assessment prior to high risk data processing article 35 outlines high risk
- controllers must keep records of processing activities article 30
- consent of data choice means user can with draw consent, must be as easy as giving consent article 7
- individuals below 16 must get parental responsibility approve consent article 8
- 72 hours to notify data breach article 33
- "right to be forgotten" article 17, individuals have a rioght that data controllers must delete their data where the information is no longer neccessary or the individual withdraws constent
- right to portability - individual must be able to receive the data in a structured, commonly user, machine-readable format
- GDPR can impose admin fines for up to 20 mill euros or 4 percent of ww turnover
- monitoring the behaviour of individuals in the EU is the big one for aussies

Wolford, B. (n.d.), _[Does the GDPR apply to companies outside of the EU?](https://gdpr.eu/companies-outside-of-europe/)_, GDPR website, accessed 8 June 2024.

- article 3 - territorial scope of the law - regardless if the processing takes place in the union or not
- offering goods or services irrespective of whether a payment is required, monitoring eu behaviour within the union
- if you cater to the EU - foreign language ads, random instances do not qualify you
- cookies, ip addresses, GDPR applies

Australian Government Attorney-General's Department, (2023), _[Privacy Act Review Report](https://www.ag.gov.au/rights-and-protections/publications/privacy-act-review-report)_, Australian Government website, accessed 8 June 2024.

- government accepted proposals to alter the privacy act
- proposed reforms to strengthen data privacy laws
- including small businesses in more laws which they are presently exempt from less than 3 mill revenue
- proposed to create new OAIC guidelines about destroying or depersonalising inappropriat epersonal data, review the length of time data is stored
- proposes individual rights modelled on the GDPR such as the right to object, request erasure and have search results de-indexed
- increased enforcement capabilities, civil penalties, individuals being able to seek remedies for breaches of the act that cause harm

Australian Government Office of the Australian Information Commissioner, (n.d.), _[Australian Privacy Principles quick reference](https://www.oaic.gov.au/privacy/australian-privacy-principles/australian-privacy-principles-quick-reference)_, Australian Government website, accessed 8 June 2024.

- a collection of the privacy principles that govern standards rights and oblications of data storage and individual rights
- 1: open and transparent management of personal informaiton
- 2: individuals must give individuals the option of not identifying themselves or using a pseudonym with limited exceptions
- 3: collection of solicited personal information is limited such as race or union membership
- 4: collection of unsolicited personal data, entities must destroy or de-identify data or handle it in accordance with more rules such as finanical records being atteched without being required
- 5: must notify users when an entity is collecting personal data
- 6: user must consent to secondary user or disclosure, user may reasonably expect the user to be related to the primary purpose
- 7: direct marketing must follow particular rules
- 8: must take steps to protect personal information before overseas disclosure
- 9: cannot release users Medicare numbers, centrelink reference numbers, passport numbers etc
- 10: must take reasonable steps to ensure personal data is accurate and up to date
- 11: protect data from loss unauthorised access
- 12: users must be able to access what information is stored on them
- 13: must take reasonable steps to correct personal information that is misleading

EDPB (2023), _[Following EDPB Decision, TikTok ordered to eliminate unfair design practices concerning children](https://www.edpb.europa.eu/news/news/2023/following-edpb-decision-tiktok-ordered-eliminate-unfair-design-practices-concerning_en)_, GDPR website, accessed 9 June 2024.

- Tik Tok data processing between July and December 2020
- unfair pop-up notifications shown to children 13-17 with a "skip" pop-up when making accounts which defaulted to public
- "Post Now" was presented in bold next to a lighter "cancel" which was required look for privacy settings to make account private, 'public-by-default'
- assessed a €345 million pound fine

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

### A. List and describe the software (tech stack) used by the app

- detailed description of the software, multiple references to support the description

Pinterest is a web application that allows users to keyword search for images to "pin" on user-created "pinboards" that collate images in particular orders. These images are uploaded to Pinterest by companies or individuals and they are displayed with a title, the user who uploaded them and they can link to external websites such as blogs or online stores (Pinterest Help, n.d.). User's boards are typically used for creative inspiration and the site functions largely like a social media app (Pinterest Business, n.d.). Notably, Pinterest was famously able to achieve a massive user base with a simple, but scalable, tech stack (Engineer's Codex, 2023). As the app has grown, it has incorporated varying tools, libraries and software that allow it to achieve increased functionality such as suggestive ad serving and user interaction tracking however its core functionality is built upon the pinboard functionality (The Technology Vault, n.d., ).

Python is the predominant coding language used for Pinterest's backend and data processing and it is used in conjunction with Django. Django is an web framework that features routing, user authentication as well as ORM tools to generate database interactions. For its databases, Pinterest uses MySQL, an an open-source relational database and alternative to PostgreSQL. For the front-end, Pinterest uses React which is a Javascript library containing tools to build interactive HTML webpages and mobile apps. To improve the efficiency of server requests, Pinterest leverages NGINX, an open-source web-server and reverse proxy. NGINX operates between user requests and a company's servers to execute requests in an optimised way by distributing traffic to less-strained resources and caching results among other measures. Pinterest utilises both Redis and Memcached for data caching. Each software has its strengths and Memcached is optimised for storing and returning key-value pairs quickly whilst Redit is utilised for storing complex data structures (Amazone Web Services, n.d.).

## References

Amazon Web Services (n.d.) _[Comparing Redis and Memacached](https://aws.amazon.com/elasticache/redis-vs-memcached/)_, Amazon Web Services website, accessed 9 June 2024.

Engineer's Codex (2023) _[How Pinterest scaled to 11 million users with only 6 engineers](https://read.engineerscodex.com/p/how-pinterest-scaled-to-11-million)_, Engineer's Codex website, accessed 9 June 2024.

Pinterest Business (n.d.) _[How Pinterest Works](https://business.pinterest.com/en-au/how-pinterest-works/)_, Pinterest Business website, accessed 9 June 2024.

Pinterest Help (n.d.) _[All about Pinterest](https://help.pinterest.com/en/guide/all-about-pinterest)_, Pinterest Help Center website, accessed 9 June 2024.

StackShare (n.d.) _[Stack History: A Timeline of Pinterest's Tech Stack Evolution](https://stackshare.io/stack-history-timeline-pinterest-tech-stack-evolution)_, StackShare website, accessed 9 June 2024.

The Technology Vault (n.d.) _[Pinterest Tech Stack](https://thetechnologyvault.com/pinterest-tech-stack)_, The Technology Vault.com website, accessed 9 June 2024.

### B. Describe or make educated guesses about the hardware used to host the app

- Pinterest hosts data on Amazon S3, a cloud stoage service. It also uses Amazon EC2 for cloud computing

- detailed description, multiple references to support the description

- how much CPU would it need and network bandwidth

Pinterest uses Amazon services to host its databases as well as to execute cloud computing. Amazon S3 is a storage service that offers specific storage options for more or less frequently accessed data. Pinterest has publicly described how it uses different S3 storage classes including the S3 Glacier Flexible Retrieval and S3 Glacier Deep Archive services for less used, archival storage such as data from years ago (Yin et al., 2021). It also uses, non-specified, faster web S3 services such as the S3 Standard which is optimised for frequently accessed data (Amazon Web Services, n.d.). S3 are cloud databases that store data in key pairs in storage centres located around the world. Specific Amazon hardware is a trade secret but it is reasonable to assume their data centers feature advanced proprietary servers with solid-state hardware. Pinterest also uses Amazon's EC2 services which provide virtual servers for running cloud processing (Amazon Elastic Compute Cloud, 2024). These services can communicate at bandwith's of up to 100GBs (Amazon Knowledge Center, 2023). With more than 440 million users and being a prominent user of Amazon Web Services, it is safe to assume that Pinterest accesses Amazon's fastest services (Yin et al., 2021). It is worth noting that, in 2015, Pinterest had 10 petabytes of data stored in S3 (Weiner) and so, with millions more users and 9 more years of archived data, it is clear that Pinterest is hosted by very, very significant hardware.

## References

Amazon Elastic Compute Cloud (2024) _[What is Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)_, Amazon Web Services Website, accessed 9 June 2024.

Amazon Knowledge Center (2023) _[What's the maximum transfer speed between Amazon EC2 and Amazon S3?](https://repost.aws/knowledge-center/s3-maximum-transfer-speed-ec2)_, Amazon re:Post Website, accessed 9 June 2024.

Amazon Web Services (n.d.) _[Amazon S3 FAQs](https://aws.amazon.com/s3/faqs/)_, Amazon Web Services Website, accessed 9 June 2024.

Weiner, M. (2014) _[Powering big data at Pinterest](https://medium.com/pinterest-engineering/powering-big-data-at-pinterest-3c4836e2b112)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

Yin, Y., Yang, B., Kou, X. (2021) _[How Pinterest uses Amazon S3 Glacier Deep Archive to manage storage for its visual discovery engine](https://aws.amazon.com/blogs/storage/how-pinterest-uses-amazon-s3-glacier-deep-archive-to-manage-storage-for-its-visual-discovery-engine/)_, Amazon Storage Blog website, accessed 9 June 2024.

### C. Describe the interaction of technologies within the app

- detailed description, identifies the roles and purposes of all technologies described

- can make educated guesses as well

- one thing assessed is logical deductions if data isn't explained

To consider how the different software in Pinterest's stack interact, it is helpful to start at the front end. Pinterest began using ReactJS for its webpage rendering in 2015 and have described how their data flow works when a user makes a request (Chan, 2016). When a user requests a Pinterest webpage, the request first passes through an Nginx proxy layer that sends the request to Pinterest's servers in an efficient way. Once received by Pinterest servers, the servers use React and Node to begin compiling the document to be returned. This involves making requests to Pinterest's different data APIs to return data that will populate the page such as images (Semah, 2022). These APIs are coded using Django and the data requests follow the appropriate routes to access the neccessary data. These routes generate SQL statements to query Pinterest's databases. Notably, the databases may be queried directly, but it is likely that data cached via Redis and Memcached's alogrithms can be returned without passing requests to the MySQL databases directly. The requested data is then returned to React which inserts it to complete the HTML document which, once finished is returned to the user and rendered in their browser.

## References

Chan (2016) _[How we switched our template rendering engine to React](https://medium.com/pinterest-engineering/how-we-switched-our-template-rendering-engine-to-react-a799a3d540b0)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

Semah, B. (2022) _[What Exactly is Node.js? Explained for Beginners](https://www.freecodecamp.org/news/what-is-node-js/)_, freeCodeAcademy Website, accessed 9 June 2024.

### D. Describe the way data is structured within the app’s database(s)

- detailed understanding of the data structure and includes an example or reference about why the database structure was chosen for the real world application

- more of a high level assessment

Pinterest stores its data using MySQL databases. Notably, they have adopted this structure for its effectiveness and popularity. Pinterest engineer Weiner (2014a) explains that MySQL is used by the company for its maturity and scalability. As a company that requires extensive, and increasing, database queries, MySQL is an effective database that has proven its effectiveness through extended popularity. In addition, Weiner celebrates the breadth of knowledge about and developed features of MySQL.

Notably, the prominence of image data in Pinterest means that the application generates extemely large database files. Because of this, their data could not be stored on finite databases or single locations. In anticipation of increased data storage and to improve API performance, Pinterest implemented database sharding that segregated and divided their MySQL databases across servers (Weiner, 2014b). Notably, this process restricts the APIs from using joins or foreign keys to link data that is stored on separate servers, a significant decision. Sharding requires significant restructuring of the ways that data is accessed and the information contained in a tuple. To ensure data is trackable within a sharded system, Pinterest records tuples information about which shard their master is stored in and madates that data should not be moved or saved in different shards once it is reocrded. To overcome the inability to join tables, Pinterest uses mapping tables that consider the shard values to access data from different shards which are then joined at the application layer.

Whilst Pinterest's database systems are unconventional, they are appropriate for their data-intensive storage requirements.

## References

Weiner, M. (2015a) _[Powering big data at Pinterest](https://medium.com/pinterest-engineering/powering-big-data-at-pinterest-3c4836e2b112)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

Weiner, M. (2015b) _[Sharding Pinterest: How we scaled our MySQL fleet](https://medium.com/pinterest-engineering/sharding-pinterest-how-we-scaled-our-mysql-fleet-3f341e96ca6f)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

### E. Identify the entities/tables that are tracked within the app’s database(s)

- identifies all significant entities including additional entities required to optimise or normalise the db structure

- if the user can do this, then the database MUST store, front-end informing guesses to make it work

Weiner (2015) outlines key tables that are stored in the Pinterest databases: Pins, users, boards and comments. Considering how the user can interact with these features, it is reasonable to assume the tables have the following attributes:

Pins: "description, "link", "user_id", "board_id", "pin_id", "shard_id", "date_pinned"
Users: "email", "password", "id", "shard_id", "boards"
Boards: "id", "board_title", "user_id", "shard_id", "has_pins", "pin_sequence", "date_created", "visibility"
Comments: "id", "user_id", "pin_id", "shard_id", "content", "date_created", "edited"

## References

Weiner, M. (2015) _[Sharding Pinterest: How we scaled our MySQL fleet](https://medium.com/pinterest-engineering/sharding-pinterest-how-we-scaled-our-mysql-fleet-3f341e96ca6f)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

### F. Identify the relationships and associations between the entities/tables identified in sub-question E

- identifies ALL relationships/associations in a sophisticated relational model

Users has a one to many relationship with pins, boards and comments. Pins, boards and comments would each use user ID as a foreign key to contribute to their primary keys. Pins are linked to boards via "board_id", a foreign key that uses a board's ID to link individual pins to a board. A board must also preserve values to sequence the pins linked to it in a "pin_sequence" value. This would update as the user adds pins and rearranges them. Boards have a one to many relationship with pins. Users can also comment on pins unlimited times so a comment's primary key would be a compound key from the pin ID that it was posted on, the user ID who commented it and a comment ID to differentiate it from a user's other comments on the same pin.

### G. Design an entity relationship diagram (ERD) based on the answers provided to sub-questions 5 and 6. This must represent a relational database model, even if the app itself uses something other than a relational database model

- a normalised ERD (without data duplication) that facilitates full functionality of the app

![Pinterest ERD](/docs/Pinterest-ERD-v1.0.png)

## References

PostgreSQL Documentation (n.d.a) _[psql](https://www.postgresql.org/docs/current/app-psql.html)_, PostgreSQL website, accessed 5 June 2024.
