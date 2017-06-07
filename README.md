# URI resolver tester
An in-browser test suite for JavaScript-based URI resolver libraries

The main "app" is uri_tests.html.
To run the tests, just load that document in a web browser.

The test suite uses JavaScript to:

1. Load several JavaScript functions to be tested. Each function implements the
   RFC 3986/STD 66 section 5 algorithm to resolve a URI reference to absolute form.
2. Subject those functions to a battery of test cases.
3. Output the results in an HTML table.

One of the functions tested is my own code (uri_funcs.js) which implements the "remove_dot_segments" portion of the algorithm by using "two segment stacks rather than strings". This is something the spec suggests applications may do for efficiency. I don't know if it is actually more efficient; I just did it for the novelty. I originally wrote this code in Python; see absolutize() in [Uche Ogbuji's Amara](https://github.com/uogbuji/amara3-iri/blob/master/lib/iri.py) library. The test suite itself is based on Python [code I co-wrote](https://web.archive.org/web/20060514093956/http://cvs.4suite.org/viewcvs/4Suite/test/Lib/test_uri.py?view=markup) for Amara's predecessor, 4Suite XML.

The other functions to test are imported from other people's libraries, although I may have modified them slightly just to get them to run in a browser and integrate with the test suite.

As of mid-2017, Tim Berners-Lee's library is hosted on a server at MIT which still does not have HTTPS service configured properly. So for now, I am just loading that file via regular HTTP, which means your browser may complain about mixed/insecure content. For example, in Chrome, if you load uri_tests.html via HTTPS, then the tests won't run until you click on the shield icon in the omnibar and allow the insecure content to load.

The test suite currently does not test or support the optional normalization steps allowed by section 6 of the spec.
