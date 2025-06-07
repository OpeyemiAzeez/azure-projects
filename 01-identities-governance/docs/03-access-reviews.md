# Access Reviews in Azure AD

## Objective
This section explains how to configure and manage Access Reviews in Azure Active Directory (Azure AD), now part of Microsoft Entra, to ensure that users have appropriate access to resources over time.

---

## Prerequisites

▪	Azure AD Premium P2 license
▪	Global Administrator, User Administrator, or Privileged Role Administrator role
▪	Target groups, roles, or applications already set up
▪	Access to the Azure Portal

---

## Step 1: Navigate to Access Reviews

1.	Go to the Azure Portal.
2.	Search for Azure AD or Microsoft Entra ID.
3.	Under Identity Governance, select Access reviews.

---

## Step 2: Create a new Access Review

1.	Click + New access review.
2.	Choose one of the following review types:
	Users in a group
	Access to an application
	Assignments to Azure AD roles
3.	Select the specific group, app, or role to review.
4.	Set the Review name and optionally add a description.
5.	Define the Reviewers:
	Group owners
	Selected users
	Self-review
6.	Set the Recurrence (One time, Weekly, Monthly, Quarterly, etc.).
7.	Configure Auto-apply results (e.g., remove access if not approved).
8.	Click Create.



![Access Review](images/access-review.png)
---

## Step 3: Monitor and Take Action on Reviews

1.	Once created, reviews appear in the Access reviews list.
2.	Reviewers will be notified via email to perform the review.
3.	Admins can check progress and see who completed or skipped reviews.
4.	After the review period, results can be applied automatically or manually.

---
