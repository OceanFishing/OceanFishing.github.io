---
layout: page
title: Original Artifact
---

Travlr Getaways is a full-stack travel booking application I built in CS 465 using the MEAN stack: MongoDB, Express, Angular, and Node.js. Customers browse available trips through an Angular single-page application, while administrators manage trip data through a separate Angular admin panel. The backend is a REST API built with Express and Node.js that authenticates with JSON Web Tokens and persists data in MongoDB through Mongoose. The application is the single artifact enhanced throughout this portfolio.

In its original form the application stored its data as two independent document collections, one for trips and one for users, with no enforced relationship between them and only minimal constraints on the shape of the data. It worked, but it left almost all responsibility for data integrity in the application code rather than the database, validated little of what it received, and contained several defects that the code review identifies in detail.

**Original code:** [cs499-capstone, `main` branch](https://github.com/OceanFishing/cs499-capstone/tree/main)

The three enhancements that follow each modify this baseline. The [code review]({{ '/code-review/' | relative_url }}) walks through the original functionality and the specific weaknesses that motivated each change.
