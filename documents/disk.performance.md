# Disk performance 

With Windows 10, measurement only once.

```
C>winsat disk -drive (drive)
```
for example
```
C>winsat disk -drive g
```

# MicroSD performance

## Media: Samsung EVO 64GB SDXC, exFAT/32KB

### Transend USB 3.0 Card reader RDF5W

R(32.59 MB/s) / W(28.19 MB/s) / T(00:00:37.56)

```
C:\Windows\system32>winsat disk -drive g
Windows System Assessment Tool
> Running: Feature Enumeration ''
> Run Time 00:00:00.00
> Running: Storage Assessment '-drive g -ran -read'
> Run Time 00:00:01.50
> Running: Storage Assessment '-drive g -seq -read'
> Run Time 00:00:06.25
> Running: Storage Assessment '-drive g -seq -write'
> Run Time 00:00:20.22
> Running: Storage Assessment '-drive g -flush -seq'
> Run Time 00:00:05.20
> Running: Storage Assessment '-drive g -flush -ran'
> Run Time 00:00:04.08
> Disk  Random 16.0 Read                       13.59 MB/s          5.6
> Disk  Sequential 64.0 Read                   32.59 MB/s          4.5
> Disk  Sequential 64.0 Write                  28.19 MB/s          4.2
> Average Read Time with Sequential Writes     1.973 ms          6.9
> Latency: 95th Percentile                     3.278 ms          6.9
> Latency: Maximum                             9.290 ms          8.1
> Average Read Time with Random Writes         1.424 ms          8.1
> Total Run Time 00:00:37.56
```


## Media: SanDisk Ultra 16GB Class 10

### Transend USB 3.0 Card reader RDF5W

R(77.97 MB/s) / W(39.28 MB/s) / T(00:00:33.22)

```
C:\Windows\system32>winsat disk -drive g
Windows System Assessment Tool
> Running: Feature Enumeration ''
> Run Time 00:00:00.00
> Running: Storage Assessment '-drive g -ran -read'
> Run Time 00:00:01.24
> Running: Storage Assessment '-drive g -seq -read'
> Run Time 00:00:03.06
> Running: Storage Assessment '-drive g -seq -write'
> Run Time 00:00:16.36
> Running: Storage Assessment '-drive g -flush -seq'
> Run Time 00:00:05.16
> Running: Storage Assessment '-drive g -flush -ran'
> Run Time 00:00:06.91
> Disk  Random 16.0 Read                       17.27 MB/s          5.8
> Disk  Sequential 64.0 Read                   77.97 MB/s          6.1
> Disk  Sequential 64.0 Write                  39.28 MB/s          4.9
> Average Read Time with Sequential Writes     1.871 ms          7.0
> Latency: 95th Percentile                     4.170 ms          6.8
> Latency: Maximum                             267.412 ms          7.1
> Average Read Time with Random Writes         2.773 ms          6.6
> Total Run Time 00:00:33.22
```

### HP built in SD-Card slot (HP Pavilion Slimline s5295)

R(18.72 MB/s) / W(16.53 MB/s) / T(00:01:04.97)

```
C:\Windows\system32>winsat disk -drive e
Windows System Assessment Tool
> Running: Feature Enumeration ''
> Run Time 00:00:00.00
> Running: Storage Assessment '-drive e -ran -read'
> Run Time 00:00:01.91
> Running: Storage Assessment '-drive e -seq -read'
> Run Time 00:00:06.61
> Running: Storage Assessment '-drive e -seq -write'
> Run Time 00:00:33.28
> Running: Storage Assessment '-drive e -flush -seq'
> Run Time 00:00:07.34
> Running: Storage Assessment '-drive e -flush -ran'
> Run Time 00:00:08.95
> Disk  Random 16.0 Read                       9.66 MB/s          5.4
> Disk  Sequential 64.0 Read                   18.72 MB/s          3.5
> Disk  Sequential 64.0 Write                  16.53 MB/s          3.3
> Average Read Time with Sequential Writes     2.770 ms          6.7
> Latency: 95th Percentile                     5.001 ms          6.6
> Latency: Maximum                             270.226 ms          7.1
> Average Read Time with Random Writes         3.648 ms          6.4
> Total Run Time 00:01:04.97
```


## Media: Samsung 16GB Class 6

### Transend USB 3.0 Card reader RDF5W

R(22.94 MB/s) / W(5.71 MB/s) / T(00:02:25.02)

```
C:\Windows\system32>winsat disk -drive g
Windows System Assessment Tool
> Running: Feature Enumeration ''
> Run Time 00:00:00.00
> Running: Storage Assessment '-drive g -ran -read'
> Run Time 00:00:02.02
> Running: Storage Assessment '-drive g -seq -read'
> Run Time 00:00:05.94
> Running: Storage Assessment '-drive g -seq -write'
> Run Time 00:01:32.69
> Running: Storage Assessment '-drive g -flush -seq'
> Run Time 00:00:21.20
> Running: Storage Assessment '-drive g -flush -ran'
> Run Time 00:00:21.77
> Disk  Random 16.0 Read                       9.07 MB/s          5.3
> Disk  Sequential 64.0 Read                   22.94 MB/s          3.8
> Disk  Sequential 64.0 Write                  5.71 MB/s          2.5
> Average Read Time with Sequential Writes     9.253 ms          4.7
> Latency: 95th Percentile                     19.501 ms          4.6
> Latency: Maximum                             379.238 ms          5.4
> Average Read Time with Random Writes         9.194 ms          4.7
> Total Run Time 00:02:25.02
```

### HP built in SD-Card slot (HP Pavilion Slimline s5295)

R(18.75 MB/s) / W(5.75 MB/s) / T(00:02:30.06)

```
C:\Windows\system32>winsat disk -drive e
Windows System Assessment Tool
> Running: Feature Enumeration ''
> Run Time 00:00:00.00
> Running: Storage Assessment '-drive e -ran -read'
> Run Time 00:00:02.23
> Running: Storage Assessment '-drive e -seq -read'
> Run Time 00:00:06.38
> Running: Storage Assessment '-drive e -seq -write'
> Run Time 00:01:31.17
> Running: Storage Assessment '-drive e -flush -seq'
> Run Time 00:00:26.22
> Running: Storage Assessment '-drive e -flush -ran'
> Run Time 00:00:22.75
> Disk  Random 16.0 Read                       7.92 MB/s          5.2
> Disk  Sequential 64.0 Read                   18.75 MB/s          3.5
> Disk  Sequential 64.0 Write                  5.75 MB/s          2.5
> Average Read Time with Sequential Writes     11.795 ms          4.1
> Latency: 95th Percentile                     16.615 ms          4.9
> Latency: Maximum                             363.212 ms          5.7
> Average Read Time with Random Writes         9.840 ms          4.5
> Total Run Time 00:02:30.06
```

## Media: SanDisk 8GB Class 4

### Transend USB 3.0 Card reader RDF5W

R(43.85 MB/s) / W(6.26 MB/s) / T(00:08:05.03)

```
C:\Windows\system32>winsat disk -drive g
Windows System Assessment Tool
> Running: Feature Enumeration ''
> Run Time 00:00:00.00
> Running: Storage Assessment '-drive g -ran -read'
> Run Time 00:00:01.33
> Running: Storage Assessment '-drive g -seq -read'
> Run Time 00:00:02.47
> Running: Storage Assessment '-drive g -seq -write'
> Run Time 00:01:25.09
> Running: Storage Assessment '-drive g -flush -seq'
> Run Time 00:00:13.08
> Running: Storage Assessment '-drive g -flush -ran'
> Run Time 00:06:22.56
> Disk  Random 16.0 Read                       15.90 MB/s          5.7
> Disk  Sequential 64.0 Read                   43.85 MB/s          5.1
> Disk  Sequential 64.0 Write                  6.26 MB/s          2.5
> Average Read Time with Sequential Writes     5.856 ms          5.7
> Latency: 95th Percentile                     724.700 ms          1.9
> Latency: Maximum                             1582.349 ms          1.9
> Average Read Time with Random Writes         191.517 ms          1.9
> Total Run Time 00:08:05.03
```

# Options

Change command prompt to US English
```
chcp 437
```

# Reference

* http://www.betterhostreview.com/change-language-in-command-prompt.html
* http://superuser.com/questions/130143/how-to-measure-disk-performance-under-windows

