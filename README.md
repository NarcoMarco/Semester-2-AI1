# Semester-2-AI1
2024 Semester 2 ai1 assignment


## OS_Revision009
```
ssh os_revision009@10.13.37.10
password: os_revision009
```
List files and Check hint
```
ls -la
cat secret.hint
```
Check contents of 'secret file'
```
cat secret
```
In this it gives a string that looks like a flag, but is not:
```
6fa1b41f5a40b34ca707c6d36a231d79
```
Pass this into the secret program
```
./secret 6fa1b41f5a40b34ca707c6d36a231d79
```
The output of this gives you the flag
```
CTF FFlag: ae87a47a1b8a6eb58843ce6967ab201f
```
