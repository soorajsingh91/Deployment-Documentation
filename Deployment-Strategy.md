Part 1: Deployment Strategy

Git Tags: Overview and Differences from Branches
Git Tags:
•	Definition: Git tags are references pointing to specific commits, typically used to mark important milestones or releases.
•	Types:
    Lightweight tags: Simple pointers to commits.
o	Annotated tags: Include additional metadata such as the tagger’s name, email, date, and a message.
•	Difference from Branches: Tags are immutable fixed points in the repository's history, unlike branches which are movable pointers that change as new commits are added.

Use of Git Tags in Deployment Management:
1.	Marking Releases:Tags are used to mark release points (e.g., v1.0, v1.2), helping to identify specific versions of the code deployed to production.
2.	Rollback Strategy:Tags facilitate easy rollbacks to previous stable versions in case of deployment issues.
3.	Continuous Integration and Deployment (CI/CD): CI/CD pipelines can be configured to trigger deployments based on tags, ensuring only tagged commits (e.g., release tags) are deployed to production.

Steps to Ensure Stable Deployment:
•	Feature Branch Workflow: Each developer works on their own feature branch, which is regularly merged into a 'develop' branch after code reviews and testing.
•	Tagging for Releases: Once features are ready and tested on the 'develop' branch, merge it into the 'main' branch and create an annotated tag (e.g., git tag -a v1.0 -m "Release version 1.0").
•	Deployment Pipeline: Set up CI/CD pipelines to automatically deploy tagged commits from the 'main' branch to production, ensuring stages for building, testing, and deploying the code are included.
•	Pre-Deployment Testing: Before deploying to production, deploy the tagged commit to a staging environment and conduct thorough testing to identify any potential issues.
•	Monitoring and Rollback: Monitor the production environment post-deployment. If issues arise, rollback using the previous stable tag (e.g., git checkout v0.9).

Example Scenario:
1.	Developing a Feature: Developer A completes a feature on a branch called feature/awesome-feature. After code review, the feature branch is merged into develop.
2.	Preparing for Release:
o	Merge develop into main once all features for the release are merged and tested.
o	Tag the release on main: git tag -a v1.1 -m "Release version 1.1".
3.	Deployment:
o	The CI/CD pipeline detects the tag v1.1 and triggers the deployment process, deploying the code to the staging environment for final testing.
o	Post successful tests, the same tagged commit is deployed to production.
4.	Post-Deployment:
o	Monitor the system, and if issues arise, rollback to v1.0 by checking out the previous tag and redeploying (git checkout v1.0).
