#### Yotta install

If your are behind corporate firewall, while following `http://yottadocs.mbed.com/#installing` page, and encounter network problems...

1) install required 
```
$ sudo apt-get install python-setuptools \
cmake build-essential ninja-build python-dev \
libffi-dev libssl-dev
```

2) install pip inside sudo
```
$ sudo -i
# export http_proxy=http://(your proxy server ip):(your proxy port)
# export https_proxy=https://(your proxy server ip):(your proxy port)
# easy_install pip
# pip install yotta
# exit
```

#### HelloYotta

Normally this should work.
```
git clone git@github.com:ARMmbed/helloyotta.git
cd helloyyotta
yotta target frdm-k64f-gcc
yotta build
```

But if you get something like this...
```
error: connection error: bad handshake: Error([('SSL routines', 
'SSL3_GET_SERVER_CERTIFICATE', 'certificate verify failed')],)
```

You can follow as below. I don't think it is safe so do it on your own risk!

```
cd /usr/local/lib/python2.7/dist-packages/yotta/lib
sudo vi registry_access.py
```

Add `verify=False` to all `request.get(....)` like
```
response = requests.get(url, headers=request_headers, verify=False)
...
response = requests.get(url, headers=request_headers, 
                        allow_redirects=True, stream=True, verify=False)
...
response = requests.get(url, headers=headers, params=params, verify=False)
...
```
