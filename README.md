# shell-script-reference

Bash interpreter location:

```
which bash
```

Execute with interpreter:

```shell script
bash <filename>
sh <filename>
```

Execute file:

- Take ownership of file

```
chmod +x <filename>
```

- Add interpreter location to the top of the script

```shell script
#!/bin/bash

# Note: You may also see #!/usr/bin/env bash instead, which can be used if you don't know the exact path for bash.

#!/usr/bin/env
```

- Execute file directly

```shell script
./<filename>
```
