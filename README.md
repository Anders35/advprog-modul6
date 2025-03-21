# Tutorial 6

## Commit 1 Reflection Notes

`handle_connection` function reads the incoming HTTP request line-by-line using `BufReader` and collects the request headers until it encounters an empty line. Running the program and accessing the server via a browser revealed the structure of an HTTP request, including details such as the request method (`GET`), the requested resource (`/`), headers like `User-Agent`, and other metadata. 

## Commit 2 Reflection Notes

![Commit 2 screen capture](/assets/images/commit2.png)

The new `handle_connection` function now not only read incoming HTTP requests but also respond with a valid HTTP response. It constructs a proper HTTP response, starting with the status line `"HTTP/1.1 200 OK"`, indicating a successful request. The response body is read from `hello.html` using `fs::read_to_string`, and its length is determined to set the `Content-Length` header. Finally, the response is formatted and sent back to the client using `stream.write_all`.