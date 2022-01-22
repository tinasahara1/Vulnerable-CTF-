# curl 

curl -X GET "https://example.com/endpoint/?api_key=abcdef12345" 

- -H ‘content-type: application/json’ 

- -H 'Authorization: Bearer abcdef12345...' 

- -H 'Connection: keep-alive' 

- -H 'Upgrade-Insecure-Requests: 1'

- -H 'Connection: keep-alive'

- -H 'Content-Type: application/www-x-form-urlencoded'

- -d ‘ {“api_key”: "abcdef12345”}  =>json

- --data-raw 'username=guest&password=guest' 

- -d ('username=guest&password=guest') =>www-x-from


# TOOL NIKTO >>>LINUX
cd nikto/program

- ./nikto.pl -h example.com
- whatweb -a 1 <URL> #Stealthy
- whatweb -a 3 <URL> #Aggresive
- webtech -u <URL>
