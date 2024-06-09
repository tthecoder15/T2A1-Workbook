# Tom Tutone T2A1-A Workbook Part A

## Q1. Describe the architecture of a typical API project, such as a Flask application. /6

When creating an API, a web framework is an effective launching point as it provides tools and templates for routing and resource handling. Flask is a web framework written for Python that is database agnostic and lightweight. For this reason, Flask is quick to install and configure and allows developers to choose the rest of their stack piece by piece and install these extensions only when required keeping source codes file size down (MDN Web Docs n.d.). After choosing a web framework, a database software must be chosen. If PostgreSQL (Postgres) is chosen, Psycopg is an adapter that allows a Python application to interact with PostgreSQL databases. "psycopg2-binary" is a pip package that allows developers to connect the two with only minor configuration by providing a URI for the database that contains the user profile username and password to engage as when interacting with Postgres.

Once the database is connected, an Object Relational Mapper (ORM) allows a developer to generate SQL queries and objects in the application's language. SQLAlchemy provides a Python class that, once extended, contains tools to create models that mirror tables in a Postgres database. These models can be used, in the Python app, to generate correctly formatted SQL statements as well as return objects with row data from the Postgres database. SQLAlchemy is a useful ORM because it allows for varying data types, is database agnostic and can generate insert, update, delete or join statements (SQLAlchemy n.d.).

The objects these queries return are not formatted in easy-to-access objects however. For this reason, an API will typically feature a data conversion package that transforms these objects into Python-native objects such as dictionaries. marshmallow is a popular data converter that can convert an SQLAlchemy object flexibly (marshmallow, n.d.). marshmallow requires a user to define a schema that mirrors the model object and contains fields that correlate to the columns in the table. After an SQLAlchemy object is returned, it is passed to the marshmallow schema which converts selected fields into a Python dictionary.

In terms of security, flask_bcrypt is a package that can be installed to hash and unhash data as it is sent and received from a database. A login route can then be defined which hashes the user's input and compares it to the hashed password to ensure they match without a user seeing the comparison. The next layer of security typically involves JWT tokens which can be generated in a Flask API using the flask_jwt_extended package. JWT tokens are generated then returned to the user upon logging in. These JWT tokens have a defined lifecycle and are embedded with a secret key. The secret key adds specific characters to the key which ensures that the token was generated via the application and was not altered in anyway before it was returned for authentication checks.

### References

marshmallow (n.d.) _[Why marshmallow?](https://marshmallow.readthedocs.io/en/latest/why.html)_, marshmallow Website, accessed 6 June 2024.

MDN Web Docs (n.d.) _[Explanation of a web framework](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Web_frameworks)_, MDN Web Docs website, accessed 31 May 2024.

Psycopg (n.d.) _[Psycopg 2.9.9 documentation: Installation](https://www.psycopg.org/docs/install.html)_, Psycopg Website, accessed 6 June 2024.

SQLAlchemy (n.d.) _[Features and Philosophy](https://www.sqlalchemy.org/features.html)_, SQLAlchemy Website, accessed 6 June 2024.

## Q2. Identify a database commonly used in an API project (such as a Flask application) and discuss the pros and cons of this database. /6

When initialising an API, there is a variety of paid and open-source software that can for the application's database. These include choices of relational and non-relational databases. Two of the most popular open source databases are the relational databases PostgreSQL (Postgres) and MySQL. Both use SQL to interact with stored data and each has benefits in how they are designed. A key feature of Postgres is its default robustness, installing with many features which do not need to be added with additional modules like in MySQL. Postgres has MVCC (multiversion concurrency control) built into it which is a key benefit in many usage contexts. MVCC configures Postgres to access recent snapshots of data rather than access the live data. This means that tuples or tables are not locked when they are being accessed, either queried or written to, so that multiple transactions can place concurrently (PostgreSQL Documentation, n.d.). This is beneficial in many API contexts where data could be required by two or more systems at once. Postgres is also ACID (Atomicity, Consistency, Isolation, Durability) compliant so that errors will not corrupt data (Amazon Web Services, 2024). Another benefit of Postgres is that it allows for parent-child relationships and inheritance without installing additional packages. These are some of the distinct advantages of Postgres over its competitors.

In terms of negatives, a key consideration when choosing Postgres versus an alternative is a higher overhead cost to initialise and utilise Postgres (Amazon Web Services, 2024 & Hanlon et al., 2011). Because Postgres is strict when inputting data, formatting schema and seeding data, users must be experienced in how the system works to use it effectively. In addition, tuples cannot be seeded unless they completely align with the data structure of the tables they are being inserted into meaning that data will often have to be screened or edited before it can be saved. This is a negative in more dynamic data storage environments where saving results is the first priority. This, again, becomes a problem when migrating data from an old or different system to be stored in Postgres (Hanlon et al., 2011). Postgres is also resource intensive and returns read queries slower than MySQL or alternative, non-relational databases such as CouchDB (Amazon Web Services, 2024 & Hanlon et al., 2011).

In totality, Postgres' strictness and robustness is a signature strength of the database but also causes some drawbacks. It is important to consider the frequency and types of requests an API will receive when choosing a database for it.

### References

Amazon Web Services (2024) _[What is SQL?](https://aws.amazon.com/what-is/sql/)_, AWS website, accessed 24 May 2024.

Hanlon, M., Dooley, R., Mock, S., Dahan, M., Nuthulapati, P. & Hurley, P. (2011). _Benefits of NoSQL databases for portals & science gateways_. DOI:[10.1145/2016741.2016780](https://doi.org/10.1145/2016741.2016780).

PostgreSQL Documentation (n.d.) _[13.1 Introduction: Chapter 13 Concurrency Control](https://www.postgresql.org/docs/16/mvcc-intro.html)_, PostgreSQL website, accessed 6 June 2024.

## Q3. Discuss an implementation of an Agile project management methodology for an API project. /6

Agile project management is a collection of techniques used to break down the steps required to achieve a large goal or collection of goals. Broadly, agile projects begin with a team describing the steps necessary to reach a goal, estimating the resources needed to achieve these sub-goals including time and personnel distribution, deciding which goals are most urgent, dividing the responsibilities amongst team members and constantly evaluating how each sub-goal is tracking (Moe, et. all, 2014). With these calculations, the team schedules iterations which are deadlines for an outcome to be achieved by. In agile planning, a project manager is an active participant in the work who must be able to provide expert feedback on work and help solve problems (Fernandez & Fernandez, 2008). However, agile methods also prioritise giving team members autonomy in their own time management and objectives. Agile projects also schedule feature regular face-to-face feedback loops where team members check-in on each other's work, share their progress and difficulties and reflect upon their processes to identify what is working and what needs altering moving forwards. Finally, a typical feature of agile projects is a kanban board where team members write sub-goals on sticky notes and track their progress by moving them into sections such as "to do", "in progress", "need help", "review" and "finished". The kanban board is updated as team members reach challenges or during feedback sessions (Moe, et. all, 2014).

Utilising agile project management to create an API would require a team to first break down the process into features and components. For an API this would include API infrastructure and the decision of what software and modules will be used, database initialising and seeding, routing, database interaction functions from the app such as adding data, testing of the app, testing of the database and standardising data returns. The highest priority task would be to decide upon the API infrastructure and which software will be used. In an agile project, it would likely be beneficial if all team members have a chance to weigh-in on the tech stack. After this is decided, the team would estimate how long each task would take and create a kanban board to monitor progress. The project manager would lead the team in defining iterations and deadlines for the team to achieve. These deadlines would prioritise the objectives which are necessary for other sub-goals including the database initialisation which needs to be completed so that the routing can connect to it. With the kanban board created and iterations defined, the team members would divide the work amongst themselves, with input from the project manager. The project manager would also schedule regular check-ins so that the team members can update eachother on their progress and voice challenges. As the team members meet, challenges would be shared and the team could continually adjust its goals, potentially changing their responsibilities or collaborating on specific tasks if they are overwhelming an individual. In addition, the project manager would continually evaluate the relevance of each feature and consider adding or removing any features.

### References

Brede Moe, N., Dingsøyr, T., Dyba, T. (2014) 'Agile Project Management', in Ruhe, G., Wohlin, C. (eds.) _Software Project Management in a Changing World_. Berlin: Springer-Verlag, pp. 277-300.

Fernandez, D. J. and Fernandez, J. D. (2008) ‘Agile Project Management —Agilism versus Traditional Approaches’, Journal of Computer Information Systems, 49(2), pp. 10–17. doi: 10.1080/08874417.2009.11646044.

## Q4. Provide an overview and description of a standard source control process for an API project. /6

When initialising an API, it is vital that a source control strategy is designed and implemented because, eventually, clients and other applications will significantly depend on an API functioning in a predictable way. With this context in mind, it is standard for an API's source control process to be structured in a way that preserves the API's initial RESTful state on a main branch. Typically, any subsequent new features should be developed on forks of the main branch, with each fork representing a user story and use case (ozanseymen, 2016). These forks can be hosted in the main repository so that other developers can contribute to them also. It is imperative that these forks are continually merged with the main branch, as frequently as daily, so that they do not diverge from the released API's code and become redundant. Forking into separate branches per story allows for powerful source control as updates can be released only once they are safe to deploy and it also allows developers to share work internally and work on features that depend on yet-to-be released features as well. Importantly, forks should not be merged to the main branch until they have been reviewed and tested extensively by a multiple individuals to prevent breaking the API.

In an API context, source control management often encapsulates versioning. Versioning is strategising that ensures an API preserves its RESTful quality and allows users to predictably interact with it as updates are added (Kleier, 2020). APIs depend on stable data contracts between clients and servers and any updates to APIs should eliminate or minimise changing these contracts, particularly without warning. When updating an API, changing a property name, response format or deleting an attribute can all break a user's application. Considering the sweeping impacts of these simple changes, an API's source control must segregate these alterations from the main branch and these types of changes should be considered when approving whether a fork is merged to the main branch. Alternatively, if breaking changes must be made, the API can be versioned in a way that preserves the main branch and the routing that any clients use. An API can be versioned by altering the routing conventions for new versions of the API such as "v2/users/<id>" or incorporating query parameters such as "api/tools?version=3" that developers can use when engaging the API (Kleier, 2020). In this instance, the source control must consider these conventions by preserving the original main branch and creating a new main branch for features relating to the new versions. Again, it is essential that any subsequent forks continually merge with the correct main branch at frequent intervals.

### References

Kleier, T (2020) _[How to Version a REST API](https://www.freecodecamp.org/news/how-to-version-a-rest-api/)_, FreeCodeCamp website, accessed 31 May 2024.

ozanseymen (2016) _[Source Control for API Proxy Development](https://www.googlecloudcommunity.com/gc/Cloud-Product-Articles/Source-Control-for-API-Proxy-Development/ta-p/75620)_, Google Cloud Community website, accessed 31 May 2024.

## Q5. Provide an overview and description of a standard testing process for an API project. /6

In application development, tests should be written and executed throughout all stages of development and maintained to incorporate evolving functionality (Myakundi, 2022). In an API context, standard testing must contain contract testing and the stability of request and response formatting, singular end-point unit tests, user journey testing and the chaining of requests, as well as load testing and the API's ability to respond at an appropriate speed when faced with increased traffic (Postman, n.d. and SoapUI, 2024a).

When designing the specific tests, Jorgensen and Whitaker (2000) recommend category partitioning and Markov modelling to identify values to test with. Category partitioning recommends identifying all inputs that trigger default responses and testing at these boundaries. In an API interaction, this could refer to a required length or typing in a particular request field. After identifying these breaking points, tests should submit these values as well as values that just qualify such as 0 and 1 for an input that must be greater than 0. They also recommend using Markov modelling which is identifying the different conditions that affect an outcome and testing within those with varied sequencing. In an API context, this could refer to testing the result of a request when a user is authenticated versus not and then sequencing this with a different condition such as if the user's previous request was successful or not. Markov modelling is similar to end-to-end testing which tests user journeys and sequenced requests (Postman, n.d.).

In addition to typical functionality testing, it is also vital to test the security of an API (SoapUI, 2024b). The authentication process of an API must be tested to confirm that the API does not send data before confirming the identity of a user and ensuring this process perseveres when the server is receiving increased requests. Security tests should also ensure that users cannot submit requests with abnormal frequency, a typically malicious practice. Finally, APIs should be investigated to ensure they do not allow SQL injection that sends custom requests to the database (Myakundi, 2022).

Overall, API testing must consider functionality, performance and security. To most effectively test these elements, developers should maintain specific tests that incorporate appropriate mock data (Myakundi, 2022). Tools that can help with these tests include Insomnia, Postman and SoapUI.

### References

Jorgensen, A., Whittaker, J. (2000) _An API Testing Method_, Florida Tech.

Myakundi, H. (2022) _[API Testing Best Practices - How to Test APIs for Beginners](https://www.freecodecamp.org/news/rules-of-api-testing-for-beginners/)_, FreeCodeCamp website, accessed 31 May 2024.

Postman (n.d.) _[API Testing](https://www.postman.com/api-platform/api-testing/)_, SoapUI website, accessed 3 June 2024.

SoapUI (2024a) _[API Testing 101: Learn The Basics](https://www.soapui.org/learn/functional-testing/api-testing-101/)_, SoapUI website, accessed 3 June 2024.

SoapUI (2024b) _[State of API Security](https://www.soapui.org/learn/functional-testing/api-testing-101/)_, SoapUI website, accessed 3 June 2024.

## Q6. Explain the three principles of information system security. /6

The three principles of information system security are confidentiality, integrity and availability. These principles are commonly valued when creating data services and implementing security measures to protect them.

Confidentiality considers the legal and ethical obligations of companies when storing data to protect it from being released to inappropriate viewers (Mitchell and Osazuwa, 2023). In a medical database, an individual's name, birthdate, ailments and treatment history could be stored and an individual has a right to keep this information private. However, when receiving treatment, it is appropriate for a doctor to access this data to help their assessments. Confidentiality also considers when an individual has the right to consent or not consent to their data being stored or accessed (Olivier, 2002).

Integrity in information system security refers to data being trustworthy and accurate (Babenko et al., 2019). This means that data should not be alterable in unauthorised or disingenuous ways and, as such, security systems should only allow authorised users to alter data (Mitchell and Osazuwa, 2023). For example, a medical practitioner could be allowed to update an individual's health records so that they accurately reflect a new set of blood tests or diagnoses. Evidently, integrity and confidentiality are interconnected as anyone updating a piece of data manually would then know the new value recorded.

Availability is ensuring data can be accessed by authorised individuals when it is required (Babenko, et al., 2019). Availability can be considered as a right of the user when they consent to their data being stored as, otherwise, it may have been inappropriate to store that data (Olivier, 2002). Notably, availability is threatened by the failure of web services or server functions due to hardware faults, clogged communication channels and the lack of a fallback strategy to access the information (Mitchell and Osazuwa, 2023). In a medical field, availability could refer to a doctor having access to a patient's allergies when giving them medication.

Notably, confidentiality, integrity and accessibility are interconnected and must be balanced if they are to co-exist. Individually, any principle could be prioritised but it would come at the expense of another such as keeping a server offline which could preserve integrity but would significantly limit availability (Olivier, 2002).

### References

Babenko, M., Schwiegelsohn, U., Talbi, E. & Tchernykh, A. (2019), 'Towards understanding uncertainty in cloud computing with risks of confidentiality, integrity, and availability'. _Journal of Computational Science_, vol. 36, DOI:[10.1016/j.jocs.2016.11.011](https://doi.org/10.1016/j.jocs.2016.11.011)

Mitchell, O., Osazuwa, C. (2023), 'Confidentiality, Integrity, and Availability in Network Systems: A Review of Related Literature'. _International Journal of Innovative Science and Research Technology_, 8(12),  DOI:[10.38124/ijisrt](https://doi.org/10.38124/ijisrt)

Olivier, M. (2002), 'Database privacy: balancing confidentiality, integrity aand availability'. _SIGKDD Explorer Newsletter_, 4(3),  DOI:[10.1145/772862.772866](https://doi.org/10.1145/772862.772866)

## Q7. Provide an overview of what would need to be done within an API project to implement at least one of the principles explained in Question 6. /12

When initialising an API, confidentiality, integrity and availability must be guiding influences on how the API stores, returns and protects data. Because all three principles are connected, different, simple measures can bolster an API's ability to make strides in all three.

Enforcing authentication and limiting authorisation is a principle measure that increases an APIs confidentiality and integrity. APIs are designed to be accessed in varying user contexts such as a factory worker needing access to customer's name and address to create a postage label whilst a marketing worker may require the same customer's name and email address for promotional material. In contexts such as these, it would increase data confidentiality to only allow access to appropriate column data by each department. This can be enforced by creating unique user accounts per worker and granting distinct privileges to those users. Similarly, only certain workers should be allowed to alter tuple data to maintain database integrity. These systems can be set-up by creating log in routes that post a log in attempt to the API. The log in credentials can be checked against a hashed password stored to allow or block the log in attempt. When the worker logs in, they could be granted a JWT that is inspected on each request. Notably, it is important to implement session management and pass tokens with appropriate expiry times (Worksoft Corporate Blog, n.d.). This ensures that a user's session cannot be hijacked when they leave a workstation or lose a device. Below is an example of checking a user's login attempt and returning a JWT token if successful using Flask with the flask_jwt_extended, sqlalchemy, marshmallow and flask-bcrypt:

```Python
@app.route("/workers/login", methods=["POST"])
def login():
    params = UserSchema(only=["id", "password"]).load(
        request.json, unknown="exclude"
    )
    # creates a Python object with key pairs from the user's passed "id" and "password" using a defined marshmallow model schema
    stmt = db.select(User).where(User.id == params["id"])
    # creates an SQL query using a User model defined with SQLAlchemy that matches a database's table schema. Specifically requests the row where the "id" value matches the users input for "id"
    user = db.session.scalar(stmt)
    # assigns the returned object from the query to a local variable or sets it to none if a user with the input "id" does not exist  
    if user and bcrypt.check_password_hash(user.password, params["password"]):
    # uses bcrypt to decode the stored hashed password in the database linked to the input id and compares it to the input password value
        token = create_access_token(identity=user.id, expires_delta=timedelta(minutes=30))
    # if the passwords match, a JWT is created with an expiration date of 30 minutes. This JWT confirms that the user logged in via the appropriate method and can be checked when requesting certain routes to confirm the user has appropriate authentication to access those resources
        return {"token": token}
    else:
        return {"error": "Invalid email or password"}, 401
    # if the user's input id or password are incorrect, they are returned a HTTP error code 401
```

Another way to improve ensure confidentiality is to never pass a user's data via URLs (Amazon Web Services, 2024). If user's log in attempt or other private data is passed as a variable in a URL rather than in the body, the data would be accessible and obtainable from that user's browser history.

To improve an API's accessibility, it is vital to structure the API so that it is RESTful. Resource URLs need to be structured in a predictable and semantic way that describes the data they are attempting to access. Routing resources in a "collective noun/individual id" structure such as "biographies/bio1" helps users access data easily and logically.

### References

Amazon Web Services. (2024) _[Data protection in Amazon API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/data-protection.html)_, AWS website, accessed 7 June 2024.

Worksoft Corporate Blog. (n.d.) _[Data protection in Amazon API Gateway](https://www.worksoft.com/corporate-blog/api-security-testing-ensuring-the-integrity-and-confidentiality-of-your-apis)_, Worksoft website, accessed 7 June 2024.

## Q8. Explain the legal obligations that developers of a social media website or social media application would have in regards to handling user data, with reference to any applicable laws or acts. /12

Social media websites and applications inherently require data of varying scopes to be stored. From email addresses, to names and optional personifiers such as date of birth, location data and images, social media companies request a lot of data but also receive a lot voluntarily. These companies must implement security practices to uphold confidentiality, integrity and availability of data and they must do so in a way that follows domestic as well as international laws. These laws specify how data can be stored and used as well as what constitutes a failure from the company's practices.

In Australia, data privacy regulations are derived from the Australian Privacy Act from 1988 as well as the thirteen Australian Privacy Principles which, together, dictate guidelines and rules for businesses to adhere to when storing user data (Australian Government Office of the Australian Information Commissioner, n.d.). The privacy principles outline data-based interactions and mandate that companies must be transparent in their storage policies, clarify when data is being stored and obtain consent when doing so, communicate with customers when their information is being shared with third-parties as well as allowing users to know what data is stored about them and give them the opportunity to correct any errors in it (principles 1, 5, 6, 12 and 13). Principles 2, 3, 4 and 7 outline that companies must offer individuals the ability to use their services without their data being stored or through using a pseudonym, not store particular data including race or union affiliation, destroy or de-identify irrelevant data and follow a set of rules when using direct marketing. Finally, principles 8, 9, 10 and 11 outline security procedures for sending data internationally, the restriction of releasing government ID data, how companies must reasonably attempt to keep data up to date and, vitally, that companies must protect data from unauthorised access. Notably, the Australian government is currently in the process of updating these laws and regulations to include stricter guidelines about depersonalising and destroying data after certain time periods and granting users the ability to oppose the storage of their data (Australian Government Attorney-General's Department, 2023).

In addition to Australian laws, an Australian-based social media company must consider foreign laws that apply to any international users that the company may acquire. The GDPR (General Data Protection Regulation) is a collection of regulations that enforce how EU residents' data may be collected and stored. Importantly, the GDPR applies to foreign businesses that offer goods or services or store behaviour data about individuals living in the EU including the use of cookies (Wolford, B., n.d.). Whilst many GDPR regulations are mirrored by the Australian Privacy Act, there are notable instances where the GDPR has much stricter and more explicit requirements (Australian Government Office of the Australian Information Commissioner, 2018). Unlike Australian laws, data privacy laws apply to all scales of businesses, require all businesses to complete a compulsory data protection assessment and employ an appointed data protection officer. The regulation also features "right to erasure", a "right to data portability" and a "right to object" which gives individuals the means to have their data deleted upon request, receive stored data about them in a conventional and reasonable data format and the ability to challenge the storage of their data. It is vital that any social media company consider security laws that can be enforced on behalf of foreign users.

Considering the widespread laws relating to data privacy, it is essential that a social media company creates a thorough plan for how it will handle user data. At a fundamental level, data must be stored in a way that protects individual privacy and companies should take measures to depersonalise, securely store or, simply, not store personal data where appropriate. It is also crucial that a social media company has an individual professionally responsible for the company's policies who understands the laws that affect the company. Because users must be able to access, alter or, as per the GDPR's "right to be forgotten", delete archived data, companies must develop techniques that easily allow these actions. Finally, data storage consent is a particularly prominent focus of the GDPR and Australian laws and companies must be deliberate in communicating users these options. In 2023, the GDPR issued Tik Tok, a predominately foreign company, a €345 million fine for presenting teenage users misleading consent options between July 2020 and December 2020. During this time, the app presented subtle and hard to comprehend optionality for making a user's account and videos private (EDPB, 2023). With such rulings as well as an imminent increase to Australian laws, a social media company must err on the side of communication in its data privacy practices and transparency with users.

### References

Australian Government Attorney-General's Department, (2023), _[Privacy Act Review Report](https://www.ag.gov.au/rights-and-protections/publications/privacy-act-review-report)_, Australian Government website, accessed 8 June 2024.

Australian Government Office of the Australian Information Commissioner, (2018), _[Australian entities and the European Union General Data Protection Regulation](https://www.oaic.gov.au/privacy/privacy-guidance-for-organisations-and-government-agencies/more-guidance/australian-entities-and-the-european-union-general-data-protection-regulation)_, Australian Government website, accessed 8 June 2024.

Australian Government Office of the Australian Information Commissioner, (n.d.), _[Australian Privacy Principles quick reference](https://www.oaic.gov.au/privacy/australian-privacy-principles/australian-privacy-principles-quick-reference)_, Australian Government website, accessed 8 June 2024.

EDPB (2023), _[Following EDPB Decision, TikTok ordered to eliminate unfair design practices concerning children](https://www.edpb.europa.eu/news/news/2023/following-edpb-decision-tiktok-ordered-eliminate-unfair-design-practices-concerning_en)_, GDPR website, accessed 9 June 2024.

Wolford, B. (n.d.), _[Does the GDPR apply to companies outside of the EU?](https://gdpr.eu/companies-outside-of-europe/)_, GDPR website, accessed 8 June 2024.

Australian Government Office of the Australian Information Commissioner, (2018), _[Australian entities and the European Union General Data Protection Regulation](https://www.oaic.gov.au/privacy/privacy-guidance-for-organisations-and-government-agencies/more-guidance/australian-entities-and-the-european-union-general-data-protection-regulation)_, Australian Government website, accessed 8 June 2024.

## Q9. Describe the structural aspects of the relational database model. Your description should include information about the structure in which data is stored and how relations are represented in that structure. /6

The relational model is a format for describing and storing data in a standardised table format. The relational model is utilised in relational databases which contain collections of tables to be accessed in flexible ways whilst preserving the data's integrity (Jatana et al., 2012). These tables, also known as relations, feature columns which describe attributes of an entity, formatted in defined data types, and are seeded with rows that represent individual sets of data, also known as tuples (Geeks for Geeks, 2024a). A table and the columns it features is referred to as the relation schema.

Relations are configured with primary keys, values that are unique to a specific tuple and make each row distinct (Oracle, n.d.). The relational model also allows distinct tables to be linked by sharing a primary key from one table to be used as a primary key in a different table. The borrowed primary key is called a foreign key. Tables can also be configured so that their primary key is comprised of two values combining to make a unique identifier. This is called a composite key. Finally, two or more tables can also contribute foreign keys to create a primary key in another table called a compound key (BBC, n.d.).

Primary keys, foreign keys, composite keys and compound keys allow for the different types of cardinal relationships. In a database, a single foreign key can by used to represent a one-to-one relationship such as an individual's name being linked to a single customer ID in a database. Alternatively, a composite key comprised of a foreign key and a separate attribute can be used for one-to-many relationships such as a single customer's ID being linked to multiple orders with unique order numbers. Finally, a compound key of foreign keys can represent many-to-many relationships such as an inventory of items that can be optionally ordered by multiple customers (Geeks for Geeks, 2024b).

### References

BBC (n.d.) _[Design: Types of keys](https://www.bbc.co.uk/bitesize/guides/z4wf8xs/revision/4#:~:text=In%20a%20relational%20database%2C%20keys,and%20identify%20relationships%20between%20them.)_, BBC website, accessed 4 June 2024.

Geeks for Geeks (2024a) _[Relational Model in DBMS](https://www.geeksforgeeks.org/relational-model-in-dbms/)_, Geeks for Geeks website, accessed 4 June 2024.

Geeks for Geeks (2024b) _[Relationships in SQL - One-to-One, One-to-Many, Many-to-Many](https://www.geeksforgeeks.org/relationships-in-sql-one-to-one-one-to-many-many-to-many/)_, Geeks for Geeks website, accessed 4 June 2024.

Jatana, N., Puri, S., Ahuja, M., Kathuria, I., & Gosain, D. (2012). A Survey and Comparison of Relational and Non-Relational Database. _International journal of engineering research and technology_, 1.

Oracle (n.d.) _[What is a Relational Database (RDBMS)?](https://www.oracle.com/au/database/what-is-a-relational-database/)_, Oracle website, accessed 4 June 2024.

## Q10. Describe the integrity aspects of the relational database model. Your description should include information about the types of data integrity and how they can be enforced in a relational database. /6

The relational model is designed to ensure data integrity by featuring keys. Primary keys being mandated ensures that data is uniquely identifiable and also prevents a single instance of data from being entered multiple times (Levene and Loizou, 2001). By making each entry unique, data loss from disorganisation is reduced and users accessing or updating the data are ensured that they are not missing any stored information which can happen in non-relational data storage. Foreign keys also preserve integrity by maintaining relationships between different tables and attributes so that data is not lost.

At a database level, relational models are programmed with safeguards to ensure data remains trustworthy. Relational databases lock tables or rows data when it is being updated so that it cannot be queried whilst incomplete or incorrect. Similarly, relational databases make database changes permanent to ensure data is accurate when it is submitted (Oracle, n.d.). User roles, passwords and privileges can also be implemented to restrict data editing to qualified, trustworthy individuals too (Babenko et al., 2019). Restricting columns from allowing non-null values and accepting only specific data types is another simple measure to ensure that any entered and queried data is complete and, therefore, trustworthy (Levene, Loizou, 2001).

Using Postgres, the integrity measures of establishing a unique serial value as a primary key, requiring a column value and specifying data types can executed as so:

``` Postgres
    CREATE TABLE example (id SERIAL PRIMARY KEY, name TEXT NOT NULL, age INT);
```

Once this table is generated, an attempt to seed the table without a name value or by inputting an age value as a text string will fail:

![Error messages from inapproriate data seeding into "example" table](/docs/postgres_integrity_eg1.png)

By extension, correct data entries will have a uniquely generated primary key in a column named "id" ensuring that similar entries are segregated:

![Distinct entries from similar data](/docs/postgres_integrity_eg2.png)

These measures, whilst simple, are fundamental to relational databases' integrity.

### References

Babenko, M., Schwiegelsohn, U., Talbi, E. & Tchernykh, A. (2019), 'Towards understanding uncertainty in cloud computing with risks of confidentiality, integrity, and availability'. _Journal of Computational Science_, vol. 36, DOI:[10.1016/j.jocs.2016.11.011](https://doi.org/10.1016/j.jocs.2016.11.011)

Levene, M. and Loizou, G. (2001) ‘A Generalisation of Entity and Referential Integrity in Relational Databases’, RAIRO - Theoretical Informatics and Applications, 35(2), pp. 113–127. DOI:10.1051/ita:2001111[https://doi.org/10.1051/ita:2001111].

Oracle (n.d.) _[What is a Relational Database (RDBMS)?](https://www.oracle.com/au/database/what-is-a-relational-database/)_, Oracle website, accessed 4 June 2024.

## Q11. Describe the manipulative aspects of the relational database model. Your description should include information about the ways in which data is manipulated (added, removed, changed, and retrieved) in a relational database. /6

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

Tuples in a table can be manipulated permanently using the "UPDATE" functionality. In this example, tuples where the "brand" and "style" attributes of "Nike" and "Air Jordan 4" respectively have their "price" value set to "199.99".

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

Querying the data can also allow for powerful temporary manipulation. "SELECT" is used to target and return specific tuples based on defined criteria known as clauses. The following returns the style and price of all shoes with brand value "Nike".

```Postgres
    SELECT style, price
    FROM shoes
    WHERE brand = 'Nike'
```

Tables linked via matching values such as foreign keys can also be temporarily joined by comining a "SELECT" statement with one of the "JOIN" keywords. The type of join defines how the tables are returned. "JOIN" defaults to "INNER JOIN" which only returns tuples where the clause conditions are true. Alternatively, "LEFT JOIN", "RIGHT JOIN" and "FULL JOIN" align rows where the clause conditions match but also return values that do not have matches. For example, if a second table is created and seeded that uses the style of shoe as a foreign key, the following would combine the tables with the style listed first then the price, colour way name, primary colour and secondary colour values listed left to right.

```Postgres
SELECT colour_ways.style, price, colour_way_name, primary_colour, secondary_colour FROM colour_ways INNER JOIN shoes ON colour_ways.style = shoes.style;  
```

Returns this:

![The results using "INNER JOIN" as described above](/docs/postgres_inner_join_eg1.png)

These keywords and techniques allow users to manipulate data in powerful ways that maintain the relational database model.

### References

PostgreSQL Documentation (n.d.a) _[psql](https://www.postgresql.org/docs/current/app-psql.html)_, PostgreSQL website, accessed 5 June 2024.

PostgreSQL Documentation (n.d.b) _[Truncate](https://www.postgresql.org/docs/16/sql-truncate.html)_, PostgreSQL website, accessed 5 June 2024.

## Q12. Conduct research into a web application (app) and answer each of the following sub-questions: /42

### A. List and describe the software (tech stack) used by the app

Pinterest is a web application that allows users to keyword search for images to "pin" on user-created "pinboards" that collate images in particular orders. These images are uploaded to Pinterest by companies or individuals and they are displayed with a title, the user who uploaded them and they can link to external websites such as blogs or online stores (Pinterest Help, n.d.). User's boards are typically used for creative inspiration and the site functions largely like a social media app (Pinterest Business, n.d.). Notably, Pinterest was famously able to achieve a massive user base with a simple, but scalable, tech stack (Engineer's Codex, 2023). As the app has grown, it has incorporated varying tools, libraries and software that allow it to achieve increased functionality such as suggestive ad serving and user interaction tracking however its core functionality is built upon the pinboard functionality (The Technology Vault, n.d., ).

Python is the predominant coding language used for Pinterest's backend and data processing and it is used in conjunction with Django. Django is an web framework that features routing, user authentication as well as ORM tools to facilitate database interactions. For its databases, Pinterest uses MySQL, an an open-source relational database and an alternative to PostgreSQL. For the front-end, Pinterest uses React which is a Javascript library containing tools to build interactive HTML webpages. To improve the efficiency of server requests, Pinterest leverages NGINX, an open-source web-server and reverse proxy. NGINX operates between user requests and a company's servers to execute requests in an optimised way by distributing traffic to less-strained resources. Pinterest also utilises both Redis and Memcached for data caching. Each software has its strengths and Memcached is optimised for storing and returning key-value pairs quickly whilst Redis is utilised for storing complex data structures (Amazone Web Services, n.d.).

### References

Amazon Web Services (n.d.) _[Comparing Redis and Memacached](https://aws.amazon.com/elasticache/redis-vs-memcached/)_, Amazon Web Services website, accessed 9 June 2024.

Engineer's Codex (2023) _[How Pinterest scaled to 11 million users with only 6 engineers](https://read.engineerscodex.com/p/how-pinterest-scaled-to-11-million)_, Engineer's Codex website, accessed 9 June 2024.

Pinterest Business (n.d.) _[How Pinterest Works](https://business.pinterest.com/en-au/how-pinterest-works/)_, Pinterest Business website, accessed 9 June 2024.

Pinterest Help (n.d.) _[All about Pinterest](https://help.pinterest.com/en/guide/all-about-pinterest)_, Pinterest Help Center website, accessed 9 June 2024.

StackShare (n.d.) _[Stack History: A Timeline of Pinterest's Tech Stack Evolution](https://stackshare.io/stack-history-timeline-pinterest-tech-stack-evolution)_, StackShare website, accessed 9 June 2024.

The Technology Vault (n.d.) _[Pinterest Tech Stack](https://thetechnologyvault.com/pinterest-tech-stack)_, The Technology Vault.com website, accessed 9 June 2024.

### B. Describe or make educated guesses about the hardware used to host the app

Pinterest uses Amazon services to host its databases as well as to execute cloud computing. Amazon S3 is a storage service that offers specific storage options for more or less frequently accessed data. Pinterest has publicly described how it uses different S3 storage classes including the S3 Glacier Flexible Retrieval and S3 Glacier Deep Archive services for less used, archival storage such as data from years ago (Yin et al., 2021). It also uses, non-specified, faster web S3 services such as the S3 Standard service which is optimised for frequently accessed data (Amazon Web Services, n.d.). S3 are cloud databases that store data in key pairs in storage centres located around the world. Specific Amazon hardware is a trade secret but it is reasonable to assume their data centres feature advanced proprietary servers with solid-state hardware. Pinterest also uses Amazon's EC2 services which provide virtual servers for running cloud processing (Amazon Elastic Compute Cloud, 2024). These two Amazon services can communicate at bandwidth's of up to 100GBs (Amazon Knowledge Center, 2023). With more than 440 million users and being a prominent user of Amazon Web Services, it is safe to assume that Pinterest accesses Amazon's fastest resources (Yin et al., 2021). It is worth noting that, in 2015, Pinterest had 10 petabytes of data stored in S3 (Weiner) and so, with millions more users and 9 more years of archived data, it is clear that Pinterest is hosted by very, very significant hardware.

### References

Amazon Elastic Compute Cloud (2024) _[What is Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)_, Amazon Web Services Website, accessed 9 June 2024.

Amazon Knowledge Center (2023) _[What's the maximum transfer speed between Amazon EC2 and Amazon S3?](https://repost.aws/knowledge-center/s3-maximum-transfer-speed-ec2)_, Amazon re:Post Website, accessed 9 June 2024.

Amazon Web Services (n.d.) _[Amazon S3 FAQs](https://aws.amazon.com/s3/faqs/)_, Amazon Web Services Website, accessed 9 June 2024.

Weiner, M. (2014) _[Powering big data at Pinterest](https://medium.com/pinterest-engineering/powering-big-data-at-pinterest-3c4836e2b112)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

Yin, Y., Yang, B., Kou, X. (2021) _[How Pinterest uses Amazon S3 Glacier Deep Archive to manage storage for its visual discovery engine](https://aws.amazon.com/blogs/storage/how-pinterest-uses-amazon-s3-glacier-deep-archive-to-manage-storage-for-its-visual-discovery-engine/)_, Amazon Storage Blog website, accessed 9 June 2024.

### C. Describe the interaction of technologies within the app

To consider how the different software in Pinterest's stack interact, it is helpful to start at the front end. Pinterest began using ReactJS for its webpage rendering in 2015 and their developers have described how their data flow works when a user makes a request (Chan, 2016). When a user requests a Pinterest webpage, the request first passes through an NGINX proxy layer that sends the request to Pinterest's servers in an efficient way. Once received by Pinterest servers, the servers use React and Node to begin compiling the document to be returned. This involves making requests to Pinterest's different data APIs to return data that will populate the page such as images (Semah, 2022). These APIs are coded using Django and the data requests follow the appropriate routes to access the necessary data. These routes generate SQL statements to query Pinterest's databases. Notably, the databases may be queried directly, but it is likely that data cached via Redis and Memcached's algorithms can be returned without passing requests to the MySQL databases directly. The requested data is then returned to React which inserts it to complete the HTML document which, once finished is delivered to the user and rendered in their browser.

### References

Chan (2016) _[How we switched our template rendering engine to React](https://medium.com/pinterest-engineering/how-we-switched-our-template-rendering-engine-to-react-a799a3d540b0)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

Semah, B. (2022) _[What Exactly is Node.js? Explained for Beginners](https://www.freecodecamp.org/news/what-is-node-js/)_, freeCodeAcademy Website, accessed 9 June 2024.

### D. Describe the way data is structured within the app’s database(s)

Pinterest stores its data using MySQL databases. Notably, they have adopted this structure for its effectiveness and popularity. Pinterest engineer Weiner (2014a) explains that MySQL is used by the company for its maturity and scalability. As a company that requires extensive, and increasing, database queries, MySQL is an effective database that has proven its effectiveness through extended industry prominence. In addition, Weiner celebrates the breadth of knowledge about and developed features of MySQL.

Notably, the significant amount of image data in Pinterest means that the application generates extremely large database files. Because of this, their data could not be stored on finite databases or single locations. In anticipation of increased data storage and to improve API performance, Pinterest implemented database sharding that segregated and divided their MySQL databases across servers (Weiner, 2014b). Notably, this process restricts the APIs from using joins or foreign keys to link data that is stored on separate servers, a significant decision. Sharding requires significant restructuring of the ways that data is accessed and the information contained in a tuple. To ensure data is trackable within a sharded system, Pinterest records tuple information about which shard their master is stored in and mandates that data should not be moved or saved in different shards once it is recorded. To overcome the inability to join tables, Pinterest uses mapping tables that consider the shard values to access data from different shards which are then joined at the application layer.

Whilst Pinterest's database systems are unconventional, they are appropriate for their data-intensive storage requirements.

### References

Weiner, M. (2015a) _[Powering big data at Pinterest](https://medium.com/pinterest-engineering/powering-big-data-at-pinterest-3c4836e2b112)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

Weiner, M. (2015b) _[Sharding Pinterest: How we scaled our MySQL fleet](https://medium.com/pinterest-engineering/sharding-pinterest-how-we-scaled-our-mysql-fleet-3f341e96ca6f)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

### E. Identify the entities/tables that are tracked within the app’s database(s)

Weiner (2015) outlines key tables that are stored in the Pinterest databases: Pins, users, boards and comments. Considering how the user can interact with these features, it is reasonable to assume the tables have the following attributes:

Pins: "description, "link", "user_id", "board_id", "pin_id", "shard_id", "date_pinned"
Users: "email", "password", "id", "shard_id", "boards"
Boards: "id", "board_title", "user_id", "shard_id", "has_pins", "pin_sequence", "date_created", "visibility"
Comments: "id", "user_id", "pin_id", "shard_id", "content", "date_created", "edited"

### References

Weiner, M. (2015) _[Sharding Pinterest: How we scaled our MySQL fleet](https://medium.com/pinterest-engineering/sharding-pinterest-how-we-scaled-our-mysql-fleet-3f341e96ca6f)_, Pinterest Engineering Medium Website, accessed 9 June 2024.

### F. Identify the relationships and associations between the entities/tables identified in sub-question E

Users has a one to many relationship with pins, boards and comments. Pins, boards and comments would then each use user ID as a foreign key to contribute to their primary keys. Pins are linked to boards via "board_id", a foreign key that uses a board's ID to link individual pins to a board. A board must also preserve values to sequence the pins linked to it in a "pin_sequence" value. This would update as the user adds pins and rearranges them. Boards have a one to many relationship with pins. Users can also comment on pins unlimited times so a comment's primary key would be a compound key from the pin ID that it was posted on, the user ID who commented it and a comment ID to differentiate it from a user's other comments on the same pin.

### G. Design an entity relationship diagram (ERD) based on the answers provided to sub-questions 5 and 6. This must represent a relational database model, even if the app itself uses something other than a relational database model

![Pinterest ERD](/docs/Pinterest-ERD-v1.0.png)
