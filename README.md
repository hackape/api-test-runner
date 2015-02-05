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

## Draft Config File Options

### Request Config Options

<table class="table table-bordered table-stripped">
              <thead>
                <tr>
                  <th>Key</th>
                  <th>Type</th>
                  <th>Description</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>absUrl</td>
                  <td>String</td>
                  <td> 
                    <p>Absolute URL used by this request. This is the actual URL each request eventually uses. </p>
                    <p>If "absUrl" is not specified, it'll be composed internally by simple string concatenation: <code>absUrl = host + prefix + url</code>. </p>
                    <p>if specified, it'll override any URL relevent configs.</p>
                  </td>
                </tr>
                <tr>
                  <td>title</td>
                  <td>String</td>
                  <td>Optional title to the test, </td>
                </tr>
                <tr>
                  <td>description (des)</td>
                  <td>String</td>
                  <td> 
                    <p>Optional description to this test. This, along with "title" above, will compiles to a description section to this test in the Web UI.</p>
                    <p>You can also use "des" for short instead.</p>
                  </td>
                </tr>
                <tr>
                  <td>url</td>
                  <td>String</td>
                  <td> 
                    <p>URL (or URL pattern) to this request. <span class="label label-primary">Highest Priority</span></p>
                    <p>Route params can be declared with "/:param" syntax inside URL, these params will be identified, and will be supplied with actual value in a request via "routeParams" (see below)</p>
                  </td>
                </tr>
                <tr>
                  <td>routeParams</td>
                  <td>Object</td>
                  <td>Supply route params here.</td>
                </tr>
                <tr>
                  <td>searchParams</td>
                  <td>Object</td>
                  <td>Search params will be URL encoded then appended to URL in form of <code>url?param1=value&amp;<span></span>param2=value</code></td>
                </tr>
                <tr>
                  <td>precedence</td>
                  <td>String, Array</td>
                  <td>Permission configs that will apply to all requests in the test, can be overriden by "permission" in specify <em>request config objects</em></td>
                </tr>
                <tr>
                  <td>method</td>
                  <td>String</td>
                  <td>HTTP request method.</td>
                </tr>
                <tr>
                  <td>headers</td>
                  <td>Object</td>
                  <td>HTTP request headers.</td>
                </tr>
                <tr>
                  <td>body</td>
                  <td>Object, String, Function</td>
                  <td>HTTP request body.</td>
                </tr>
              </tbody>
            </table>
