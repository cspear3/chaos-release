#Stream Benchmark results

# Stream #

> Stream is from http://www.cs.virginia.edu/stream/ref.html

> The rpm that contains this test is called tasty\_loops. It can be found at [ftp://gdo-lc.ucllnl.org/pub/projects/chaos/4.3/x86_64/RPMS/](ftp://gdo-lc.ucllnl.org/pub/projects/chaos/4.3/x86_64/RPMS/) . This rpm will be installed if you have the "opt" YUM group installed. You can also install it by running `sudo yum -c ftp://gdo-lc.ucllnl.org/pub/projects/chaos/chaos.centos.repo --enablerepo=4.3* install tasty_loops`

> The stream benchmark is run by `/opt/tasty_loops-0.2/stream/benchmark`

> The benchmark will start running with 1 thread per socket and increase to the number of cores per socket. The variable GOMP\_CPU\_AFFINITY is used to guarantee that each socket has the same number of threads running on it.

> Streamc was compiled with RHEL5's default compiler, 4.1.2 20080704 with CFLAGS -O3 -fopenmp -DDGEMM -DMXMD16 -DLINUX. Better performance can be had by using other compilers and optimizing, but this gives a good idea of relative performance. Note that BIOS upgrades can have a big impact. Be sure that you have the latest release installed.

## AMD 8216, Memory 667MHz ##
```
8 cpus
4 sockets
2 cpu(s) per socket
Processor type  Dual-Core AMD Opteron(tm) Processor 8216

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:        9772.4832       0.0708       0.0655       0.1124
Scale:       9408.8509       0.0747       0.0680       0.1152
Add:        10152.4989       0.1108       0.0946       0.1671
Triad:      10175.2043       0.1076       0.0943       0.1613
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       13913.3308       0.0471       0.0460       0.0485
Scale:      13886.7713       0.0471       0.0461       0.0483
Add:        14758.5534       0.0672       0.0650       0.0698
Triad:      14827.8482       0.0668       0.0647       0.0697
```

## AMD 8354, Memory 667Mhz ##
```
16 cpus
4 sockets
4 cpu(s) per socket
Processor type  Quad-Core AMD Opteron(tm) Processor 8354

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       10278.6610       0.0623       0.0623       0.0625
Scale:       9671.6071       0.0662       0.0662       0.0662
Add:        10181.2505       0.0943       0.0943       0.0943
Triad:      10196.1521       0.0942       0.0942       0.0942
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       11445.2863       0.0560       0.0559       0.0560
Scale:      11650.7939       0.0550       0.0549       0.0551
Add:        11537.7703       0.0832       0.0832       0.0833
Triad:      11514.6412       0.0835       0.0834       0.0836
Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       11556.2975       0.0555       0.0554       0.0556
Scale:      11680.7561       0.0549       0.0548       0.0550
Add:        11640.0330       0.0826       0.0825       0.0827
Triad:      11625.3803       0.0826       0.0826       0.0827
Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       18125.1616       0.0353       0.0353       0.0354
Scale:      18051.6634       0.0355       0.0355       0.0355
Add:        18455.8527       0.0526       0.0520       0.0567
Triad:      18482.5382       0.0520       0.0519       0.0525
```

## AMD 8380, Memory 667 ##
```
16 cpus
4 sockets
4 cpu(s) per socket
Processor type  Quad-Core AMD Opteron(tm) Processor 8380

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       11817.4895       0.0543       0.0542       0.0544
Scale:      10912.0104       0.0588       0.0587       0.0589
Add:        12387.5754       0.0776       0.0775       0.0778
Triad:      12394.6298       0.0776       0.0775       0.0780
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       14703.4747       0.0436       0.0435       0.0438
Scale:      14438.7674       0.0445       0.0443       0.0448
Add:        15299.0126       0.0631       0.0627       0.0634
Triad:      15309.5413       0.0629       0.0627       0.0636
Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       15178.7941       0.0424       0.0422       0.0428
Scale:      15146.8472       0.0424       0.0423       0.0427
Add:        16277.5626       0.0592       0.0590       0.0596
Triad:      16286.3192       0.0591       0.0589       0.0595
Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       20124.4082       0.0327       0.0318       0.0393
Scale:      20052.6991       0.0320       0.0319       0.0320
Add:        22834.2993       0.0421       0.0420       0.0421
Triad:      22978.0285       0.0418       0.0418       0.0419
```

## AMD 8431, Memory 553MHz ##
```
24 cpus
4 sockets
6 cpu(s) per socket
Processor type  Six-Core AMD Opteron(tm) Processor 8431

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       16144.9398       0.0399       0.0396       0.0402
Scale:      15718.5703       0.0410       0.0407       0.0413
Add:        17382.7889       0.0556       0.0552       0.0560
Triad:      17463.7601       0.0556       0.0550       0.0559
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       17398.9005       0.0372       0.0368       0.0380
Scale:      17167.8929       0.0378       0.0373       0.0386
Add:        19410.7726       0.0505       0.0495       0.0524
Triad:      19535.2706       0.0498       0.0491       0.0507
Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       17978.0365       0.0357       0.0356       0.0360
Scale:      17702.5037       0.0362       0.0362       0.0364
Add:        20183.7240       0.0477       0.0476       0.0478
Triad:      20274.5813       0.0474       0.0473       0.0475
Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       18062.3524       0.0355       0.0354       0.0355
Scale:      18048.0224       0.0355       0.0355       0.0355
Add:        20361.4198       0.0472       0.0471       0.0473
Triad:      20462.6189       0.0469       0.0469       0.0470
Running 5 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       17983.5768       0.0356       0.0356       0.0357
Scale:      18100.5958       0.0354       0.0354       0.0354
Add:        20328.2166       0.0473       0.0472       0.0474
Triad:      20426.3907       0.0471       0.0470       0.0471
Running 6 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       17952.3067       0.0357       0.0357       0.0357
Scale:      18061.7447       0.0355       0.0354       0.0355
Add:        20301.9777       0.0473       0.0473       0.0474
Triad:      20405.9975       0.0471       0.0470       0.0471
```

## AMD 8431, Memory 667Mhz ##
```
24 cpus
4 sockets
6 cpu(s) per socket
Processor type  Six-Core AMD Opteron(tm) Processor 8431

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       20812.9836       0.0309       0.0308       0.0311
Scale:      19991.1717       0.0322       0.0320       0.0325
Add:        23115.8790       0.0417       0.0415       0.0418
Triad:      23181.6220       0.0416       0.0414       0.0419
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       21977.3261       0.0296       0.0291       0.0306
Scale:      21643.4825       0.0302       0.0296       0.0310
Add:        24477.9924       0.0401       0.0392       0.0406
Triad:      24711.7457       0.0398       0.0388       0.0405
Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       22758.0250       0.0283       0.0281       0.0284
Scale:      22383.7977       0.0287       0.0286       0.0288
Add:        25474.3825       0.0378       0.0377       0.0380
Triad:      25561.8733       0.0377       0.0376       0.0378
Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       22972.0637       0.0279       0.0279       0.0280
Scale:      22880.8169       0.0280       0.0280       0.0280
Add:        25818.2181       0.0372       0.0372       0.0373
Triad:      25919.2646       0.0371       0.0370       0.0372
Running 5 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       22917.7372       0.0280       0.0279       0.0281
Scale:      23041.4723       0.0279       0.0278       0.0280
Add:        25812.5907       0.0373       0.0372       0.0374
Triad:      25918.5973       0.0371       0.0370       0.0372
Running 6 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       23013.4218       0.0279       0.0278       0.0279
Scale:      23087.2500       0.0278       0.0277       0.0278
Add:        25894.9281       0.0371       0.0371       0.0372
Triad:      26023.2915       0.0369       0.0369       0.0370
```

## AMD 8431, Memory 800MHz ##
```
24 cpus
4 sockets
6 cpu(s) per socket
Processor type  Six-Core AMD Opteron(tm) Processor 8431

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       20436.8100       0.0320       0.0313       0.0324
Scale:      19321.3555       0.0336       0.0331       0.0339
Add:        21877.3803       0.0448       0.0439       0.0460
Triad:      21941.8766       0.0447       0.0438       0.0460
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       24494.7445       0.0264       0.0261       0.0266
Scale:      23924.3022       0.0270       0.0268       0.0273
Add:        26620.1141       0.0363       0.0361       0.0364
Triad:      26645.1282       0.0361       0.0360       0.0362
Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       26127.6480       0.0246       0.0245       0.0246
Scale:      25683.1795       0.0250       0.0249       0.0252
Add:        29266.6272       0.0329       0.0328       0.0329
Triad:      29385.5955       0.0327       0.0327       0.0328
Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       26772.5982       0.0240       0.0239       0.0240
Scale:      26666.4802       0.0241       0.0240       0.0241
Add:        30030.8162       0.0320       0.0320       0.0320
Triad:      30165.1284       0.0319       0.0318       0.0319
Running 5 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       26547.2780       0.0241       0.0241       0.0242
Scale:      26706.8067       0.0240       0.0240       0.0241
Add:        29952.1828       0.0321       0.0321       0.0322
Triad:      30035.5205       0.0320       0.0320       0.0320
Running 6 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       26473.4468       0.0242       0.0242       0.0242
Scale:      26725.6853       0.0240       0.0239       0.0240
Add:        29852.4762       0.0322       0.0322       0.0322
Triad:      29992.5650       0.0320       0.0320       0.0321
```

## AMD 8435, Memory 667MHz ##
```
24 cpus
4 sockets
6 cpu(s) per socket
Processor type  Six-Core AMD Opteron(tm) Processor 8435

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       18181.7567       0.0362       0.0352       0.0365
Scale:      17506.9266       0.0374       0.0366       0.0377
Add:        19596.6897       0.0499       0.0490       0.0507
Triad:      19637.8827       0.0497       0.0489       0.0506
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       20926.7237       0.0307       0.0306       0.0308
Scale:      20536.5620       0.0314       0.0312       0.0315
Add:        23187.2288       0.0416       0.0414       0.0418
Triad:      23336.6669       0.0414       0.0411       0.0415
Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       22204.3837       0.0289       0.0288       0.0290
Scale:      21860.8110       0.0294       0.0293       0.0297
Add:        24874.3280       0.0387       0.0386       0.0388
Triad:      25032.5258       0.0385       0.0384       0.0386
Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       22398.7397       0.0286       0.0286       0.0287
Scale:      22346.3439       0.0287       0.0286       0.0287
Add:        25239.3336       0.0381       0.0380       0.0382
Triad:      25329.8347       0.0380       0.0379       0.0380
Running 5 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       22368.3165       0.0287       0.0286       0.0287
Scale:      22513.1426       0.0285       0.0284       0.0285
Add:        25301.1853       0.0381       0.0379       0.0381
Triad:      25389.4095       0.0379       0.0378       0.0380
Running 6 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       22343.1819       0.0287       0.0286       0.0288
Scale:      22510.6883       0.0285       0.0284       0.0285
Add:        25238.5426       0.0381       0.0380       0.0382
Triad:      25350.5663       0.0379       0.0379       0.0380
```

## Intel E5530, Memory 1066MHz ##
```
8 cpus
2 sockets
4 cpu(s) per socket
Processor type  Intel(R) Xeon(R) CPU           E5530  @ 2.40GHz

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       14074.2553       0.0455       0.0455       0.0457
Scale:      13628.3098       0.0470       0.0470       0.0470
Add:        15306.6314       0.0643       0.0627       0.0765
Triad:      14685.1885       0.0654       0.0654       0.0658
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       19447.6169       0.0332       0.0329       0.0335
Scale:      19372.8092       0.0331       0.0330       0.0334
Add:        20686.5413       0.0465       0.0464       0.0466
Triad:      20741.5267       0.0463       0.0463       0.0464
Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       21641.3886       0.0298       0.0296       0.0300
Scale:      21704.3820       0.0295       0.0295       0.0297
Add:        23447.8308       0.0411       0.0409       0.0415
Triad:      23599.4130       0.0408       0.0407       0.0410
Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       21417.6086       0.0307       0.0299       0.0314
Scale:      21799.0317       0.0295       0.0294       0.0297
Add:        24100.7227       0.0412       0.0398       0.0435
Triad:      24141.9054       0.0400       0.0398       0.0402
```

## Intel E5540, Memory 1066Mhz ##
```
8 cpus
2 sockets
4 cpu(s) per socket
Processor type  Intel(R) Xeon(R) CPU           E5540  @ 2.53GHz

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       16705.3829       0.0393       0.0383       0.0418
Scale:      16603.9127       0.0405       0.0385       0.0448
Add:        18529.9995       0.0531       0.0518       0.0579
Triad:      18196.6289       0.0529       0.0528       0.0534

Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       20980.0431       0.0313       0.0305       0.0329
Scale:      20750.2382       0.0315       0.0308       0.0332
Add:        22524.5401       0.0438       0.0426       0.0457
Triad:      22303.2073       0.0444       0.0430       0.0464

Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       22136.2682       0.0291       0.0289       0.0292
Scale:      22172.2880       0.0290       0.0289       0.0291
Add:        24202.7075       0.0400       0.0397       0.0404
Triad:      24104.9068       0.0400       0.0398       0.0402

Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       22173.0206       0.0290       0.0289       0.0292
Scale:      22210.6302       0.0289       0.0288       0.0291
Add:        24402.6317       0.0396       0.0393       0.0398
Triad:      24361.1449       0.0395       0.0394       0.0396
```

## Intel X5550, Memory 1333MHz ##
```
8 cpus
2 sockets
4 cpu(s) per socket
Processor type  Intel(R) Xeon(R) CPU           X5550  @ 2.67GHz

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       19531.2434       0.0331       0.0328       0.0352
Scale:      19416.2482       0.0331       0.0330       0.0339
Add:        21352.3027       0.0450       0.0450       0.0451
Triad:      20950.2424       0.0459       0.0458       0.0459
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       25209.7046       0.0254       0.0254       0.0254
Scale:      24834.2097       0.0258       0.0258       0.0259
Add:        27025.5174       0.0356       0.0355       0.0357
Triad:      26639.3109       0.0362       0.0360       0.0364
Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       27088.6983       0.0237       0.0236       0.0239
Scale:      27066.0284       0.0237       0.0236       0.0237
Add:        29415.2203       0.0328       0.0326       0.0330
Triad:      29388.3837       0.0328       0.0327       0.0329
Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       27260.6333       0.0235       0.0235       0.0236
Scale:      27423.2736       0.0234       0.0233       0.0234
Add:        29867.5338       0.0322       0.0321       0.0323
Triad:      29901.9133       0.0322       0.0321       0.0323
```

## Intel X5570, Memory 1333MHz ##
```
8 cpus
2 sockets
4 cpu(s) per socket
Processor type  Intel(R) Xeon(R) CPU           X5570  @ 2.93GHz

Running 1 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       16768.4126       0.0382       0.0382       0.0383
Scale:      16124.1864       0.0397       0.0397       0.0397
Add:        17930.1229       0.0536       0.0535       0.0536
Triad:      17200.3445       0.0558       0.0558       0.0559
Running 2 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       23389.1953       0.0274       0.0274       0.0275
Scale:      23243.1774       0.0276       0.0275       0.0277
Add:        24940.2704       0.0386       0.0385       0.0389
Triad:      24790.8622       0.0389       0.0387       0.0389
Running 3 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       26314.6217       0.0246       0.0243       0.0249
Scale:      26439.8097       0.0243       0.0242       0.0244
Add:        28484.0362       0.0339       0.0337       0.0341
Triad:      28477.3883       0.0339       0.0337       0.0341
Running 4 threads per socket
Array size = 40000000, Offset = 0
Total memory required = 915.5 MB.
Function      Rate (MB/s)   Avg time     Min time     Max time
Copy:       26949.7275       0.0239       0.0237       0.0241
Scale:      27281.6895       0.0235       0.0235       0.0236
Add:        29706.6749       0.0327       0.0323       0.0341
Triad:      29655.2596       0.0326       0.0324       0.0328
```