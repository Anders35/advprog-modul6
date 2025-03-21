# Tutorial 6

## Commit 1 Reflection Notes

`handle_connection` function reads the incoming HTTP request line-by-line using `BufReader` and collects the request headers until it encounters an empty line. Running the program and accessing the server via a browser revealed the structure of an HTTP request, including details such as the request method (`GET`), the requested resource (`/`), headers like `User-Agent`, and other metadata. 

## Commit 2 Reflection Notes

![Commit 2 screen capture](/assets/images/commit2.png)

The new `handle_connection` function now not only read incoming HTTP requests but also respond with a valid HTTP response. It constructs a proper HTTP response, starting with the status line `"HTTP/1.1 200 OK"`, indicating a successful request. The response body is read from `hello.html` using `fs::read_to_string`, and its length is determined to set the `Content-Length` header. Finally, the response is formatted and sent back to the client using `stream.write_all`.

## Commit 3 Reflection Notes

![Commit 3 screen capture](/assets/images/commit3.png)

First, it extract the request line and compare the requested path. If the path is `/`, the server responds with `HTTP/1.1 200 OK` and serves `hello.html`. Otherwise, it responds with `HTTP/1.1 404 NOT FOUND` and serves `404.html`.

## Commit 4 Reflection Notes

When accessing `/sleep` in one browser tab and `/` in another, I noticed that the second request had to wait for the first one to finish before it could be processed. This happens because the server handles all requests sequentially in a single thread.  

## Commit 5 Reflection Notes

The server is now multithreaded using a ThreadPool that manages 4 worker threads. Each incoming request is assigned to an available thread. Therefore, the server can handle multiple connections simultaneously.