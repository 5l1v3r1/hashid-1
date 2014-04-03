hashID
======

Identify the different types of hashes used to encrypt data and especially passwords.

This tool replaces [hash-identifier](http://code.google.com/p/hash-identifier/), which is outdated!
 
hashID is a tool written in Python 3.x which supports the identification of over 175 unique hash types using regular expressions.           
It is able to identify a single hash or parse a file and identify the hashes within it.    
There is also a nodejs version of hashID available which is easily set up to provide online hash identification.  


Install
------
```
sudo apt-get install python3 git
git clone https://github.com/psypanda/hashid.git
cd hashid/python
chmod +x hashid.py
exit
```

Usage
------
```
$ python3 hashid.py INPUT [-f] [-m] [-o OUTFILE] [--help] [--version]
```

| Parameter        				| Description      				  					|
| ----------------------------- | -------------------------------------------------	|
| input					      	| identify given input  		  					|  
| -f, --file 					| enable file analyze     		  					|
| -m, --mode	              	| include hashcat mode in output					|
| -o OUTPUT, --output OUTPUT	| set output filename (default: hashid_output.txt)	|
| --help	    				| show this help message and exit 					|
| --version                   	| show program's version number and exit			|


Screenshot
------
```
$ python3 hashid.py d41d8cd98f00b204e9800998ecf8427e
Analyzing 'd41d8cd98f00b204e9800998ecf8427e'
[+] MD5
[+] MD4
[+] MD2
[+] Double MD5
[+] NTLM
[+] LM
[+] RAdmin v2.x
[+] RIPEMD-128
[+] Haval-128
[+] Tiger-128
[+] Snefru-128
[+] ZipMonster
[+] Skein-256(128)
[+] Skein-512(128)
[+] Domain Cached Credentials
[+] mscash
[+] Domain Cached Credentials 2
[+] mscash2
[+] DNSSEC(NSEC3)


$ python3 hashid.py ecf076ce9d6ed3624a9332112b1cd67b236fdd11:17782686 -m
Analyzing 'ecf076ce9d6ed3624a9332112b1cd67b236fdd11:17782686'
[+] Redmine Project Management Web App [Hashcat Mode: 7600]
[+] SMF ≥ v1.1 [Hashcat Mode: 121]


$ python3 hashid.py hashes.txt -f
Analysing 'home/psypanda/hashes.txt'
Hashes analysed: 259
Hashes found: 231
Output written: '/home/psypanda/hashid_output.txt'
```

Contribute
------
Contributing to this project can be done in various ways:
* Supply new regular expressions (take a look at [hashinfo.xlsx](hashinfo.xlsx) first)
* Change existing regular expression (please provide a resource why the current regex might be wrong)
* Fix anything noted in the "Known issues" section

Known issues
------
* hashID isn't capable of handling piped input at the moment

Credits
------
* Thanks to [sigkill](https://github.com/sigkill-rcode) who helped me numerous times fixing and optimizing the code
* Thanks to [kmulvey](https://github.com/kmulvey) for supplying and maintaining a nodejs version of hashID

Resources
------
* http://pythonhosted.org/passlib/index.html
* http://wiki.insidepro.com/index.php/Algorithms
* http://openwall.info/wiki/john
* http://hashcat.net/wiki/doku.php?id=example_hashes
