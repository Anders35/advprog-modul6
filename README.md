# Tutorial 6

## Commit 1 Reflection Notes

`handle_connection` function reads the incoming HTTP request line-by-line using `BufReader` and collects the request headers until it encounters an empty line. Running the program and accessing the server via a browser revealed the structure of an HTTP request, including details such as the request method (`GET`), the requested resource (`/`), headers like `User-Agent`, and other metadata. 