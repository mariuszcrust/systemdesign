## Problem nr 1
(INBOUND, EXTERNAL) : A customer uses Monte Carlo as a tool for data observability. They have set it up so that Monte Carlo catches any table health or data reliability issues early on. The customer would like Atlan to also become a near-real-time repository of such issues, with relevant metadata attached to respective assets.


![MonteCarloCase (1)](https://github.com/mariuszcrust/systemdesign/assets/7340196/426422b3-eefd-47ab-a275-d17fe22a30e2)



## Problem nr 2
(OUTBOUND, INTERNAL) : There are internal enrichment automation requirements towards metadata into Atlan, such that any change in the Atlan entity triggers similar changes to entities connected downstream in lineage from that entity.


![DataLineageEnrichment (1)](https://github.com/mariuszcrust/systemdesign/assets/7340196/9f2a5165-201d-4e0a-a058-3ef64a526bb4)




## Requirements:
- Near-real-time nature of the solution
  - Using CDC (Debezium) and Kafka will ensure near real-time nature 
- Schematics when ingesting and consuming metadata
- Selecting an appropriate metadata store to work with these capabilities
  - I don't have to much experience in analytics databases. From what I have read and found Druid seems to be a good solution in case of near real-time analytics, with direct connection to Kafka
- Capability for pre-ingest and post-consume transformations where needed on the metastore
  - Stream processing by Flink will have us possibility to trasnform as we want data that we want to insert into analytcis database. 
- Authentication and authorization as first-class citizens in the system
- Tenancy as a problem statement in mind, given customers range from comfort deploying in a multi-tenant setup, to wanting complete isolation in their setup
  - On the database level by column tenant_id or schema. During requests, we can set an additional header in the request to identify tenants. In Kafka, we can have different topics with the syntax ClientX.TopicY (topic pattern). In Avro, we can force events to keep   
  information about tenant ID
- Deploying the solution in a plug-and-play fashion as more use cases come in
- Solving for SaaS sources and targets such as Slack, JIRA, MS-Teams, Freshdesk, and Okta
- Adaptability to inbound and outbound consumers to scale as per the volume of metadata change events hitting the platform
  Using CDC and message queue should make the solution highly scalable
- Cost of deploying the solution proposed
- Observability of the platform
