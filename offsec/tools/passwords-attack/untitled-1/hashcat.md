# hashcat

## hashcat

### List hashes

```csharp
hashcat --example-hashes
```

#### Example

Attack mode : `-a X`

Dictionary \(-a 0\) – Reads from a text file and uses each line as a password candidate

Combination \(-a 1\) – Like the Dictionary attack except it uses two dictionaries. Each word of a dictionary is appended to each word in a dictionary.

Bruteforce -a 3 – Try all combinations in a given keyspace. It is effectively a brute-force on user specified character sets.

Hybrid \(-a 6 and -a 7\) – A combination of a dictionary attack and a mask attack.

```csharp
./hashcat -a 3 -m 0 hashes.txt  ?u?l?l?l?d?d?d?d
```

#### mask

```text
?l = abcdefghijklmnopqrstuvwxyz
?u = ABCDEFGHIJKLMNOPQRSTUVWXYZ
?d = 0123456789
?h = 0123456789abcdef
?H = 0123456789ABCDEF
?s = «space»!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
?a = ?l?u?d?s
?b = 0x00 – 0xff
```

### Examples

{% hint style="info" %}
use --show to retrieve a cracked password

use --force on vm or hw issues
{% endhint %}

### Net-NTLMv2 \(via responder\)

```csharp
sudo hashcat -m 5600 /home/nyws/test/mssql.hash /usr/share/wordlists/rockyou.txt --force 
```

### Kerberos \(SPN\)

```csharp
hashcat -m 13100 /tmp/5 /usr/share/wordlists/rockyou.txt  --force
```

### NTLM hash

```csharp
hashcat -m 1000  /usr/share/wordlists/rockyou.txt --force hash.txt
```

