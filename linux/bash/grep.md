# grep

## grep

\
**Nombre de ligne suivante (ie 15 lignes en plus):**\
\
grep -A 15 search file\
\
\
**Remove a line with a chosen char :**\
\
grep -v 'polo' file\
\
**Remove multi lines containing multi char :**\
\
egrep -v '(red|white|blue)' file\
\
\
**Multiple patterns:**\
\
grep 'pattern1\\|pattern2' filename\
\
**Grep backslash stuff ...**\
\
looking for JD\\:\
\
cat Users.txt |grep 'JD\\\\'\
\
\
**grep everything between quotes :**\
\
\
grep -oP '".\*?"'\
\
\
**grep only digit 1 between 5 number :**\
\
grep -oP '\d{1,5}/closed'\
\
\
**grep binary + regular expression + line before / after**\
\


```
grep -a -B2 -A2 ‘[a-z0-9]\{32\}' 
```

\=> tous les characteres et chiffres d'une longueur de 32 chars.\
\
\
**Grep ports from exported nmap :**\
\
\
&#x20;grep -oP " \[\d]{1,5}/" 10.11.1.230.gnmap |sed 's/\[/ ]//g' |tr "\n" ","\
\
80,135,139,445,3389,3573,49152,49153,49154,49155,49156,49157,\
\
\
**Remove space and comment :**\


```
less /etc/apache2/apache2.conf | grep -v "^#\|^$"

```
