# Team Weekly Report #7

**Team**: HardHatRacoons (Construction Blueprint)

**Week**: 10

**Members**: Emmie Teng, Stella Yang, Lucy Zhang, Michael McCarthy, Christopher Kelley

## Status Report

This week, the team has made significant steps towards the completion of the project. In the frontend, graphs have been made to display information given in csv/json format about the data. In the backend, the time to process a pdf document has been successfully cut down from the initial amount to merely a couple of seconds per document (except for documents with large amounts of shading).

The team has faced a couple of challenges this week. For one, frontend testing has been difficult as always. It can be hard to mimick user behavior in a headless browser and write all-encompassing test cases. Improving the runtime of the backend has also proven difficult at times, until new ideas are had and tested.

The team has a couple of goals to hit in the next week. The team seeks to integrate the backend algorithm with the frontend app as well as improve the backend algorithm even further to deal with the edge cases mentioned briefly above. The backend team also seeks to establish better benchmarks and testing for the backend. The frontend team seeks to add more professional and better quality styling to the website as well as different views for different groups of users.

## Current Status

### What did the team work on this past week?

| Task                                        | Task Lead       | Status      | Notes                               |
| ------------------------------------------- | --------------- | ----------- | ----------------------------------- |
| Algorithm Profiling                         | Michael & Chris | Not Started | Pushed to next sprint               |
| Convex Hull Padding                         | Michael         | Complete    |                                     |
| Metric View (make graphs and populate)      | Lucy            | Complete    | includes testing                    |
| Thumbnail image for cards                   | Emmie           | Complete    |                                     |
| Write test cases for delete and thumbnail   | Emmie           | Complete    |                                     |
| Show all files in Gallery                   | Emmie           | Complete    |                                     |
| Search bar for file in gallery              | Stella          | Complete    |                                     |
| Keep test coverage at 100%                  | Stella          | Complete    |                                     |
| Edge cases for page identification          | Chris           | Complete    |                                     |
| Edge cases for cluster identification       | Chris           | Complete    |                                     |
| Improve Algorithm Runtime                   | Michael         | Complete    | <1 min on average (without shading) |
| Algorithm Coverage Report w/ GitHub Actions | Michael         | Complete    |                                     |

### What feedback has the team receieved?

| From Whom   | Feedback                                                                    | Next Steps                                                       |
| ----------- | --------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Dr. Ritchey | Profile our code to understand what parts of our code is taking a long time | Improved upon running speed and have past versions to compare to |

### Are any resources needed? If so, what?

Currently no resource needed. We are at \~$0.05 total in AWS S3 bucket billing ($0.02 per sprint).

## Plans for Next Week

| Task                                     | Task Lead       | Notes                         |
| ---------------------------------------- | --------------- | ----------------------------- |
| Algorithm Profiling                      | Michael & Chris |                               |
| Integrate algorithm to run with app      | Michael & Chris |                               |
| Handle pdfs with excess shading          | Michael         | Starting with colored shading |
| Improve coverage for backend tests       | Michael & Chris |                               |
| Improving visual front end components    | Emmie           | Fonts, colors, spacing, etc   |
| Admin view for adding users              | Emmie           |                               |
| Admin view of all files                  | Emmie           |                               |
| Darkmode Styling                         | Lucy            |                               |
| Hover over blueprint for summarized data | Stella          |                               |
