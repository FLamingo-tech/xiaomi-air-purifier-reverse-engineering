**Filter Information**

These are binary dumps and traffic snoops.
Different filters with different time left.


This is how the filter password is created:

python script:

    import sys
    import hashlib
    
    # Usage: pwd.py 04A03CAA1E7080
    
    > def getpwd(uid):
    >     uid = bytearray.fromhex(uid)
    >     h = bytearray.fromhex(hashlib.sha1(uid).hexdigest())
    >     pwd = ""
    >     pwd += "%02X" % h[h[0] % 20]
    >     pwd += "%02X" % h[(h[0]+5) % 20]
    >     pwd += "%02X" % h[(h[0]+13) % 20]
    >     pwd += "%02X" % h[(h[0]+17) % 20]
    >     return pwd
    > 
    > assert getpwd("04A03CAA1E7080") == "CD91AFCC" assert
    > getpwd("04112233445566") == "EC9805C8" print("PWD:",
    > getpwd(sys.argv[1]))
