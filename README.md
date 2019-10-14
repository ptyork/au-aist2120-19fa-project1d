# Project 1d: ROT13 Cipher

You are to implement a very simple encoder and decoder using the classic [ROT13 Cipher](http://www.crypto-it.net/eng/simple/rot13.html). Don't worry, it looks WAY worse than it actually is.

The script, `encrypt.py`, should: 

1. Ask the user for a file name
2. Open the requested file 
3. Iterate over each line in the file. For each:
    - strip() any extra spaces or newlines from the beginning or end of the line
    - create an empty list called `chars` (will hold each character)
    - now you want to iterate over each CHARACTER in the line. For each:
        - If the character is NOT a character in [A-Za-z] (use isalpha()), just append it to your `chars` list and continue (skip) to the next character
        - Convert the character to upper case
        - Use the `ord()` funciton to retrieve the ordinal value of the character and store it in a `chnum` variable (will be between 65 for 'A' and 90 for 'Z')
        - Subtract from `chnum` 65 to give you a value between 0 and 25
        - Add 13 to `chnum` (value will be between 13 and 38)
        - Get the remainder of `chnum` when dividing by 26 (i.e., `chnum = chnum % 26`--character values of 13 to 25 stay the same, but values of 26 to 38 become 0 to 12 because that's the remainder when dividing by 26)
        - Add 65 back to `chnum` (again get a number from 65 to 90)
        - Convert `chnum` back to a character using the `chr()` function and append that character to `chars`
        - The end result is that 'A' becomes 'N', 'B' becomes 'O', 'C' becomes 'P' and so on
    - join() the characters in `chars` back together again to form an encrypted line
5. Print each encrypted line to the screen

Most of step 4 is just performing some fifth-grade math to make it easy to shift each character 13 places to the right. Do your best to REALLY understand what that is doing. That kind of numerical manipulation of characters can be VERY handy, especially in the world of cyber security. 

This particular cipher is pretty neat in that the same cipher both ENcodes and DEcodes the text. In fact, if you do your job right, you should be able to run your script agains the `sample-encrypted-testmsg.txt` and you'll get a the original message back (well, all upper case). Of course, it's perhaps the least secure cipher imaginable, so, you know, don't ever, EVER use it.

## REQUIRED IMPLEMENTATION NOTES 

1. You MUST abstract your most useful logic by creating a function named `encryptline` that takes string as a parameter and returns the encoded string. This function should be "called" as your step 4 above, which will make the main script much cleaner. So to reiterate, the following function MUST be in your code: 
``` 
        def encryptline(str): 
            ...
            return encryptedstr
``` 
2. You MUST edit `testmsg.txt` and add a line with __your__ name in it; perhaps something like "Paul York was here".

3. You MUST run your script against the edited version of  `testmsg.txt` and redirect the output to `encrypted-testmsg.txt`. In other words, you should run `python encrypt.py > encrypted-testmsg.txt` and select `testmsg.txt` when prompted. Include this file in your final submission. 

## LOGISTICS 

Same basic deal as with the homeworks. 

1. From your AIST2120 folder, run `git clone [URL]` to make a local copy of this assignment. 
2. DO THE WORK (create and complete any and all needed files)
3. TEST YOUR WORK A WHOLE LOT 
4. TEST IT SOME MORE LIKE YOU MEAN IT THIS TIME 
5. When done, run `git add .` 
6. Then run `git commit –m "type a clever message here"` 
7. Finally run `git push` to push your changes back up to GitHub 
8. Breathe a sigh of relief 

## OPTIONAL CHALLENGES 

1. Create a second version of the script, encrypt2.py. This version should import the encryptline function from encrypt (`from encrypt import encryptline`). Instead of asking for a file name and reading the text from the file, read in the text line-by-line from `sys.stdin`. This should allow you to run it interactively AND to pipe in text from another command (e.g., `type testmsg.txt | python encrypt2.py`). Even cooler here, you can "double-pipe" the output and get the original back (e.g., `type testmsg.txt | python encrypt2.py | python encrypt2.py`)

2. Preserve the correct capitalization by correctly shifting capital letters by 13 (ord values from 65 to 90) AND lower case letters by 13 (ord values from 97 to 122), but leaving all others alone.

3. Do the same as #2, but SWAP lower and upper case characters during the encode and decode process. You know, 'cause it's sooooo much harder to rEAD tEXT wRITTEN lIKE tHIS.

4. Make the shifting "variable". In other words, ask how many characters to shift (13 is "default", but can supply any number).
