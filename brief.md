Version: NAFATH-V2
Track: Cybersecurity

## Overview

An emergency 5G service helps responders send and receive information fast, so every part must work together. A mobile app lets responders use the service in the field. Software on the phone and servers sends requests, and it must be careful when it retries a failed request. Networking gives the service a dedicated 5G slice, so emergency traffic stays fast even when the network is busy. AI predicts congestion before it happens. Data reports show how much the service is used in each region every day. Cybersecurity protects all of these parts from attacks. If one part fails, the others are affected too. This is why the operator must plan all six fields together, not one by one.

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

## Cybersecurity

## Data

## Misconception in My Track

## Open Question
