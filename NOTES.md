# Notes

## Summary of Changes

I found issues related to searching/filtering and task ordering.

The searching and filtering issue was in the backend SQL query in the `TaskRepository`. The conditions in the `WHERE` clause were not properly grouped with parentheses.

I fixed this by adding parentheses around the title and description search conditions.

I also changed the ordering from `ORDER BY created_at DESC` to `ORDER BY id ASC` so that tasks are displayed in ID order.

## What I Chose Not to Change

I did not make unrelated UI or architectural changes because they were outside the scope of the identified issues.

I also did not change the existing pagination logic because it was working as expected during my testing.

## Biggest Remaining Risk

One remaining risk is that invalid pagination values are not properly validated in the backend. 

For example, if a negative value for `page` is received, the pagination calculation could cause an exception. Currently, the frontend initializes the page with `useState(1)`, but the backend should still validate request parameters.

## Tools / AI Used

I used Postman to test the backend API directly and verify the API responses before checking the same behavior through the frontend. I also used Postman after making changes to the backend logic to verify that the changes produced the expected results.

I used ChatGPT to help me understand and identify the problem in the SQL logic. I had a doubt about the query but was initially unable to identify the exact issue. I then tested and verified the behavior myself using Postman, confirmed the issue, applied the fix, and tested the API again before verifying the result through the frontend.