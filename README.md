# py-secobj #

## ABOUT ##
A simple python library that will handle synchronous encryption (AES) of
a python object to either a string or dumping it right to a file.

## REQUIRED LIBRARIES ##
The only non-standard library required is the PyCrypto library, which
is usually available in your package manager.  If not, get it from 

    https://www.dlitz.net/software/pycrypto/

## INSTALL ##
Install is easy with the standard Python package install

```bash
tar -xvzf py-secobj-X.X.X.tar.gz
cd py-secobj-*
python setup.py install
```

You can also install via *pip* or *easy_install*
    
```bash
pip install py-secobj
```

## USAGE ##
You can use this library to encrypt any "pickleable" object.  It will only
encrypt one object so if you wanted to encrypt multiple, put them in a
container like a list or dict.

A couple of quick examples:

```python
import secobj

passphrase = 'spam and eggs'
fname = '/var/tmp/test.enc'
my_obj = [1 , 2 , 3]
enc = secobj.EncObject(passphrase)

# Encrypt to file and decrypt
enc.encrypt_to_file(my_obj , fname)
unencrypted_object = enc.decrypt_from_file(fname , True)

# Encrypt to string.  You will need to hold on to your IV here
enc_str , iv = enc.encrypt_to_str(my_obj)
unencrypted_object  = enc.decrypt_from_str(enc_str , iv)
```

