# Team Weekly Report

**Team**: HardHatRacoons (Construction Blueprint)

**Week**: 8

**Members**: Emmie Teng, Stella Yang, Lucy Zhang, Michael McCarthy, Christopher Kelley 


## Status Report

The team has completed most of the goals that we set out to finish for this sprint. Stella completed linking our app with Google OAuth through AWS lambda and protected routes that should not be accessible when not logged in. She also finished file routing. Emmie finished the file upload and file displaying and assisted with authentication. Chris worked on improving the algorithms in the backend and Michael successfully set up AWS Lambda to run our algorithms on files and put them in the right folder. Lucy improved frontend test coverage to ~93%. Authentication was difficult to set up as it involved linking two 3rd party providers, which was challenging. Chris also faced difficulties in edge cases and runtime during improving the algorithms. Lucy had trouble with mocking and authentication for the coverage testing. 

For the next week, the team plans to further improve the algorithms in the backend. The team also seeks to display annotations on hover and populate the metric and table view. The team will also clean up some of the CI/CD by adding more tests and protections. The team will also add thumbnails for files and organize the documentation for the project. Lastly, if there is bandwidth, the team will improve testing and coverage.

## Current Status

### What did the team work on this past week?

| Task                                     | Task Lead | Status   | Notes    |
| -----------------------------------------| --------- | -------- | -------- |
| Preparing backend for AWS Lambda         | Michael   | Complete |          |
| Add padding to Convex Hull               | Michael   | Complete |          |
| Implement File Display/Upload            | Emmie     | Complete |          |
| Beautify File Display/Upload             | Emmie     | Complete |          |
| Improve page identification algorithm    | Chris     | Complete |          |
| Improve cluster identification algorithm | Chris     | Complete |          | 
| Protect Routes                           | Stella    | Complete |          |
| Authentication                           | Stella    | Complete |          |
| File Routing                             | Stella    | Complete |          |
| Improve Frontend Test Coverage           | Lucy      | Complete | ~93% now | 

### What feedback has the team receieved?

| From Whom   | Feedback                                        | Next Steps         |
| ----------- | ----------------------------------------------- | ------------------ |
| Instructors | Good on testing, documentation, and deployment. | Need more features |

### Are any resources needed? If so, what?
We definitely need money because we surpassed the free tier ($0.02).

## Plans for Next Week

| Task                                        | Task Lead       | Notes                           |
| ------------------------------------------- | --------------- | ------------------------------- |
| Display annotation on hovers                | Lucy            |                                 | 
| Convex Hull Padding                         | Michael         |                                 | 
| Fix bug in convex hull algo                 | Michael         | *Top left sometimes not in hull | 
| Python coverage report                      | Micahel         |                                 | 
| Metric/table view loading actual data       | Lucy            |                                 | 
| CI prettier/testing                         | Stella          |                                 |
| Thumbnails for files                        | Emmie           |                                 | 
| Documentation organizing (frontend, report) | Emmie           |                                 |
| Edge cases for page identification          | Chris           |                                 | 
| Edge cases for cluster identification       | Chris           |                                 | 
| Improve cluster algo speed                  | Chris & Michael |                                 |


