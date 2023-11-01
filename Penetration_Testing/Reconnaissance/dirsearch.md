# DirSearch

## Installation
```
git clone https://github.com/maurosoria/dirsearch.git
cd dirsearch
```
## Executing
```
./dirsearch.py -u -b -w -e -t -r -x -f -o reportName
  -u = URL
  -f force extensions
  -b = request by host name, because dirsearch by default requests by IP.
  -w = path to wordlist
  -e = extensions separated by comma [aspx, php, asp, txt,js, zip, xml]
  -r = recursive
  -t = number of threads
  -x = exclude specific status code separated by comma
  --simple-report = only found paths
  --json-report = json output 
```
