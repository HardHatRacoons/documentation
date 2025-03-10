# Team Weekly Report #4

**Team**: HardHatRacoons (Construction Blueprint)

**Week**: 7

**Members**: Emmie Teng, Stella Yang, Lucy Zhang, Michael McCarthy, Christopher Kelley 


## Status Report

In the backend, we added testing and documentation for our algorithm. We improved the page identification algorithm to around 80% accuracy. We ran into some problems regarding the standardization of blueprint pdfs and what exactly should be annotated. Over this next week, we plan to further improve the page identification algorithm and the cluster identification algorithm. If the algorithmic strategy to page identification doesn’t work, we plan to explore alternate methods like machine learning. Also, we plan to add padding to convex hulls.

In the frontend, the file upload system was successfully implemented, and React tests now cover 70% of the main application. Additionally, the Google OAuth client was created, and its integration with AWS Amplify is nearing completion with just protective routes missing. Over the next week, we plan to implement file display and protective routes. Currently, the user upload feature is allowing guests to read and write, once the authentication changes are pushed, we will also have to update the upload feature to only allow authenticated users to write to specific s3 buckets. We may also want to figure out a file storage structure for storing each user’s file and preventing them from accessing each other’s files. Lastly, we aim to improve the overall coverage of the React tests. 


## Current Status

### What did the team work on this past week?

| Task                                     | Task Lead     | Status      | Notes                                    |
| ---------------------------------------- | ------------- | ----------- | ---------------------------------------- |
| Preparing backend for AWS Lambda         | Michael       | In Progress |                                          |
| File Upload                              | Emmie         | Complete    |                                          |
| Write React Tests                        | Lucy          | Complete    | Currently at 75% coverage on main        |
| Add New Task to Taiga                    | Stella        | Complete    |                                          |
| Create Google OAuth Client               | Stella        | Complete    |                                          |
| Connect Google OAuth to Amplify          | Stella        | In Progress | Nearly done, just have to protect routes |
| Improve page identification algorithm    | Chris         | In Progress | About 80% accurate                       |
| Improve cluster identification algorithm | Chris         | In Progress |                                          |
| Work on backend Documentation            | Michael/Chris | Complete    |                                          |
| Backend Unit Tests                       | Michael       | Complete    | Update and and to as needed.             |
| Implement File Display                   | Emmie         | In Progress | Waiting for auth                         |
| Set up Bucket and Database               | Michael       | Closed      | No longer need it                        |
| Create mock graphs for metric view       | Lucy          | Complete    | Basic view                               |
| Create mock tables table view            | Lucy          | Complete    | Basic view                               |
| Set up database server                   | Stella        | Closed      | No longer need it                        |

### What feedback has the team receieved?
| From Whom | Feedback            | Next Steps |
| --------- | ------------------- | ---------- |
| Sponsor   | Convex Hull is good |            |

### Are any resources needed? If so, what?
- Will likely need funding for S3 bucket soon. We are about to hit the free tier limit, and afterwards it will be $0.01 per 1k requests.

## Plans for Next Week

| Task                                     | Task Lead | Notes |
| ---------------------------------------- | --------- | ----- |
| Preparing backend for AWS Lambda         | Michael   |       |
| Add padding to Convex Hull               | Michael   |       |
| Implement File Display                   | Emmie     |       |
| Beautify File Display                    | Emmie     |       |
| Improve page identification algorithm    | Chris     |       |
| Improve cluster identification algorithm | Chris     |       |
| Protect Routes                           | Stella    |       |
| Improve Frontend Test Coverage           | Lucy      |       |



