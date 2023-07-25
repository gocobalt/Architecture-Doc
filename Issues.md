## Current Problems To Address

**Lack of granular performance monitoring: [Sub Critical ]**

**Context**

On the side of infrastructure currently we deploy our services on one EC2 instance.
We have tried ECS before, it blew up costs for extermely under-utilized machines (we had small loads).

On AWS we get machine specific metrics or process specific metrics.

Example: This server @ 1:00 am had memory utilization of 90% or Process X utilized this much memory.

We are able to identify, which service consumed more RAM. We want more information,

Such as heatmaps [with memory utilization of each method in call], the call stack during execution,all necessary snapshots.

Why?

Current Hypothesis, we declare a lot of data-structures (hashmaps etc, for efficient algorithms) in code, which may stay in memory before garbage collection kicks in and other efficiency related issues  

**Current Solutions Tried:**

We tried adopting solutions such as node-doctor, graphana, etc. Issue is that the metric logs are extemely high in number and often contain lots of information that is not required which makes debugging method level info a pain.

**Expectations**

1. Setting up the infra that works best for these kinds of monitoring.
2. Developing Load Testing stratergy since we can expect to deal with high loads from early stage of the company.
3. KT sessions or similar to make team capable of understanding the monitoring process. Aim is to make engineers capable to know basic performance bottlenecks on own.


**Database modeling for efficiencies [Critical]**

We currently employ MongoDB database throughout our system. Collections responsible for maintaining audits already has a million entry. Causing efficiency issues.

Hypothesis:

To change the data model, would be first step towards efficiency.

**Expectations**

0. Exp in both SQL and NoSQL DB to identify, scopes of optimization.
1. Collaborating with enineering teams to have efficient data models, based on use case and keeping legacy in mind.
2. Set up DB profiling.
3. Optimizing Queries and Aggregation pipelines.


**Concurrency Issues and Distributed Transactions**

While scaling, we often run into issues such as, not being able to delete edge and node if API is fired in parallel. (Among Others)

**Expectation**

Having discussions with engineering teams, based on load testing stratergy,
try to achieve greater efficiencies by parallel processing and having consistency in system.   


**Code reduction and better design**

**Expectation**

Identifying design flaws in low-level (class level) flow, guiding engineering team to have better design, (We strictly want to avoid copying pasting boilerplate codes, it gives high learning curve to new devs and doesnt scale well).  

**Testing Statergy [Sub Critical]**

There are currently no unit tests on platform and infrastructre layer is higly coupled in backend. 

We can not refactor confidently or deploy with confidence. 

**Expectations**

Guiding Engineering team to write tests that wil matter, instead of random assertions for coverage.  
