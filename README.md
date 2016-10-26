# awslambda-pycrypto
[Python Cryptography Toolkit (pycrypto)](https://github.com/dlitz/pycrypto) compiled and packaged for AWS Lambda. Because that is a pain to do.

# Setup
Simply download and include the Crypto folder in your project, zip and upload it to Lambda.

# Lambda Example:
Directory structure:
```
* myproject
  - Crypto/
  - lambda_handler.py
```
`lambda_handler.py`:
```python
from __future__ import print_function

from Crypto.Hash import SHA256


def lambda_handler(event, context):
    hash = SHA256.new()
    hash.update('message')
    digest = hash.digest()
    print(len(digest))
    print(repr(digest))
    return
```

Log output:
```
START RequestId: 17e0f272-9b91-11e6-bf2d-f756ae83795f Version: $LATEST
32
'\xabS\n\x13\xe4Y\x14\x98+y\xf9\xb7\xe3\xfb\xa9\x94\xcf\xd1\xf3\xfb"\xf7\x1c\xea\x1a\xfb\xf0+F\x0cm\x1d'
END RequestId: 17e0f272-9b91-11e6-bf2d-f756ae83795f
REPORT RequestId: 17e0f272-9b91-11e6-bf2d-f756ae83795f	Duration: 0.28 ms	Billed Duration: 100 ms 	Memory Size: 128 MB	Max Memory Used: 14 MB	
```
# Disclaimer
Use at your own risk. I compiled this for usage in a personal project where it worked fine.
