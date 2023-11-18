# Lab Report: Week 5, 10/31/2023, 4-6:00 pm
# Hao Tri Luu

---
## Part 1
I am writing about the bugs for the `ArrayTests.java` implementation of the method `testReversedLongArray()`.
The JUnit test I wrote and ran are:

The first output, which is failure-inducing, is an array with elements `{1,2,3}`.
```
@Test
public void testReversedLongArray(){
  int[] arr = {1,2,3};
  int[] rra = {3,2,1};
  assertArrayEquals(rra, ArrayExamples.reversed(arr));
}
```
The result of running the debugger is `expected:<3> but was:<0>` being outputted in the terminal.

The second output, which is not failure-inducing, is an array with elements `{0}`.
```
@Test
public void testReversedLongArray(){
  int[] arr = {0};
  int[] rra = {0};
  assertArrayEquals(rra, ArrayExamples.reversed(arr));
}
```
The result of running the debugger is that no bugs are caught and the terminal just prints the runtime.

Screenshot with symptom:
![Image](Screenshot 2023-11-05 175422.png)

Screenshot with passing test:
![Image](Screenshot 2023-11-05 175457.png)

The original code is:
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```

The fixed code is:
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[i] = arr[arr.length - i - 1];
  }
  return newArray;
}
```
The issue was fixed because in the code, the array `newArray` is supposed to store the reversed array but the code was not taking elements from the input `arr` and filling `newArray`. Rather, The elements of `newArray` were filling `arr`, and `arr` was being returned instead of `newArray`. Because `newArray` was initialized with only size, it was populated with `0`, so the returned array had elements of `0` instead of the correct values.

---
## Part 2
I googled and used: [https://www.geeksforgeeks.org/grep-command-in-unixlinux/](https://www.geeksforgeeks.org/grep-command-in-unixlinux/) to research each of the `grep` commands.

The first option I explored was `-v` which is described as printing the lines that do not match the given string. I used: `grep -v "biomed" technical` as an input and got `grep: technical: Is a directory` as an output. This is because the `grep` command is for files not directories (for the other commands, I will not try it on directories as the result is redundant). I then used `grep -v -c "1" technical/biomed/*.txt` where `-v` is the test option and `-c` is an additional option that only counts how many lines in each file. The output is:
```
$ grep -v -c "1" technical/biomed/*.txt
technical/biomed/1468-6708-3-1.txt:389
technical/biomed/1468-6708-3-10.txt:468
technical/biomed/1468-6708-3-3.txt:274
technical/biomed/1468-6708-3-4.txt:524
technical/biomed/1468-6708-3-7.txt:256
technical/biomed/1471-2091-2-10.txt:292
technical/biomed/1471-2091-2-11.txt:534
technical/biomed/1471-2091-2-12.txt:368
technical/biomed/1471-2091-2-13.txt:503
technical/biomed/1471-2091-2-16.txt:282
technical/biomed/1471-2091-2-5.txt:704
technical/biomed/1471-2091-2-7.txt:399
technical/biomed/1471-2091-2-9.txt:384
technical/biomed/1471-2091-3-13.txt:474
technical/biomed/1471-2091-3-14.txt:756
technical/biomed/1471-2091-3-15.txt:541
technical/biomed/1471-2091-3-16.txt:529
technical/biomed/1471-2091-3-17.txt:514
technical/biomed/1471-2091-3-18.txt:493
technical/biomed/1471-2091-3-22.txt:466
technical/biomed/1471-2091-3-23.txt:524
technical/biomed/1471-2091-3-30.txt:566
technical/biomed/1471-2091-3-31.txt:780
technical/biomed/1471-2091-3-4.txt:795
technical/biomed/1471-2091-3-8.txt:369
technical/biomed/1471-2091-4-1.txt:442
technical/biomed/1471-2091-4-5.txt:304
technical/biomed/1471-2105-1-1.txt:748
technical/biomed/1471-2105-2-1.txt:523
technical/biomed/1471-2105-2-8.txt:1405
technical/biomed/1471-2105-2-9.txt:386
technical/biomed/1471-2105-3-12.txt:353
technical/biomed/1471-2105-3-14.txt:1067
technical/biomed/1471-2105-3-16.txt:726
technical/biomed/1471-2105-3-17.txt:832
technical/biomed/1471-2105-3-18.txt:2131
technical/biomed/1471-2105-3-2.txt:2068
technical/biomed/1471-2105-3-22.txt:485
technical/biomed/1471-2105-3-23.txt:503
technical/biomed/1471-2105-3-24.txt:192
technical/biomed/1471-2105-3-26.txt:501
technical/biomed/1471-2105-3-28.txt:843
technical/biomed/1471-2105-3-3.txt:1153
technical/biomed/1471-2105-3-30.txt:807
technical/biomed/1471-2105-3-34.txt:533
technical/biomed/1471-2105-3-37.txt:437
technical/biomed/1471-2105-3-38.txt:832
technical/biomed/1471-2105-3-4.txt:509
technical/biomed/1471-2105-3-6.txt:710
technical/biomed/1471-2105-4-13.txt:536
technical/biomed/1471-2105-4-24.txt:416
technical/biomed/1471-2105-4-25.txt:357
technical/biomed/1471-2105-4-26.txt:549
technical/biomed/1471-2105-4-27.txt:366
technical/biomed/1471-2105-4-28.txt:519
technical/biomed/1471-2105-4-31.txt:456
technical/biomed/1471-2121-1-2.txt:415
technical/biomed/1471-2121-2-1.txt:406
technical/biomed/1471-2121-2-10.txt:732
technical/biomed/1471-2121-2-11.txt:658
technical/biomed/1471-2121-2-12.txt:386
technical/biomed/1471-2121-2-15.txt:494
technical/biomed/1471-2121-2-18.txt:431
technical/biomed/1471-2121-2-21.txt:448
technical/biomed/1471-2121-2-22.txt:408
technical/biomed/1471-2121-2-3.txt:216
technical/biomed/1471-2121-2-6.txt:457
technical/biomed/1471-2121-3-10.txt:591
technical/biomed/1471-2121-3-11.txt:434
technical/biomed/1471-2121-3-12.txt:821
technical/biomed/1471-2121-3-13.txt:661
technical/biomed/1471-2121-3-15.txt:661
technical/biomed/1471-2121-3-16.txt:655
technical/biomed/1471-2121-3-18.txt:560
technical/biomed/1471-2121-3-19.txt:748
technical/biomed/1471-2121-3-2.txt:453
technical/biomed/1471-2121-3-21.txt:588
technical/biomed/1471-2121-3-22.txt:501
technical/biomed/1471-2121-3-25.txt:744
technical/biomed/1471-2121-3-30.txt:670
technical/biomed/1471-2121-3-4.txt:741
technical/biomed/1471-2121-3-6.txt:530
technical/biomed/1471-2121-3-8.txt:270
technical/biomed/1471-2121-4-1.txt:275
technical/biomed/1471-2121-4-2.txt:480
technical/biomed/1471-2121-4-3.txt:478
technical/biomed/1471-2121-4-4.txt:422
technical/biomed/1471-2121-4-5.txt:432
technical/biomed/1471-2121-4-6.txt:401
technical/biomed/1471-213X-1-1.txt:241
technical/biomed/1471-213X-1-10.txt:478
technical/biomed/1471-213X-1-11.txt:470
technical/biomed/1471-213X-1-12.txt:439
technical/biomed/1471-213X-1-13.txt:620
technical/biomed/1471-213X-1-15.txt:665
technical/biomed/1471-213X-1-2.txt:745
technical/biomed/1471-213X-1-3.txt:590
technical/biomed/1471-213X-1-4.txt:300
technical/biomed/1471-213X-1-6.txt:658
technical/biomed/1471-213X-1-9.txt:672
technical/biomed/1471-213X-2-1.txt:591
technical/biomed/1471-213X-2-7.txt:707
technical/biomed/1471-213X-2-8.txt:238
technical/biomed/1471-213X-3-2.txt:360
technical/biomed/1471-213X-3-3.txt:879
technical/biomed/1471-213X-3-4.txt:705
technical/biomed/1471-213X-3-7.txt:522
technical/biomed/1471-2148-1-1.txt:354
technical/biomed/1471-2148-1-14.txt:405
technical/biomed/1471-2148-1-4.txt:482
technical/biomed/1471-2148-1-6.txt:232
technical/biomed/1471-2148-1-8.txt:837
technical/biomed/1471-2148-2-12.txt:506
technical/biomed/1471-2148-2-14.txt:264
technical/biomed/1471-2148-2-15.txt:451
technical/biomed/1471-2148-2-17.txt:941
technical/biomed/1471-2148-2-2.txt:450
technical/biomed/1471-2148-2-5.txt:276
technical/biomed/1471-2148-2-7.txt:299
technical/biomed/1471-2148-2-8.txt:600
technical/biomed/1471-2148-3-1.txt:349
technical/biomed/1471-2148-3-18.txt:552
technical/biomed/1471-2148-3-3.txt:910
technical/biomed/1471-2148-3-4.txt:582
technical/biomed/1471-2148-3-7.txt:628
technical/biomed/1471-2156-2-1.txt:585
technical/biomed/1471-2156-2-12.txt:572
technical/biomed/1471-2156-2-17.txt:436
technical/biomed/1471-2156-2-18.txt:662
technical/biomed/1471-2156-2-3.txt:258
technical/biomed/1471-2156-2-5.txt:363
technical/biomed/1471-2156-2-7.txt:260
technical/biomed/1471-2156-2-8.txt:164
technical/biomed/1471-2156-3-10.txt:551
technical/biomed/1471-2156-3-11.txt:313
technical/biomed/1471-2156-3-16.txt:690
technical/biomed/1471-2156-3-17.txt:795
technical/biomed/1471-2156-3-22.txt:201
technical/biomed/1471-2156-3-3.txt:337
technical/biomed/1471-2156-3-4.txt:637
technical/biomed/1471-2156-4-10.txt:730
technical/biomed/1471-2156-4-5.txt:417
technical/biomed/1471-2156-4-6.txt:583
technical/biomed/1471-2156-4-9.txt:618
technical/biomed/1471-2164-2-1.txt:558
technical/biomed/1471-2164-2-2.txt:557
technical/biomed/1471-2164-2-4.txt:412
technical/biomed/1471-2164-2-6.txt:280
technical/biomed/1471-2164-2-7.txt:488
technical/biomed/1471-2164-2-8.txt:441
technical/biomed/1471-2164-2-9.txt:709
technical/biomed/1471-2164-3-1.txt:402
technical/biomed/1471-2164-3-10.txt:321
technical/biomed/1471-2164-3-13.txt:383
technical/biomed/1471-2164-3-15.txt:389
technical/biomed/1471-2164-3-16.txt:421
technical/biomed/1471-2164-3-18.txt:706
technical/biomed/1471-2164-3-19.txt:525
technical/biomed/1471-2164-3-23.txt:481
technical/biomed/1471-2164-3-24.txt:464
technical/biomed/1471-2164-3-26.txt:334
technical/biomed/1471-2164-3-27.txt:387
technical/biomed/1471-2164-3-28.txt:773
technical/biomed/1471-2164-3-29.txt:339
technical/biomed/1471-2164-3-30.txt:235
technical/biomed/1471-2164-3-31.txt:615
technical/biomed/1471-2164-3-32.txt:484
technical/biomed/1471-2164-3-33.txt:549
technical/biomed/1471-2164-3-34.txt:341
technical/biomed/1471-2164-3-35.txt:573
technical/biomed/1471-2164-3-4.txt:808
technical/biomed/1471-2164-3-6.txt:321
technical/biomed/1471-2164-3-7.txt:623
technical/biomed/1471-2164-3-8.txt:530
technical/biomed/1471-2164-3-9.txt:440
technical/biomed/1471-2164-4-13.txt:472
technical/biomed/1471-2164-4-14.txt:370
technical/biomed/1471-2164-4-15.txt:406
technical/biomed/1471-2164-4-16.txt:586
technical/biomed/1471-2164-4-19.txt:492
technical/biomed/1471-2164-4-2.txt:367
technical/biomed/1471-2164-4-21.txt:622
technical/biomed/1471-2164-4-22.txt:538
technical/biomed/1471-2164-4-23.txt:480
technical/biomed/1471-2164-4-24.txt:436
technical/biomed/1471-2164-4-25.txt:274
technical/biomed/1471-2164-4-26.txt:582
technical/biomed/1471-2164-4-28.txt:496
technical/biomed/1471-2164-4-4.txt:735
technical/biomed/1471-2164-4-5.txt:394
technical/biomed/1471-2164-4-6.txt:451
technical/biomed/1471-2172-1-1.txt:466
technical/biomed/1471-2172-2-10.txt:564
technical/biomed/1471-2172-2-3.txt:716
technical/biomed/1471-2172-2-4.txt:551
technical/biomed/1471-2172-2-9.txt:284
technical/biomed/1471-2172-3-1.txt:299
technical/biomed/1471-2172-3-10.txt:633
technical/biomed/1471-2172-3-12.txt:489
technical/biomed/1471-2172-3-16.txt:649
technical/biomed/1471-2172-3-2.txt:544
technical/biomed/1471-2172-3-4.txt:580
technical/biomed/1471-2172-3-9.txt:302
technical/biomed/1471-2172-4-1.txt:341
technical/biomed/1471-2172-4-2.txt:401
technical/biomed/1471-2180-1-12.txt:569
technical/biomed/1471-2180-1-16.txt:470
technical/biomed/1471-2180-1-26.txt:815
technical/biomed/1471-2180-1-28.txt:362
technical/biomed/1471-2180-1-29.txt:465
technical/biomed/1471-2180-1-31.txt:442
technical/biomed/1471-2180-1-33.txt:540
technical/biomed/1471-2180-1-34.txt:531
technical/biomed/1471-2180-1-7.txt:598
technical/biomed/1471-2180-1-8.txt:590
technical/biomed/1471-2180-2-1.txt:517
technical/biomed/1471-2180-2-13.txt:462
technical/biomed/1471-2180-2-16.txt:602
technical/biomed/1471-2180-2-2.txt:357
technical/biomed/1471-2180-2-20.txt:531
technical/biomed/1471-2180-2-22.txt:415
technical/biomed/1471-2180-2-26.txt:312
technical/biomed/1471-2180-2-29.txt:241
technical/biomed/1471-2180-2-32.txt:330
technical/biomed/1471-2180-2-35.txt:771
technical/biomed/1471-2180-2-38.txt:312
technical/biomed/1471-2180-2-7.txt:422
technical/biomed/1471-2180-3-10.txt:572
technical/biomed/1471-2180-3-11.txt:879
technical/biomed/1471-2180-3-13.txt:664
technical/biomed/1471-2180-3-15.txt:670
technical/biomed/1471-2180-3-4.txt:619
technical/biomed/1471-2180-3-5.txt:736
technical/biomed/1471-2180-3-9.txt:572
technical/biomed/1471-2199-2-1.txt:513
technical/biomed/1471-2199-2-10.txt:383
technical/biomed/1471-2199-2-12.txt:366
technical/biomed/1471-2199-2-2.txt:402
technical/biomed/1471-2199-2-3.txt:331
technical/biomed/1471-2199-2-4.txt:791
technical/biomed/1471-2199-2-5.txt:498
technical/biomed/1471-2199-2-6.txt:389
technical/biomed/1471-2199-3-10.txt:291
technical/biomed/1471-2199-3-11.txt:393
technical/biomed/1471-2199-3-12.txt:474
technical/biomed/1471-2199-3-17.txt:365
technical/biomed/1471-2199-3-3.txt:449
technical/biomed/1471-2199-3-7.txt:497
technical/biomed/1471-2199-4-4.txt:478
technical/biomed/1471-2199-4-5.txt:446
technical/biomed/1471-2202-1-1.txt:312
technical/biomed/1471-2202-2-1.txt:609
technical/biomed/1471-2202-2-10.txt:242
technical/biomed/1471-2202-2-12.txt:445
technical/biomed/1471-2202-2-14.txt:385
technical/biomed/1471-2202-2-15.txt:348
technical/biomed/1471-2202-2-16.txt:476
technical/biomed/1471-2202-2-17.txt:423
technical/biomed/1471-2202-2-18.txt:318
technical/biomed/1471-2202-2-19.txt:486
technical/biomed/1471-2202-2-2.txt:282
technical/biomed/1471-2202-2-20.txt:668
technical/biomed/1471-2202-2-3.txt:430
technical/biomed/1471-2202-2-5.txt:522
technical/biomed/1471-2202-2-6.txt:406
technical/biomed/1471-2202-2-7.txt:397
technical/biomed/1471-2202-2-8.txt:657
technical/biomed/1471-2202-2-9.txt:656
technical/biomed/1471-2202-3-1.txt:1205
technical/biomed/1471-2202-3-10.txt:367
technical/biomed/1471-2202-3-11.txt:518
technical/biomed/1471-2202-3-14.txt:531
technical/biomed/1471-2202-3-16.txt:654
technical/biomed/1471-2202-3-17.txt:554
technical/biomed/1471-2202-3-19.txt:479
technical/biomed/1471-2202-3-20.txt:556
technical/biomed/1471-2202-3-3.txt:492
technical/biomed/1471-2202-3-4.txt:445
technical/biomed/1471-2202-3-5.txt:855
technical/biomed/1471-2202-3-7.txt:474
technical/biomed/1471-2202-3-8.txt:398
technical/biomed/1471-2202-4-10.txt:452
technical/biomed/1471-2202-4-11.txt:582
technical/biomed/1471-2202-4-12.txt:345
technical/biomed/1471-2202-4-16.txt:370
technical/biomed/1471-2202-4-17.txt:446
technical/biomed/1471-2202-4-2.txt:552
technical/biomed/1471-2202-4-3.txt:661
technical/biomed/1471-2202-4-5.txt:394
technical/biomed/1471-2202-4-6.txt:396
technical/biomed/1471-2210-1-10.txt:420
technical/biomed/1471-2210-1-2.txt:225
technical/biomed/1471-2210-1-3.txt:454
technical/biomed/1471-2210-1-4.txt:471
technical/biomed/1471-2210-1-7.txt:797
technical/biomed/1471-2210-1-8.txt:297
technical/biomed/1471-2210-2-14.txt:611
technical/biomed/1471-2210-2-4.txt:316
technical/biomed/1471-2210-2-5.txt:494
technical/biomed/1471-2210-2-6.txt:517
technical/biomed/1471-2210-2-8.txt:398
technical/biomed/1471-2210-2-9.txt:343
technical/biomed/1471-2210-3-1.txt:462
technical/biomed/1471-2210-3-3.txt:269
technical/biomed/1471-2229-1-2.txt:492
technical/biomed/1471-2229-1-3.txt:311
technical/biomed/1471-2229-2-11.txt:484
technical/biomed/1471-2229-2-3.txt:726
technical/biomed/1471-2229-2-4.txt:532
technical/biomed/1471-2229-2-8.txt:373
technical/biomed/1471-2229-2-9.txt:623
technical/biomed/1471-2229-3-3.txt:229
technical/biomed/1471-2253-1-1.txt:304
technical/biomed/1471-2253-2-4.txt:270
technical/biomed/1471-2253-2-5.txt:826
technical/biomed/1471-2261-1-6.txt:290
technical/biomed/1471-2261-2-11.txt:407
technical/biomed/1471-2261-3-4.txt:690
technical/biomed/1471-2261-3-5.txt:434
technical/biomed/1471-2288-1-9.txt:423
technical/biomed/1471-2288-2-10.txt:708
technical/biomed/1471-2288-2-11.txt:587
technical/biomed/1471-2288-2-4.txt:471
technical/biomed/1471-2288-3-4.txt:1031
technical/biomed/1471-2288-3-8.txt:707
technical/biomed/1471-2288-3-9.txt:747
technical/biomed/1471-2296-3-18.txt:457
technical/biomed/1471-2296-3-19.txt:351
technical/biomed/1471-2296-3-3.txt:422
technical/biomed/1471-230X-1-10.txt:403
technical/biomed/1471-230X-1-5.txt:297
technical/biomed/1471-230X-1-6.txt:219
technical/biomed/1471-230X-1-8.txt:255
technical/biomed/1471-230X-2-17.txt:210
technical/biomed/1471-230X-2-21.txt:230
technical/biomed/1471-230X-2-23.txt:314
technical/biomed/1471-230X-3-3.txt:241
technical/biomed/1471-230X-3-5.txt:353
technical/biomed/1471-2318-3-2.txt:576
technical/biomed/1471-2326-2-4.txt:396
technical/biomed/1471-2334-1-10.txt:266
technical/biomed/1471-2334-1-13.txt:340
technical/biomed/1471-2334-1-17.txt:279
technical/biomed/1471-2334-1-21.txt:295
technical/biomed/1471-2334-1-24.txt:335
technical/biomed/1471-2334-1-9.txt:289
technical/biomed/1471-2334-2-1.txt:363
technical/biomed/1471-2334-2-24.txt:509
technical/biomed/1471-2334-2-26.txt:500
technical/biomed/1471-2334-2-27.txt:431
technical/biomed/1471-2334-2-29.txt:389
technical/biomed/1471-2334-2-5.txt:352
technical/biomed/1471-2334-2-6.txt:341
technical/biomed/1471-2334-2-7.txt:408
technical/biomed/1471-2334-3-10.txt:362
technical/biomed/1471-2334-3-11.txt:379
technical/biomed/1471-2334-3-12.txt:277
technical/biomed/1471-2334-3-13.txt:116
technical/biomed/1471-2334-3-15.txt:672
technical/biomed/1471-2334-3-9.txt:354
technical/biomed/1471-2350-2-11.txt:327
technical/biomed/1471-2350-2-12.txt:242
technical/biomed/1471-2350-2-2.txt:367
technical/biomed/1471-2350-2-8.txt:209
technical/biomed/1471-2350-3-1.txt:794
technical/biomed/1471-2350-3-12.txt:708
technical/biomed/1471-2350-3-7.txt:267
technical/biomed/1471-2350-3-9.txt:390
technical/biomed/1471-2350-4-2.txt:634
technical/biomed/1471-2350-4-3.txt:470
technical/biomed/1471-2350-4-4.txt:250
technical/biomed/1471-2350-4-6.txt:611
technical/biomed/1471-2369-3-1.txt:381
technical/biomed/1471-2369-3-10.txt:362
technical/biomed/1471-2369-3-6.txt:263
technical/biomed/1471-2369-3-9.txt:368
technical/biomed/1471-2369-4-1.txt:328
technical/biomed/1471-2369-4-5.txt:287
technical/biomed/1471-2377-1-2.txt:219
technical/biomed/1471-2377-2-4.txt:403
technical/biomed/1471-2377-2-6.txt:311
technical/biomed/1471-2377-3-4.txt:832
technical/biomed/1471-2407-1-13.txt:409
technical/biomed/1471-2407-1-15.txt:560
technical/biomed/1471-2407-1-19.txt:328
technical/biomed/1471-2407-1-6.txt:324
technical/biomed/1471-2407-2-11.txt:436
technical/biomed/1471-2407-2-12.txt:306
technical/biomed/1471-2407-2-15.txt:432
technical/biomed/1471-2407-2-16.txt:343
technical/biomed/1471-2407-2-17.txt:678
technical/biomed/1471-2407-2-18.txt:443
technical/biomed/1471-2407-2-19.txt:501
technical/biomed/1471-2407-2-22.txt:351
technical/biomed/1471-2407-2-23.txt:296
technical/biomed/1471-2407-2-3.txt:420
technical/biomed/1471-2407-2-31.txt:299
technical/biomed/1471-2407-2-33.txt:505
technical/biomed/1471-2407-2-8.txt:273
technical/biomed/1471-2407-2-9.txt:227
technical/biomed/1471-2407-3-14.txt:362
technical/biomed/1471-2407-3-15.txt:350
technical/biomed/1471-2407-3-16.txt:359
technical/biomed/1471-2407-3-18.txt:630
technical/biomed/1471-2407-3-3.txt:589
technical/biomed/1471-2407-3-4.txt:453
technical/biomed/1471-2407-3-5.txt:381
technical/biomed/1471-2415-3-1.txt:370
technical/biomed/1471-2415-3-3.txt:520
technical/biomed/1471-2415-3-4.txt:364
technical/biomed/1471-2415-3-5.txt:766
technical/biomed/1471-2431-2-1.txt:450
technical/biomed/1471-2431-2-11.txt:335
technical/biomed/1471-2431-2-12.txt:436
technical/biomed/1471-2431-2-4.txt:270
technical/biomed/1471-2431-3-3.txt:341
technical/biomed/1471-2431-3-4.txt:612
technical/biomed/1471-2431-3-5.txt:551
technical/biomed/1471-2431-3-6.txt:321
technical/biomed/1471-244X-2-9.txt:488
technical/biomed/1471-244X-3-5.txt:328
technical/biomed/1471-2458-1-9.txt:509
technical/biomed/1471-2458-2-11.txt:442
technical/biomed/1471-2458-2-16.txt:451
technical/biomed/1471-2458-2-18.txt:257
technical/biomed/1471-2458-2-21.txt:381
technical/biomed/1471-2458-2-25.txt:646
technical/biomed/1471-2458-2-3.txt:504
technical/biomed/1471-2458-2-6.txt:521
technical/biomed/1471-2458-3-11.txt:550
technical/biomed/1471-2458-3-2.txt:506
technical/biomed/1471-2458-3-20.txt:367
technical/biomed/1471-2458-3-5.txt:431
technical/biomed/1471-2458-3-9.txt:342
technical/biomed/1471-2466-1-1.txt:342
technical/biomed/1471-2466-2-3.txt:547
technical/biomed/1471-2466-2-4.txt:324
technical/biomed/1471-2466-3-1.txt:257
technical/biomed/1471-2474-2-1.txt:309
technical/biomed/1471-2474-2-2.txt:413
technical/biomed/1471-2474-2-3.txt:411
technical/biomed/1471-2474-3-23.txt:428
technical/biomed/1471-2474-3-3.txt:359
technical/biomed/1471-2474-4-4.txt:374
technical/biomed/1471-2474-4-8.txt:385
technical/biomed/1471-2490-3-2.txt:112
technical/biomed/1471-5945-1-3.txt:361
technical/biomed/1471-5945-2-13.txt:552
technical/biomed/1471-5945-3-3.txt:213
technical/biomed/1472-6750-1-11.txt:519
technical/biomed/1472-6750-1-12.txt:399
technical/biomed/1472-6750-1-13.txt:412
technical/biomed/1472-6750-1-6.txt:476
technical/biomed/1472-6750-1-8.txt:469
technical/biomed/1472-6750-2-10.txt:334
technical/biomed/1472-6750-2-13.txt:304
technical/biomed/1472-6750-2-14.txt:717
technical/biomed/1472-6750-2-2.txt:425
technical/biomed/1472-6750-2-21.txt:520
technical/biomed/1472-6750-3-11.txt:240
technical/biomed/1472-6750-3-4.txt:544
technical/biomed/1472-6750-3-6.txt:550
technical/biomed/1472-6769-1-1.txt:590
technical/biomed/1472-6769-1-2.txt:279
technical/biomed/1472-6769-1-3.txt:264
technical/biomed/1472-6769-1-4.txt:149
technical/biomed/1472-6785-1-3.txt:369
technical/biomed/1472-6785-1-5.txt:599
technical/biomed/1472-6785-2-6.txt:387
technical/biomed/1472-6785-2-7.txt:682
technical/biomed/1472-6793-1-11.txt:340
technical/biomed/1472-6793-1-12.txt:417
technical/biomed/1472-6793-1-15.txt:451
technical/biomed/1472-6793-1-2.txt:534
technical/biomed/1472-6793-1-6.txt:305
technical/biomed/1472-6793-1-8.txt:598
technical/biomed/1472-6793-2-1.txt:454
technical/biomed/1472-6793-2-11.txt:549
technical/biomed/1472-6793-2-16.txt:425
technical/biomed/1472-6793-2-17.txt:386
technical/biomed/1472-6793-2-18.txt:864
technical/biomed/1472-6793-2-19.txt:468
technical/biomed/1472-6793-2-2.txt:584
technical/biomed/1472-6793-2-4.txt:427
technical/biomed/1472-6793-2-5.txt:527
technical/biomed/1472-6793-2-8.txt:584
technical/biomed/1472-6793-3-3.txt:278
technical/biomed/1472-6793-3-4.txt:417
technical/biomed/1472-6793-3-5.txt:428
technical/biomed/1472-6793-3-6.txt:471
technical/biomed/1472-6807-1-1.txt:268
technical/biomed/1472-6807-2-1.txt:338
technical/biomed/1472-6807-2-2.txt:299
technical/biomed/1472-6807-2-3.txt:832
technical/biomed/1472-6807-2-4.txt:826
technical/biomed/1472-6807-2-5.txt:217
technical/biomed/1472-6807-2-9.txt:314
technical/biomed/1472-6807-3-1.txt:1107
technical/biomed/1472-6807-3-2.txt:294
technical/biomed/1472-6815-2-3.txt:554
technical/biomed/1472-6823-2-2.txt:279
technical/biomed/1472-6823-3-1.txt:512
technical/biomed/1472-6831-2-2.txt:414
technical/biomed/1472-6831-3-1.txt:502
technical/biomed/1472-684X-1-5.txt:857
technical/biomed/1472-684X-2-1.txt:410
technical/biomed/1472-684X-2-2.txt:478
technical/biomed/1472-6874-2-1.txt:275
technical/biomed/1472-6874-2-13.txt:577
technical/biomed/1472-6874-2-8.txt:303
technical/biomed/1472-6874-3-2.txt:315
technical/biomed/1472-6882-1-10.txt:1362
technical/biomed/1472-6882-1-11.txt:511
technical/biomed/1472-6882-1-12.txt:507
technical/biomed/1472-6882-1-7.txt:414
technical/biomed/1472-6882-2-10.txt:333
technical/biomed/1472-6882-2-5.txt:243
technical/biomed/1472-6882-3-1.txt:778
technical/biomed/1472-6882-3-3.txt:623
technical/biomed/1472-6890-1-4.txt:654
technical/biomed/1472-6890-2-5.txt:289
technical/biomed/1472-6890-3-2.txt:561
technical/biomed/1472-6904-1-2.txt:489
technical/biomed/1472-6904-2-4.txt:612
technical/biomed/1472-6904-2-5.txt:1547
technical/biomed/1472-6904-2-7.txt:795
technical/biomed/1472-6904-3-1.txt:1011
technical/biomed/1472-6920-1-3.txt:362
technical/biomed/1472-6920-2-1.txt:501
technical/biomed/1472-6920-2-3.txt:314
technical/biomed/1472-6947-1-2.txt:265
technical/biomed/1472-6947-1-5.txt:312
technical/biomed/1472-6947-1-6.txt:545
technical/biomed/1472-6947-2-4.txt:565
technical/biomed/1472-6947-2-7.txt:708
technical/biomed/1472-6947-3-5.txt:601
technical/biomed/1472-6947-3-8.txt:630
technical/biomed/1472-6955-2-1.txt:410
technical/biomed/1472-6963-1-11.txt:345
technical/biomed/1472-6963-1-8.txt:439
technical/biomed/1472-6963-2-10.txt:516
technical/biomed/1472-6963-3-1.txt:424
technical/biomed/1472-6963-3-11.txt:275
technical/biomed/1472-6963-3-12.txt:374
technical/biomed/1472-6963-3-13.txt:335
technical/biomed/1472-6963-3-14.txt:688
technical/biomed/1472-6963-3-6.txt:405
technical/biomed/1472-6963-3-7.txt:594
technical/biomed/1475-2832-1-1.txt:397
technical/biomed/1475-2867-2-10.txt:388
technical/biomed/1475-2867-2-15.txt:342
technical/biomed/1475-2867-2-7.txt:269
technical/biomed/1475-2867-3-12.txt:402
technical/biomed/1475-2867-3-2.txt:413
technical/biomed/1475-2867-3-3.txt:394
technical/biomed/1475-2867-3-4.txt:486
technical/biomed/1475-2875-1-14.txt:519
technical/biomed/1475-2875-1-5.txt:407
technical/biomed/1475-2875-2-10.txt:579
technical/biomed/1475-2875-2-14.txt:626
technical/biomed/1475-2875-2-4.txt:478
technical/biomed/1475-2883-2-11.txt:395
technical/biomed/1475-2891-1-2.txt:421
technical/biomed/1475-2891-2-1.txt:434
technical/biomed/1475-4924-1-10.txt:974
technical/biomed/1475-4924-1-5.txt:492
technical/biomed/1475-925X-2-1.txt:409
technical/biomed/1475-925X-2-10.txt:650
technical/biomed/1475-925X-2-11.txt:255
technical/biomed/1475-925X-2-12.txt:388
technical/biomed/1475-925X-2-3.txt:317
technical/biomed/1475-925X-2-6.txt:1174
technical/biomed/1475-9268-1-1.txt:645
technical/biomed/1475-9268-1-2.txt:274
technical/biomed/1475-9276-1-3.txt:449
technical/biomed/1476-069X-1-3.txt:448
technical/biomed/1476-069X-2-2.txt:523
technical/biomed/1476-069X-2-4.txt:872
technical/biomed/1476-069X-2-7.txt:439
technical/biomed/1476-069X-2-9.txt:1205
technical/biomed/1476-0711-2-3.txt:319
technical/biomed/1476-0711-2-7.txt:452
technical/biomed/1476-072X-2-3.txt:487
technical/biomed/1476-072X-2-4.txt:862
technical/biomed/1476-4598-1-3.txt:338
technical/biomed/1476-4598-1-5.txt:219
technical/biomed/1476-4598-1-6.txt:494
technical/biomed/1476-4598-1-8.txt:517
technical/biomed/1476-4598-2-1.txt:398
technical/biomed/1476-4598-2-2.txt:239
technical/biomed/1476-4598-2-20.txt:407
technical/biomed/1476-4598-2-22.txt:183
technical/biomed/1476-4598-2-24.txt:718
technical/biomed/1476-4598-2-25.txt:499
technical/biomed/1476-4598-2-28.txt:518
technical/biomed/1476-4598-2-3.txt:260
technical/biomed/1476-511X-1-2.txt:1227
technical/biomed/1476-511X-2-2.txt:442
technical/biomed/1476-511X-2-3.txt:346
technical/biomed/1476-5918-1-2.txt:297
technical/biomed/1476-9433-1-2.txt:537
technical/biomed/1476-9433-1-3.txt:316
technical/biomed/1477-5956-1-1.txt:327
technical/biomed/1477-7525-1-10.txt:391
technical/biomed/1477-7525-1-12.txt:258
technical/biomed/1477-7525-1-9.txt:430
technical/biomed/1477-7819-1-10.txt:183
technical/biomed/1477-7827-1-13.txt:824
technical/biomed/1477-7827-1-17.txt:483
technical/biomed/1477-7827-1-21.txt:313
technical/biomed/1477-7827-1-23.txt:493
technical/biomed/1477-7827-1-27.txt:378
technical/biomed/1477-7827-1-31.txt:640
technical/biomed/1477-7827-1-36.txt:775
technical/biomed/1477-7827-1-43.txt:632
technical/biomed/1477-7827-1-46.txt:754
technical/biomed/1477-7827-1-48.txt:416
technical/biomed/1477-7827-1-54.txt:532
technical/biomed/1477-7827-1-6.txt:333
technical/biomed/1477-7827-1-9.txt:673
technical/biomed/1478-1336-1-2.txt:338
technical/biomed/1478-1336-1-3.txt:369
technical/biomed/1478-1336-1-4.txt:521
technical/biomed/1478-7954-1-3.txt:587
technical/biomed/ar104.txt:535
technical/biomed/ar118.txt:571
technical/biomed/ar120.txt:463
technical/biomed/ar130.txt:690
technical/biomed/ar140.txt:592
technical/biomed/ar149.txt:352
technical/biomed/ar297.txt:311
technical/biomed/ar309.txt:275
technical/biomed/ar319.txt:405
technical/biomed/ar321.txt:379
technical/biomed/ar328.txt:259
technical/biomed/ar331.txt:225
technical/biomed/ar383.txt:231
technical/biomed/ar387.txt:297
technical/biomed/ar407.txt:395
technical/biomed/ar408.txt:416
technical/biomed/ar409.txt:461
technical/biomed/ar422.txt:483
technical/biomed/ar429.txt:290
technical/biomed/ar430.txt:290
technical/biomed/ar601.txt:239
technical/biomed/ar612.txt:445
technical/biomed/ar615.txt:485
technical/biomed/ar619.txt:310
technical/biomed/ar624.txt:410
technical/biomed/ar68.txt:474
technical/biomed/ar745.txt:347
technical/biomed/ar750.txt:292
technical/biomed/ar774.txt:406
technical/biomed/ar778.txt:598
technical/biomed/ar79.txt:535
technical/biomed/ar792.txt:309
technical/biomed/ar795.txt:316
technical/biomed/ar799.txt:419
technical/biomed/ar93.txt:489
technical/biomed/bcr273.txt:698
technical/biomed/bcr284.txt:499
technical/biomed/bcr285.txt:559
technical/biomed/bcr294.txt:334
technical/biomed/bcr303.txt:492
technical/biomed/bcr317.txt:402
technical/biomed/bcr45.txt:520
technical/biomed/bcr458.txt:342
technical/biomed/bcr567.txt:274
technical/biomed/bcr568.txt:371
technical/biomed/bcr570.txt:308
technical/biomed/bcr571.txt:343
technical/biomed/bcr583.txt:299
technical/biomed/bcr588.txt:348
technical/biomed/bcr602.txt:247
technical/biomed/bcr605.txt:683
technical/biomed/bcr607.txt:337
technical/biomed/bcr618.txt:402
technical/biomed/bcr620.txt:499
technical/biomed/bcr631.txt:696
technical/biomed/bcr635.txt:220
technical/biomed/cc103.txt:508
technical/biomed/cc1044.txt:261
technical/biomed/cc105.txt:318
technical/biomed/cc1476.txt:588
technical/biomed/cc1477.txt:388
technical/biomed/cc1495.txt:280
technical/biomed/cc1497.txt:273
technical/biomed/cc1498.txt:384
technical/biomed/cc1529.txt:437
technical/biomed/cc1538.txt:502
technical/biomed/cc1547.txt:253
technical/biomed/cc1843.txt:265
technical/biomed/cc1852.txt:503
technical/biomed/cc1856.txt:347
technical/biomed/cc1882.txt:397
technical/biomed/cc2160.txt:297
technical/biomed/cc2167.txt:507
technical/biomed/cc2171.txt:463
technical/biomed/cc2172.txt:401
technical/biomed/cc2190.txt:314
technical/biomed/cc2358.txt:307
technical/biomed/cc3.txt:407
technical/biomed/cc300.txt:351
technical/biomed/cc303.txt:549
technical/biomed/cc343.txt:363
technical/biomed/cc350.txt:249
technical/biomed/cc367.txt:319
technical/biomed/cc4.txt:746
technical/biomed/cc713.txt:194
technical/biomed/cc973.txt:177
technical/biomed/cc991.txt:453
technical/biomed/cvm-2-1-038.txt:330
technical/biomed/cvm-2-4-180.txt:334
technical/biomed/cvm-2-4-187.txt:435
technical/biomed/cvm-2-6-278.txt:429
technical/biomed/cvm-2-6-286.txt:314
technical/biomed/gb-2000-1-1-research002.txt:396
technical/biomed/gb-2000-1-2-research0003.txt:580
technical/biomed/gb-2001-2-10-research0041.txt:588
technical/biomed/gb-2001-2-10-research0042.txt:769
technical/biomed/gb-2001-2-11-research0045.txt:604
technical/biomed/gb-2001-2-11-research0046.txt:901
technical/biomed/gb-2001-2-12-research0051.txt:593
technical/biomed/gb-2001-2-12-research0053.txt:433
technical/biomed/gb-2001-2-12-research0054.txt:746
technical/biomed/gb-2001-2-12-research0055.txt:841
technical/biomed/gb-2001-2-2-research0004.txt:535
technical/biomed/gb-2001-2-3-research0007.txt:366
technical/biomed/gb-2001-2-3-research0008.txt:531
technical/biomed/gb-2001-2-4-research0010.txt:781
technical/biomed/gb-2001-2-4-research0011.txt:773
technical/biomed/gb-2001-2-4-research0012.txt:580
technical/biomed/gb-2001-2-4-research0014.txt:576
technical/biomed/gb-2001-2-6-research0018.txt:639
technical/biomed/gb-2001-2-6-research0020.txt:457
technical/biomed/gb-2001-2-6-research0021.txt:585
technical/biomed/gb-2001-2-7-research0024.txt:726
technical/biomed/gb-2001-2-7-research0025.txt:1101
technical/biomed/gb-2001-2-8-research0027.txt:647
technical/biomed/gb-2001-2-8-research0030.txt:895
technical/biomed/gb-2001-2-8-research0031.txt:925
technical/biomed/gb-2001-2-8-research0032.txt:432
technical/biomed/gb-2001-2-9-research0035.txt:372
technical/biomed/gb-2001-2-9-research0037.txt:810
technical/biomed/gb-2001-3-1-research0001.txt:985
technical/biomed/gb-2001-3-1-research0004.txt:443
technical/biomed/gb-2001-3-1-research0005.txt:408
technical/biomed/gb-2002-3-10-research0052.txt:550
technical/biomed/gb-2002-3-10-research0053.txt:579
technical/biomed/gb-2002-3-10-research0054.txt:516
technical/biomed/gb-2002-3-10-research0055.txt:774
technical/biomed/gb-2002-3-10-research0056.txt:688
technical/biomed/gb-2002-3-11-research0059.txt:1225
technical/biomed/gb-2002-3-11-research0060.txt:458
technical/biomed/gb-2002-3-11-research0061.txt:418
technical/biomed/gb-2002-3-11-research0062.txt:681
technical/biomed/gb-2002-3-11-research0065.txt:860
technical/biomed/gb-2002-3-12-research0071.txt:1000
technical/biomed/gb-2002-3-12-research0072.txt:1157
technical/biomed/gb-2002-3-12-research0075.txt:354
technical/biomed/gb-2002-3-12-research0077.txt:675
technical/biomed/gb-2002-3-12-research0078.txt:528
technical/biomed/gb-2002-3-12-research0079.txt:903
technical/biomed/gb-2002-3-12-research0080.txt:382
technical/biomed/gb-2002-3-12-research0081.txt:700
technical/biomed/gb-2002-3-12-research0082.txt:734
technical/biomed/gb-2002-3-12-research0083.txt:1447
technical/biomed/gb-2002-3-12-research0085.txt:766
technical/biomed/gb-2002-3-12-research0086.txt:1611
technical/biomed/gb-2002-3-12-research0087.txt:689
technical/biomed/gb-2002-3-12-research0088.txt:824
technical/biomed/gb-2002-3-2-research0008.txt:704
technical/biomed/gb-2002-3-2-research0009.txt:477
technical/biomed/gb-2002-3-3-research0011.txt:973
technical/biomed/gb-2002-3-3-research0012.txt:501
technical/biomed/gb-2002-3-4-research0018.txt:576
technical/biomed/gb-2002-3-4-research0019.txt:627
technical/biomed/gb-2002-3-5-research0020.txt:586
technical/biomed/gb-2002-3-5-research0021.txt:610
technical/biomed/gb-2002-3-5-research0022.txt:1142
technical/biomed/gb-2002-3-5-research0023.txt:295
technical/biomed/gb-2002-3-5-research0024.txt:627
technical/biomed/gb-2002-3-5-research0025.txt:829
technical/biomed/gb-2002-3-6-research0029.txt:422
technical/biomed/gb-2002-3-6-software0001.txt:524
technical/biomed/gb-2002-3-7-research0032.txt:450
technical/biomed/gb-2002-3-7-research0035.txt:796
technical/biomed/gb-2002-3-7-research0036.txt:1677
technical/biomed/gb-2002-3-7-research0037.txt:892
technical/biomed/gb-2002-3-8-research0038.txt:755
technical/biomed/gb-2002-3-8-research0039.txt:311
technical/biomed/gb-2002-3-8-research0040.txt:417
technical/biomed/gb-2002-3-9-research0043.txt:910
technical/biomed/gb-2002-3-9-research0044.txt:497
technical/biomed/gb-2002-3-9-research0045.txt:900
technical/biomed/gb-2002-3-9-research0046.txt:575
technical/biomed/gb-2002-3-9-research0048.txt:907
technical/biomed/gb-2002-3-9-research0049.txt:465
technical/biomed/gb-2002-3-9-research0051.txt:859
technical/biomed/gb-2002-4-1-r1.txt:466
technical/biomed/gb-2002-4-1-r2.txt:825
technical/biomed/gb-2003-4-1-r5.txt:710
technical/biomed/gb-2003-4-1-r7.txt:492
technical/biomed/gb-2003-4-2-r11.txt:663
technical/biomed/gb-2003-4-2-r14.txt:1170
technical/biomed/gb-2003-4-2-r16.txt:478
technical/biomed/gb-2003-4-2-r8.txt:765
technical/biomed/gb-2003-4-2-r9.txt:856
technical/biomed/gb-2003-4-3-r17.txt:893
technical/biomed/gb-2003-4-3-r18.txt:292
technical/biomed/gb-2003-4-3-r20.txt:826
technical/biomed/gb-2003-4-4-r24.txt:706
technical/biomed/gb-2003-4-4-r26.txt:1032
technical/biomed/gb-2003-4-4-r28.txt:469
technical/biomed/gb-2003-4-5-r30.txt:418
technical/biomed/gb-2003-4-5-r32.txt:665
technical/biomed/gb-2003-4-5-r34.txt:1452
technical/biomed/gb-2003-4-6-r37.txt:659
technical/biomed/gb-2003-4-6-r39.txt:934
technical/biomed/gb-2003-4-6-r41.txt:506
technical/biomed/gb-2003-4-7-r42.txt:1061
technical/biomed/gb-2003-4-7-r43.txt:1329
technical/biomed/gb-2003-4-7-r46.txt:578
technical/biomed/gb-2003-4-8-r50.txt:411
technical/biomed/gb-2003-4-8-r51.txt:339
technical/biomed/gb-2003-4-9-r57.txt:607
technical/biomed/gb-2003-4-9-r58.txt:521
technical/biomed/gb-2003-4-9-r60.txt:451
technical/biomed/rr166.txt:369
technical/biomed/rr167.txt:568
technical/biomed/rr171.txt:561
technical/biomed/rr172.txt:375
technical/biomed/rr191.txt:434
technical/biomed/rr196.txt:596
technical/biomed/rr37.txt:496
technical/biomed/rr73.txt:291
technical/biomed/rr74.txt:360
```

The second option I explored was `-A n` where `n` refers to a number. The command is described as printing the lines with the matching pattern and `n` number of lines after it. I used: `grep -A 1 "carcinogenic" technical/biomed/*.txt` as my input and got an output of lines that contained the found pattern where each line also had another line under it from the same file of each. This is useful for getting context for long sentences that take up multiple lines per file. The output is:
```
technical/biomed/1471-2105-3-26.txt:        tumors in animal carcinogenicity studies, and the
technical/biomed/1471-2105-3-26.txt-        development of more pertinent animal xenograft models of
--
technical/biomed/1471-2156-3-22.txt:        carcinogenic insults is offered in a report by Schantz et
technical/biomed/1471-2156-3-22.txt-        al., showing the highest levels of chromosomal sensitivity
--
technical/biomed/1471-2156-3-22.txt:        a family of transcription factors known to be carcinogenic.
technical/biomed/1471-2156-3-22.txt-        Evidence suggests that gain of function in PAX7 triggers
--
technical/biomed/1471-2210-2-8.txt:        taken from the FDA rodent carcinogenicity database [ 35 ] .
technical/biomed/1471-2210-2-8.txt-        Results (Table 2) demonstrate good specificity of the
--
technical/biomed/1471-2210-2-8.txt:        metabolites against carcinogenicity and mutagenicity
technical/biomed/1471-2210-2-8.txt-        databases [ 35 ] , [ 36 ] .
--
technical/biomed/1471-2407-3-4.txt:        "preconditioned" by chronic exposure to carcinogenic
technical/biomed/1471-2407-3-4.txt-        agents, thus priming them for the subsequent development of
--
technical/biomed/1472-6882-1-10.txt:        carcinogenic risk cited in the literature on aristolochic
technical/biomed/1472-6882-1-10.txt-        acid [ 61 ] needs to be evaluated versus its potential
--
technical/biomed/1472-6947-3-8.txt:            our understanding of the carcinogenic process, they
technical/biomed/1472-6947-3-8.txt-            were collected as a separate listing. When the
--
technical/biomed/bcr583.txt:        carcinogenic exposures. Among atomic bomb survivors and
technical/biomed/bcr583.txt-        women exposed to ionizing radiation as part of their
```

The third option I explored was `-B n` where `n` refers to a number. The command is described as printing the lines with the matching pattern and `n` number of lines before it. I used: `grep -B 1 "carcinogenic" technical/biomed/*.txt` as my input and got an output of lines that contained the found pattern where each line also had another line above it from the same file of each. This is also useful for getting context for long sentences that take up multiple lines per file. The output is:
```
$ grep -B 1 "carcinogenic" technical/biomed/*.txt
technical/biomed/1471-2105-3-26.txt-        assessment of relevance to human safety of drug-associated
technical/biomed/1471-2105-3-26.txt:        tumors in animal carcinogenicity studies, and the
--
technical/biomed/1471-2156-3-22.txt-        suggesting that non-smokers may respond differently to
technical/biomed/1471-2156-3-22.txt:        carcinogenic insults is offered in a report by Schantz et
--
technical/biomed/1471-2156-3-22.txt-        candidate oncogenes in this region [ 21 ] . PAX7 is part of
technical/biomed/1471-2156-3-22.txt:        a family of transcription factors known to be carcinogenic.
--
technical/biomed/1471-2210-2-8.txt-        a large group of structurally diverse molecules, which were
technical/biomed/1471-2210-2-8.txt:        taken from the FDA rodent carcinogenicity database [ 35 ] .
--
technical/biomed/1471-2210-2-8.txt-        assessed by testing each candidate and its predicted
technical/biomed/1471-2210-2-8.txt:        metabolites against carcinogenicity and mutagenicity
--
technical/biomed/1471-2407-3-4.txt-        epithelium, although normal in appearance, are
technical/biomed/1471-2407-3-4.txt:        "preconditioned" by chronic exposure to carcinogenic
--
technical/biomed/1472-6882-1-10.txt-        showed good potential against crotalid venoms. The
technical/biomed/1472-6882-1-10.txt:        carcinogenic risk cited in the literature on aristolochic
--
technical/biomed/1472-6947-3-8.txt-            Since these syndromes may have enormous relevance to
technical/biomed/1472-6947-3-8.txt:            our understanding of the carcinogenic process, they
--
technical/biomed/bcr583.txt-        vulnerability of the adolescent breast tissue to
technical/biomed/bcr583.txt:        carcinogenic exposures. Among atomic bomb survivors and
```

The fourth option I explored was `-C n` where `n` refers to a number. The command is described as printing the lines with the matching pattern and `n` number of lines before and after it. Basically, it combined the second and third commands I explored earlier. I used: `grep -C 1 "carcinogenic" technical/biomed/*.txt` as my input. This time, each line was preceded by 1 line before it and 1 line after it, which did not have the matching pattern but was added because I specified `1` in my command again. As seen below, we can see that `-C n` really is a combination of `-A -n` and `-B -n`. This is better than both prior commands for getting full context. The output is:
```
technical/biomed/1471-2105-3-26.txt-        assessment of relevance to human safety of drug-associated
technical/biomed/1471-2105-3-26.txt:        tumors in animal carcinogenicity studies, and the
technical/biomed/1471-2105-3-26.txt-        development of more pertinent animal xenograft models of
--
technical/biomed/1471-2156-3-22.txt-        suggesting that non-smokers may respond differently to
technical/biomed/1471-2156-3-22.txt:        carcinogenic insults is offered in a report by Schantz et
technical/biomed/1471-2156-3-22.txt-        al., showing the highest levels of chromosomal sensitivity
--
technical/biomed/1471-2156-3-22.txt-        candidate oncogenes in this region [ 21 ] . PAX7 is part of
technical/biomed/1471-2156-3-22.txt:        a family of transcription factors known to be carcinogenic.
technical/biomed/1471-2156-3-22.txt-        Evidence suggests that gain of function in PAX7 triggers
--
technical/biomed/1471-2210-2-8.txt-        a large group of structurally diverse molecules, which were
technical/biomed/1471-2210-2-8.txt:        taken from the FDA rodent carcinogenicity database [ 35 ] .
technical/biomed/1471-2210-2-8.txt-        Results (Table 2) demonstrate good specificity of the
--
technical/biomed/1471-2210-2-8.txt-        assessed by testing each candidate and its predicted
technical/biomed/1471-2210-2-8.txt:        metabolites against carcinogenicity and mutagenicity
technical/biomed/1471-2210-2-8.txt-        databases [ 35 ] , [ 36 ] .
--
technical/biomed/1471-2407-3-4.txt-        epithelium, although normal in appearance, are
technical/biomed/1471-2407-3-4.txt:        "preconditioned" by chronic exposure to carcinogenic
technical/biomed/1471-2407-3-4.txt-        agents, thus priming them for the subsequent development of
--
technical/biomed/1472-6882-1-10.txt-        showed good potential against crotalid venoms. The
technical/biomed/1472-6882-1-10.txt:        carcinogenic risk cited in the literature on aristolochic
technical/biomed/1472-6882-1-10.txt-        acid [ 61 ] needs to be evaluated versus its potential
--
technical/biomed/1472-6947-3-8.txt-            Since these syndromes may have enormous relevance to
technical/biomed/1472-6947-3-8.txt:            our understanding of the carcinogenic process, they
technical/biomed/1472-6947-3-8.txt-            were collected as a separate listing. When the
--
technical/biomed/bcr583.txt-        vulnerability of the adolescent breast tissue to
technical/biomed/bcr583.txt:        carcinogenic exposures. Among atomic bomb survivors and
technical/biomed/bcr583.txt-        women exposed to ionizing radiation as part of their
```
