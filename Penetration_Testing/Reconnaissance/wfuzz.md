# Wfuzz
***

## Insallation
```
pip3 install wfuzz
```

### Usage
```
wfuzz -c -z file,/usr/share/wordlists/dirb/big.txt --hc 404 --hw 0 http://IP:80/FUZZ/note.txt
  -c shows the output in color
  -z specifyes what will replace FUZZ
  --hc don't show certain http response codes
  --hw don't show word
```

