### Find and kill ports

To see a list of all ports on a specific port number.
```shell
lsof -i :3001
```

To kill all ports on a specific port number.

```shell
kill -9 `lsof -i TCP:3000 | awk '/LISTEN/{print $2}'`
```