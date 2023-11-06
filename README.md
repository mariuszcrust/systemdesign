System Design interview

Requirements:
- Near-real time nature of the solution
- Schematics when ingesting and consuming metadata
- Selecting an appropriate metadata store to work with these capabilities
- Capability for pre-ingest and post-consume transformations where needed on the metastore
- Authentication and authorization as first-class citizens in the system
- Tenancy as a problem statement in mind, given customers range from comfort deploying in a multi-tenant setup, to wanting complete isolation in their setup
- Deploying the solution in a plug-and-play fashion as more use cases come in
- Solving for SaaS sources and targets such as Slack, JIRA, MS-Teams, Freshdesk, and Okta
- Adaptability to inbound and outbound consumers to scale as per the volume of metadata change events hitting the platform
- Cost of deploying the solution proposed
- Observability of the platform

Problem nr 1
(INBOUND, EXTERNAL) : A customer uses Monte Carlo as a tool for data observability. They have set it up so that Monte Carlo catches any table health or data reliability issues early on. The customer would like Atlan to also become a near-real-time repository of such issues, with relevant metadata attached to respective assets.







Problem nr 2
(OUTBOUND, INTERNAL) : There are internal enrichment automation requirements towards metadata into Atlan, such that any change in the Atlan entity triggers similar changes to entities connected downstream in lineage from that entity.



