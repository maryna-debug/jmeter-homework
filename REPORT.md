# JMeter Homework Report

## Environment
- OS: Windows
- JMeter: 
- Java: 
- SUT: Docker app QA Pro REST App
- Base URL: http://localhost:8080

## Endpoints
- GET /characters
- GET /character/{id}
- POST /character

## Correlation
For GET /character/{id} the id value is extracted from the response of GET /characters using JSON Extractor and reused in the next request.

## Scenarios

### 1) Concurrency Thread Group (short)
- Users: 30
- Goal: short concurrency test of main endpoints

### 2) Stepping Thread Group
- Users: up to 30 (step load)
- Goal: gradual load increase and stability observation

### 3) Concurrency Thread Group (long run)
- Users: 15
- Duration: 30 minutes
- Result file: results/aggregate_longrun_30min.csv
- JTL file: results/results_htmlrun.jtl
- HTML report: html-report/index.html

## Findings
- GUI tests: Error 0.00%
- HTML report: minor non-HTTP connection errors in local Docker environment:
  - org.apache.http.NoHttpResponseException (localhost:8080 failed to respond)
  - Total errors: 8 out of 4929 requests (~0.16%)
  - GET /character/{id}: 6
  - POST /character: 2
