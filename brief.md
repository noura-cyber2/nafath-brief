Version: NAFATH-V2
Track: Cybersecurity

## Overview

An emergency 5G service helps responders send and receive information fast, so every part must work together. A mobile app lets responders use the service in the field. Software on the phone and servers sends requests, and it must be careful when it retries a failed request. Networking gives the service a dedicated 5G slice, so emergency traffic stays fast even when the network is busy. AI predicts congestion before it happens. Data reports show how much the service is used in each region every day. Cybersecurity protects all of these parts from attacks. If one part fails, the others are affected too. This is why the operator must plan all six fields together, not one by one. The incident response lifecycle helps the team get ready for, handle and learn from attacks on this service.

## Software

Safe methods read data and change nothing on the server. GET, HEAD, OPTIONS and TRACE are safe. Idempotent methods can be repeated: sending them once or many times gives the same result. All safe methods are idempotent, and so are PUT and DELETE. POST is not. This matters when a client automatically retries a failed request, because it may not know if the first one worked. Retrying idempotent methods is safe, but a retried POST may run twice.

Resource: HTTP Semantics (RFC 9110) - https://www.rfc-editor.org/rfc/rfc9110

## AI

Overfitting is when a model learns its training data too well, including noise, so it works well on old data but badly on new data. Such a congestion model may fail on new traffic. Cross-validation helps detect it. The data is split into parts. The model trains on some parts and is tested on a part it has not seen. If the test scores are much lower than the training scores, the model is overfitting.

Resource: Cross-validation: evaluating estimator performance - https://scikit-learn.org/stable/modules/cross_validation.html

## Mobile

A responder's app should keep working offline. It saves data on the phone, so the responder can still read maps and write reports. The app stores each change in a local queue. When the connection returns, it sends the queued changes to the server and downloads new updates. If two changes conflict, the app needs a rule, such as keeping the newest change. The app should also show which data is not yet synced.

Resource: Build an offline-first app - https://developer.android.com/topic/architecture/data-layer/offline-first

## Networking

5G network slicing creates separate logical networks on top of the same physical network. Each slice has its own capabilities, such as speed, delay and reliability. A dedicated slice for emergency responders would give them priority over normal users, so they can use the network first when it is busy. The slice could also support push-to-talk, video and data for emergency work. It keeps responder data apart from normal traffic, which helps security.

Resource: Generic Network Slice Template (GSMA NG.116 v3.0) - https://www.gsma.com/newsroom/wp-content/uploads/NG.116-v3.0.pdf

## Cybersecurity

Incident response has four phases. In Preparation, a company gets ready before any attack: it makes a plan, trains staff, and sets up tools. In Detection and Analysis, the team checks alerts and logs, finds what happened, and writes down every fact with the time. In Containment, Eradication and Recovery, the team stops the attack from spreading, removes the cause, and brings the 5G service back. In Post-Incident Activity, the team learns from mistakes and improves the plan.

Resource: Computer Security Incident Handling Guide (NIST SP 800-61 Rev. 2) - https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf

## Data

A star schema has one fact table in the center, with dimension tables joined directly to it. A snowflake schema splits a dimension into smaller related tables. This removes repeated data, but adds more tables and joins. For reports of usage per region per day, the star schema suits better. The fact table has one row per region per day, and the region and date dimensions connect to it. Fewer joins make reports faster and easier to build.

Resource: Understand star schema and the importance for Power BI - https://learn.microsoft.com/power-bi/guidance/star-schema

## Misconception in My Track

A common wrong belief is that incident response only starts after an attack happens. Many people think the team just waits and then reacts when something goes wrong. This is not correct. Incident response starts much earlier, with preparation. The team must be ready before any attack: it needs a plan, trained people, and the right tools. Preparation also means preventing incidents by keeping systems, networks, and applications secure. When the team has its tools and plan ready, it can respond faster and handle incidents better. This is shown in NIST SP 800-61 Rev. 2, Section 3.1 "Preparation".

## Open Question

When many alerts come at the same time, how can the team decide which incident to handle first? I would like to learn how an emergency 5G service can sort incidents by how much they affect responders.
