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
![Image](Screenshot 2023-11-05 175422)

Screenshot with passing test:
![Image](Screenshot 2023-11-05 175457)

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
I googled and used: https://www.geeksforgeeks.org/grep-command-in-unixlinux/ to research each of the `grep` commands.

The first option I explored was `-v` which is described as printing the lines that do not match the given string. I used: `grep -v "biomed" technical` as an input and got `grep: technical: Is a directory` as an output. This is because the `grep` command is for files not directories (for the other commands, I will not try it on directories as the result is redundant). I then used `grep -v -c "1" technical/biomed/*.txt > name.txt` to put all printed results into a file `name.txt`. I ended up finding 837 file names in it. None of the file names had the number 1 in it. There was no output because I used `>` to store the names instead of printing to the terminal because there would be too many files to print out.

The second option I explored was `-A n` where `n` refers to a number. The command is described as printing the lines with the matching pattern and `n` number of lines after it. I used: `grep -A 1 "carcinogenic" technical/biomed/*.txt > name.txt` as my input and got no output because I redirected it into the `name.txt` file again. This time, I got 9 matching lines and each line was followed by another line under it which did not have the matching pattern but was added because I specified `1` in my command. The lines from different files were separated by `--`.

The third option I explored was `-B n` where `n` refers to a number. The command is described as printing the lines with the matching pattern and `n` number of lines before it. I used: `grep -B 1 "carcinogenic" technical/biomed/*.txt > name.txt` as my input and got no output because I redirected it into the `name.txt` file again. This time, I got 9 matching lines and each line was preceded by another line before it which did not have the matching pattern but was added because I specified `1` in my command again. Again, the lines from different files were separated by `--`.

The fourth option I explored was `-C n` where `n` refers to a number. The command is described as printing the lines with the matching pattern and `n` number of lines before and after it. Basically it combined the second and third commands I explored earlier. I used: `grep -C 1 "carcinogenic" technical/biomed/*.txt > name.txt` as my input and got no output because I redirected it into the `name.txt` file again. This time, I got 9 matching lines and each line was preceded by 1 line before it and 1 line after it, which did not have the matching pattern but was added because I specified `1` in my command again. Again, the lines from different files were separated by `--`.
