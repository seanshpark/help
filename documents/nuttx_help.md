#### Get latest NuttX

```
mkdir nuttx.up; cd nuttx.up
git init
git submodule add https://bitbucket.org/patacongo/nuttx.git nuttx
git submodule add https://bitbucket.org/nuttx/apps.git apps
cd nuttx
git submodule update --init --recursive
```

grab a coffee...