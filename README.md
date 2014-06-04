hashID
======

Identify the different types of hashes used to encrypt data and especially passwords.

This tool replaces [hash-identifier](http://code.google.com/p/hash-identifier/), which is outdated!
 
hashID is a tool written in Python 3.x which supports the identification of over 185 unique hash types using regular expressions.
A full list of supported hashes is found [here](hashinfo.xlsx).    
It is able to identify a single hash, parse a file or read files in a directory and identify the hashes within them.    
Altough hashID is written in Python 3.x it should also work with Python 2.x except for the file and directory analyze.

There is also a [nodejs](js) version of hashID available which is easily set up to provide online hash identification.  

*Note: When identifying a hash on *nix operating systems use single quotes to prevent interpolation*

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
$ python3 hashid.py INPUT [-m] [--help] [--version]
```

| Parameter        				 | Description      				  				  |
| :----------------------------- | :------------------------------------------------- |
| input					      	 | string or filename to analyze 					  |  
| -m, --mode	              	 | include corresponding hashcat mode in output		  |
| --help	    				 | show this help message and exit 					  |
| --version                   	 | show program's version number and exit			  |


Screenshot
------
```
$ python3 hashid.py $P$8ohUJ.1sdFw09/bMaAQPTGDNi2BIUt1
Analyzing '$P$8ohUJ.1sdFw09/bMaAQPTGDNi2BIUt1'
[+] Wordpress ≥ v2.6.2
[+] Joomla ≥ v2.5.18
[+] PHPass' Portable Hash

$ python3 hashid.py -m ecf076ce9d6ed3624a9332112b1cd67b236fdd11:17782686
Analyzing 'ecf076ce9d6ed3624a9332112b1cd67b236fdd11:17782686'
[+] Redmine Project Management Web App [Hashcat Mode: 7600]
[+] SMF ≥ v1.1 [Hashcat Mode: 121]

$ python3 hashid.py hashes.txt
--File 'hashes.txt'--
Analyzing '*85ADE5DDF71E348162894C71D73324C043838751'
[+] MySQL5.x
[+] MySQL4.1
Analyzing '$2a$08$VPzNKPAY60FsAbnq.c.h5.XTCZtC1z.j3hnlDFGImN9FcpfR1QnLq'
[+] Blowfish(OpenBSD)
[+] Woltlab Burning Board 4.x
[+] bcrypt
--End of file 'hashes.txt'--

$ python3 hashid.py folder/*.txt
--File 'hashes.txt'--
Analyzing '*85ADE5DDF71E348162894C71D73324C043838751'
[+] MySQL5.x
[+] MySQL4.1
Analyzing '$2a$08$VPzNKPAY60FsAbnq.c.h5.XTCZtC1z.j3hnlDFGImN9FcpfR1QnLq'
[+] Blowfish(OpenBSD)
[+] Woltlab Burning Board 4.x
[+] bcrypt
--End of file 'hashes.txt'--
--File 'hashes.txt'--
Analyzing '{smd5}01234567$yOImZPvBC8dg1HjGYfH7j.'
[+] AIX(smd5)
Analyzing 'crypt1:fnd+8xl+U1E=:Wc30H8MPgAc='
[+] Clavister Secure Gateway
--End of file 'hashes.txt'--
```

Contribute
------
Contributing to this project can be done in various ways:
* Add currently unsupported hash types
* Change/Fix/Enhance existing regular expression
* Provide reading resources on the specific hash types (see "Resources" section in [hashinfo.xlsx](hashinfo.xlsx))
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
* http://openwall.info/wiki/john/sample-hashes
* http://hashcat.net/wiki/doku.php?id=example_hashes