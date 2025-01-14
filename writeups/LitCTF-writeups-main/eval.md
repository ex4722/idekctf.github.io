# rev/Evaluation (201 solves/112 points)
## Description: 
Here’s an evaluation copy of my flag checker! I hid the flag in the evaluation copy though…
```
print(eval(eval(eval(eval(eval(eval("''.join([chr(i) for i in [39,39,46,106,111,105,110,40,91,99,104,114,40,105,41,32,102,111,114,32,105,32,105,110,32,91,51,57,44,51,57,44,52,54,44,49,48,54,44,49,49,49,44,49,48,53,44,49,49,48,44,52,48,44,57,49,44,57,57,44,49,48,52,44,49,49,52,44,52,48,44,49,48,53,44,52,49,44,51,50,44,49,48,50,44,49,49,49
...
...
53,50,44,53,55,44,52,52,44,53,55,44,53,49,44,52,52,44,53,55,44,53,49,44,52,52,44,53,50,44,52,57,44,57,51,44,57,51,44,52,49,93,93,41]])")))))))

```

## Solution:
We run this in python and get 
`Enter the flag:`
So this is python obfuscation by packing a giant list with evals. If we take out one of the `eval(` and `)` we get:
`['Correct flag!', 'Incorrect flag :('][''.join(map(lambda x: chr(ord(x)^5), list(input('Enter the flag: ').zfill(36)[::-1])))!='x6wpf6vZ|w6sZq5kZv4Zk54q1fvpcg5~bdic']`
This makes a lot more sense but is still really weird python. We can see that there's a `!=` and some string there conveniently 36 chars just like that `.zfill(36)`. That's probably the flag and is comparing it. We see a `lambda x: chr(ord(x)^5)`, basically meaning xor the char `x` with `5`. Lastly, there's a `[::-1]` which means the string is read reversed. Time to reverse.
`print(''.join([chr(ord(x)^5) for x in 'x6wpf6vZ|w6sZq5kZv4Zk54q1fvpcg5~bdic'])[::-1])` returns `flag{0bfusc4t10n_1s_n0t_v3ry_s3cur3}`. Looks like a flag to me.

## Flag:
flag{0bfusc4t10n_1s_n0t_v3ry_s3cur3}