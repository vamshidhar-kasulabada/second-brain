
# curl

The curl command is a versatile tool for transferring data from or to a server, using protocols like HTTP, HTTPS, FTP, and others. Here’s an explanation of commonly used flags:

## Basic Structure
`curl [options] <URL>`

## -o `<filename>` (or --output)
- Purporse: Saves the output to a specific file.
- Example: `curl -o filename.ext <URL>`
- Use Case: Allows you to specify a filename instead of dumping output to the terminal.


## -O (or --remote-name)
- **Purpose**: Saves the file with its original name from the server.
- Example: `curl -O <URL>`
- Use Case: Useful when you want to keep the original filename provided by the server.

## -L (or --location)
- Purpose: Tells curl to follow redirects.
- Example: `curl -L <URL>`
- Use Case: Necessary if the URL you’re accessing redirects to another location. Without -L, curl will only request the original URL and will stop if a redirect response (like HTTP 301 or 302) is returned.




