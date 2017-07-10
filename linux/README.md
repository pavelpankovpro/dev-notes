# Bash Tips

Run a command or shell script in backgraound and even if you logout

```bash
nohup command-with-options &
```

# Scripts

-e - exits if any of the lines fail
-x - print evert command that is going to be executed with a + sign

```bash
set -ex
```

Delete files in a directory older than 7 days
``` bash
find /path/to/files/* -mtime +7 -exec rm {} \;
```
