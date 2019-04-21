# Blockchain
Other blockchain such xmr, iota, xlm, bch
1. miner
https://github.com/fireice-uk/xmr-stak

2. xmrig-proxy
build error on centos sometimes:
[liwei@osdnode94 build]$ make
[  1%] Linking CXX executable xmrig-proxy
/usr/bin/ld: cannot find -luuid
collect2: error: ld returned 1 exit status
make[2]: *** [xmrig-proxy] Error 1
make[1]: *** [CMakeFiles/xmrig-proxy.dir/all] Error 2
make: *** [all] Error 2

fixed by
cmake3 .. -DUV_LIBRARY=/usr/lib64/libuv.a
and changing in file
CMakeFiles/xmrig-proxy.dir/link.txt
last line to
-Wl,-Bdynamic -luuid
rather than
-Wl,-Bstatic -luuid

resolves the problem
!!!It is a dynamic lib
https://github.com/xmrig/xmrig-proxy/issues/295
