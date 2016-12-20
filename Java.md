# Heap, thread dumps
* Heap dump
```bash
jmap -dump:format=b,file=cheap.bin <pid>
```
* Thread dump
```bash
jstack <pid> > thread-dump.txt
```
# Remote tomcat debugging
* **./catalina.sh jpda run** - this command will run the catalina with jpda turned on port 8000
* Default port can be changed with this export: **export JPDA_ADDRESS=8001**
* After this You can connect with Your IDE to debug remotely
