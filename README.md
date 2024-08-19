# Semester-2-AI1
2024 Semester 2 ai1 assignment

# OS

## "I love cat. I love every kind of cat."

```bash
ssh os_revision000@10.13.37.10
ls
cat secret.flag
```
This returns the flag.

## "hidden attributes"

```bash
ssh os_revision001@10.13.37.10
ls -a
cat .secret.flag
```
This returns the flag.

## "navigating around"

```bash
ssh os_revision002@10.13.37.10
ls
cd inhere/
ls
cat secret.flag
```
This returns the flag.

## "Why did the file go ot the police?"

```bash
ssh os_revision003@10.13.37.10
ls
cd inhere0
ls
file ./*
```
Find the file with type "ASCII text"
```bash
cat flag06
```
This returns the flag.
## "Why did the computer file feel lost?"

```bash
ssh os_revision004@10.13.37.10
ls
find . -name *.flag
cat ./inhere3/file35.flag
```
This returns the flag.

## "What is in a name?"

```bash
ssh os_revision005@10.13.37.10
ls
find . -user adam
cat ./inhere6/file65.flag
```
This returns the flag.

## "Does size count?"

```bash
ssh os_revision006@10.13.37.10
ls
find . -size 33c
cat ./inhere6/fjEkweorWp
```
This returns the flag.

## "That's a lot of words!"

```bash
ssh os_revision007@10.13.37.10
ls
grep hornstone os.revision.007.flag
```
This returns the flag next to the word 'hornstone'

## "What the wget?"

```bash
ssh os_revision008@10.13.37.10
cat secret.hint
```
This will conatain a password. Remember this.
```bash
find / .-name *.7z 2> /dev/null
```
This gives us the name of the file we must wget.

Now, exit the ssh session.
```bash
exit
```

Now, we will download the file.
```bash
wget http://10.13.37.10/secret.flag.7z
7za x secret.flag.7z
```
Enter the password from earlier.
Then, read the extracted file.
```bash
ls
cat secret.flag
```
This will give you the flag.

## It is the strings that matter most!
```bash
ssh os_revision009@10.13.37.10
password: os_revision009
```
List files and Check hint
```bash
ls -la
cat secret.hint
```
Check contents of 'secret file'
```bash
cat secret
```
In this it gives a string that looks like a flag, but is not:
```bash
6fa1b41f5a40b34ca707c6d36a231d79
```
Pass this into the secret program
```bash
./secret 6fa1b41f5a40b34ca707c6d36a231d79
```
The output of this gives you the flag
```bash
CTF Flag: ae87a47a1b8a6eb58843ce6967ab201f
```

# Network Administration

## "Hello Containerlabs"

First, we must create a yaml file on our local machine that conatins the topology of our network.
```bash
nano Hello_Containerlabs.yml
```
Inside the file, we must create the topology.
```yaml
name: reverse_ctf_tester
topology:
  nodes:
    alpine:
      kind: linux
      image: reverse-ctf-server
      ports:
        - "2222:22/tcp"
```
Now, we can deploy the network, as well as check our ip address, which we will need later.
```bash
sudo containerlab deploy -t Hello_Containerlabs.yml
ip a | grep 10.13.37.
```
This challenge requires no configuration on the server, so we now only need to SSH into the server to get the flag.
```bash
ssh networking000@10.13.37.10
password: networking000
```
Now we need to run the reverse-ctf file, and give it our ip address we found earlier (In my case, 10.13.37.55).
```bash
./reverse-ctf 10.13.37.55
```
This should return the flag.

## "Connect test-server to a router"

First, we must create a yaml file on our local machine that conatins the topology of our network.
```bash
nano test-server-router.yml
```
Inside the file, we must create the topology.
```yaml
name: test-server-router
topology:
  nodes:
    test:
      kind: linux
      image: reverse-ctf-server
      ports:
        - "2222:22/tcp"
    r1:
      kind: linux
      image: frrouting/frr:latest
  links:
    - endpoints: ['r1:eth1', 'test:eth1']
```
Now, we can deploy the network, as well as check our ip address, which we will need later.
```bash
sudo containerlab deploy -t test-server-router.yml
ip a | grep 10.13.37.
```
Now that our network has started, we can begin by configuring our router.

```bash
# first, we connect to our router:
docker exec -it clab-test-server-router-r1 vtysh
# now, we can begin configuring:
configure terminal
interface eth1
ip address 10.0.0.1/24
end
write memory
show interface brief # confirm that the ip address is there
exit
```
Now, we can configure our test machine.
```bash
# first, we connect to the test machine:
docker exec -it clab-test-server-router-test sh
# now, we can begin configuring:
# update the packages:
apk update
# install the iproute2 package:
apk add iproute2
# configure the ip address:
ip addr add 10.0.0.50/24 dev eth1
ip link set eth1 up

ip route add default via 10.0.0.1
```
Now, we can connect to the remote testing server to get our flag.
```bash
ssh networking001@10.13.37.10
password: networking001
ls
./reverse-ctf.sh 10.13.37.55
```
This should return the flag.

## "Two networks; one router"

# secret

## secret.000

## secret.001

## secret.002

## secret.003

## secret.004

## secret.005

# Challenge.000

## challenge.000.000

SSH into the server
```bash
ssh challenge.000.000@10.13.37.10
password: challenge.000.000
```
Locate the flag
```bash
ls
cd inhere
ls
ls -la
cat .secret
```
This Returns the flag.

## challenge.000.001

SSH into the server
```bash
ssh challenge.000.001@10.13.37.10
password: challenge.000.001
```
Find the hint:
```bash
ls
cat secret.hint
```
Hint states the flag is > 50 bytes and < 60 bytes.
Find the file.
```bash
find / -size +50c -size -60c -name *flag 2> /dev/null
cat /lusr/local/share/obsolete_libs/W344gweSDl.flag
```
This returns the flag.

## challenge.000.002

SSH into the server
```bash
ssh challenge.000.002@10.13.37.10
password: challenge.000.002
```
Read the hint
```bash
ls
cat secret.hint
```
"Your flag is next to the word hunched"
```bash
cat secret.flag | grep -w hunched
```
This returns the flag next to the word "hunched"

## challenge.000.003

## challenge.000.004

## challenge.000.005