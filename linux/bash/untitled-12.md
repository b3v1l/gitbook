# Common

## **date conversion** <a id="date-conversion"></a>

`date -d @unix_timestamp`

## **cd in weird directory** <a id="cd"></a>

`cd -- "-= STUPID USER INPUT HERE =-"`

## Check process & i/o <a id="check-process-io"></a>

`grep read_bytes /proc/[0-9]*/io | sort -nrk2 | head -5`

