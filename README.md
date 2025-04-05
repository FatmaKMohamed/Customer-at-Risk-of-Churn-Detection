##Project Description:
This project identifies at-risk customers likely to churn by analyzing drops in their platform activity.

##Key Logic:
- An active user is defined as someone with >500 visits/month over a 3-month period.

- A user is flagged as at-risk if their visits in the last 30 days drop by >50% compared to their previous 3-month average.

- The Customer Success Team uses this data to proactively engage users before they churn.

##Database Schema:
- Companies – Stores company details.

   id, name (e.g., Amazon, Google)

- Companys_members – Tracks members and their company affiliations.

   member_id, company_id, name, email, is_owner (boolean)

- Members_visits – Logs each user’s activity with timestamps.

   visit_id, member_id, created_at
