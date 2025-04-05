# Customer Churn Detection: Tracking User Activity Decline

## Project Overview
This project identifies at-risk customers who are likely to stop using the service by analyzing drops in their platform activity.

## How It Works
- **Active User Definition**: A user is considered "active" if they have **>500 visits/month** (averaged over 3 months).
- **At-Risk Flag**: A user is flagged if their visits in the **last 30 days** drop by **>50%** compared to their previous 3-month average.
- **Action**: The Customer Success Team contacts these users proactively to prevent churn.

## Database Structure
### Tables

#### 1. `Companies`
Stores company information.
- `id` (Unique identifier)
- `name` (Company name)

Example data:
| id | name      |
|----|-----------|
| 1  | Amazon    |
| 2  | Microsoft |
| 3  | Google    |

#### 2. `Companys_members`
Tracks which members belong to which companies.
- `member_id` (Unique user identifier)
- `company_id` (References Companies.id)
- `name` (Member name)
- `email` (Member email)
- `is_owner` (TRUE/FALSE if member owns company account)

Example data:
| member_id | company_id | name  | email            | is_owner |
|-----------|------------|-------|------------------|----------|
| 1         | 3          | Mark  | mark@google.com  | TRUE     |
| 2         | 1          | Sam   | sam@amazon.com   | FALSE    |
| 3         | 1          | David | dav@amazon.com   | TRUE     |

#### 3. `Members_visits`
Logs every time a member uses the platform.
- `visit_id` (Unique visit identifier)
- `member_id` (References Companys_members.member_id)
- `created_at` (Timestamp of visit)

Example data:
| visit_id | member_id | created_at          |
|----------|-----------|---------------------|
| 1        | 1         | 8/15/2021 16:46:07  |
| 2        | 2         | 8/15/2021 16:46:18  |
| 3        | 1         | 8/15/2021 16:46:20  |
| 4        | 3         | 8/15/2021 16:46:21  |

