# api-test-runner

An API test framework. It takes one config file, and do 3 things base on it:

1. Run all the test automatically.
2. Generate a human friendly API documentation page, which is also the Web UI to inspect test result and do manual test.
3. Setup a local server that handles request and responses with mocked data (if specified).

## Why?

To deal with API, usually we need 3 things:

1. API doc
2. API test
3. A local server that mocks API behaviors to ease frontend development

But it's a pain in the ass to maintain these 3 things at the same time. They should be the same thing inherently. This is the problem we're solving.
