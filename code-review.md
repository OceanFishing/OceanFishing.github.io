---
layout: page
title: Code Review
---

Before implementing any enhancement, I recorded a code review of the original Travlr Getaways application. The review establishes a baseline by walking through the existing functionality, analyzing the code for problems across structure, logic, efficiency, security, testing, and documentation, and then describing the planned enhancement for each of the three categories. The written summary below accompanies the recording.

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; margin-bottom: 1rem;">
  <iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
    src="https://www.youtube.com/embed/Ij8Gz8OKqjo"
    title="CS 499 Code Review"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen></iframe>
</div>
---

## Code Review Summary

Code review is a structured process in which a developer systematically examines source code to identify issues related to correctness, structure, security, efficiency, and documentation before that code is finalized or deployed. It is a critical practice in computer science because it catches bugs before they reach production, enforces consistent coding standards, and ensures that logic is understandable to someone other than the original author. Best practices include using a checklist-driven approach to ensure categories like structure, defensive programming, and security receive deliberate attention, keeping reviews focused on specific concerns rather than evaluating everything at once, and treating documentation as seriously as logic. Code review should occur before code is merged or deployed, as reviewing after the fact significantly limits the ability to act on findings without introducing additional risk. In this capstone, conducting the review prior to implementing enhancements established a clear baseline of what exists and what needs to improve, so that each enhancement could be designed with those findings directly in mind.

To record the code review I used OBS Studio. My approach to the script was organized around the three enhancement categories, each following the same internal structure: a walkthrough of what the relevant code does, a systematic analysis of identified problems, and a description of the planned enhancement. I was intentional about keeping the functionality description and problem analysis as separate sections within each category, and I tried to be thorough in my review process by grounding every claim in a specific visible line of code rather than a general impression, which was particularly important given that my familiarity with this codebase required careful examination rather than a surface-level pass.
