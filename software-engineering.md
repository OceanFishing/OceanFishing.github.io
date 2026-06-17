---
layout: page
title: Software Engineering and Design
---

**Enhancement:** Rewrite the Node.js and Express backend in Python and FastAPI while preserving the API contract so the Angular frontend runs unchanged.
**Course Outcome:** Outcome 4, using well-founded and innovative techniques, skills, and tools to implement solutions that deliver value.
**Original code:** [`main` branch](https://github.com/OceanFishing/cs499-capstone/tree/main) &nbsp;|&nbsp; **Enhanced code:** [`enhancement-1` branch](https://github.com/OceanFishing/cs499-capstone/tree/enhancement-1)

---

## Artifact Description

The artifact selected for this enhancement is the Travlr Getaways full-stack web application, originally developed during CS 465 in early 2026. The project was built using the MEAN stack (MongoDB, Express, Angular, and Node.js) and implements a travel booking interface that allows customers to browse available trips through an Angular single-page application while administrators manage trip data through a separate Angular admin panel. The backend exposes a REST API built with Express and Node.js, which handles authentication through JSON Web Tokens and persists data in a MongoDB database using Mongoose as the object-document mapper. The artifact represents a complete, multi-layer application with authentication, data modeling, and full CRUD functionality across both the customer-facing and administrative surfaces.

## Justification for Inclusion

This artifact was selected because it offered a substantive and well-scoped opportunity to demonstrate growth in software engineering and design, and because its existing implementation contained several identifiable weaknesses that made the case for rewriting it particularly clear. The enhancement involved rewriting the entire server layer, replacing Node.js and Express with Python and FastAPI, while preserving the existing API contract so that the Angular frontend required no modification whatsoever. This constraint, that the interface must remain identical while the underlying implementation changes entirely, is precisely the kind of engineering discipline that distinguishes a thoughtful developer from one who simply produces output.

The specific components that showcase software engineering skills include the migration from Mongoose-based data modeling to Pydantic, which enforces typed request and response validation at the framework level rather than relying on the developer to validate manually; the replacement of Passport.js with a custom dependency-injected JWT verification function using PyJWT, which makes the authentication mechanism more explicit and testable; and the use of FastAPI's dependency injection system via Depends, which cleanly separates the authentication concern from the business logic in each protected endpoint. Additionally, the enhancement addressed four bugs present in the original implementation: an undefined variable reference in the register controller that would crash the server on a failed user save, a logically unreachable JWT header validation check, improper response chaining after sendStatus in the original routes, and a semantic error in the trips list endpoint that returned 200 with an empty array rather than 404 when no trips existed in the database.

## Course Outcome Alignment

This enhancement was planned to address Course Outcome 4: demonstrating an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals. The outcome has been met through the deliberate selection of FastAPI as the target framework, which is a modern, production-grade Python web framework with native support for asynchronous operations, automatic OpenAPI documentation generation, and type-safe request validation. These qualities represent genuine improvements over the original Express implementation in terms of maintainability, clarity, and developer experience.

No updates to the outcome-coverage plan are necessary at this stage. The enhancement delivers on its stated objective without scope creep, and the remaining two enhancements, server-side filtering and sorting on the trips endpoint and migration from MongoDB to PostgreSQL, remain aligned with Outcomes 3 and 5 respectively, as planned.

## Reflection on the Enhancement Process

The process of completing this enhancement was more instructive than the original development of the artifact, largely because rewriting existing code with a clear specification forces a level of deliberate decision-making that greenfield development rarely requires. Every structural choice, whether to collapse the routes and controller files into a single router module, how to handle the ObjectId serialization issue that pymongo surfaces when FastAPI attempts to encode MongoDB documents, how to replicate the PBKDF2-based password hashing using Python's hashlib rather than Node's crypto module, required understanding not just what the original code did, but why, and whether that rationale translated cleanly to the new environment.

The most challenging aspect of the enhancement was the authentication layer. FastAPI's dependency injection model is conceptually cleaner than Express middleware, although it required a more careful read of the documentation than anticipated, particularly around how FastAPI maps HTTP header names to Python parameter names and how PyJWT's decode behavior differs from the original jsonwebtoken library's verify callback pattern. The ObjectId serialization issue, where pymongo returns MongoDB's internal ObjectId type which FastAPI cannot automatically convert to JSON, was also a practical lesson in the difference between a framework that handles impedance mismatches silently and one that surfaces them explicitly. FastAPI's behavior here, while initially disruptive, is ultimately the more defensible design.

The enhancement also reinforced the importance of testing against a real data layer rather than mocked dependencies. Several issues that would not have surfaced in unit tests, including the datetime.date serialization failure on insert and the Pydantic model immutability that prevented setting hash and salt fields before persisting the user, only became apparent when running the complete request lifecycle against a live MongoDB instance. This underscores a broader principle: integration testing catches a different and often more consequential class of bugs than unit testing alone, and building the habit of testing end-to-end early in development is worth the setup cost.
