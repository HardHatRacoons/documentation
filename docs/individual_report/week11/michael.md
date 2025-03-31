# Michael Week 11 Individual Report

**Team**: HardHatRacoons (Construction Blueprint)

**Date**: March 31, 2025

## Current Status

### What did _you_ work on this past week?

| Task                              | Status    | Time Spent | 
| --------------------------------- | --------- | ---------- |
| Rewrite of DBSCAN algo | Complete | 2 Hour |
| Parallel Processing of pages | Complete | 3 Hours |
| Padding of convex hull | Complete | 2 Hour |
| JSON output of cluster boundries | Complete | 1 Hour |
| CI/CD tests coverage report on Github Actions | Complete | 1 Hour |

*Include screenshots/diagrams/figures/etc. to illustrate what you did this past week.*
![backend_coverage](./images/backend_coverage.png)
![predictions json output](./images/predictions_json.png)

### What problems did you run into? What is your plan for them?
Multi Processing worked a bit jank on Windows compared to linux. We found a fix but have to keep an eye out on this when porting to the lambda function.
The algorithm can take a while when pages have excess shading, I have an idea on how to filter out colored shading in pdfs.

### What is the current overall project status from your perspective? 
We are on track. It is mostly piecing together the frontend, our algorithm, and vector team's algorithm.

### How is your team functioning from your perspective?
Team is working well together.

### What new ideas did you have or skills did you develop this week?
I now know how to have python coverage reports with GitHub Actions, and do parallel processing in Python.

### Who was your most awesome team member this week and why?
Lucy for making cool graphs.

## Plans for Next Week

*What are you going to work on this week?*
Handle colored shading in pdfs.
Migrate the algorithm to a lambda function to integrate with frontend.
