# longwarn
`longwarn` returns non-zero exit code if a command takes longer than pre-defined number of seconds.

For example, the following command returns non-zero exit code, because `sleep 5` takes longer than 3 seconds:
```shell
longwarn 3 sleep 5
```

## Combination with cronic
`longwarn` can be combined with `cronic` to warn a user if commands take longer that expected:
```shell
MAILTO=monitoring@example.com
11 11 * * * cronic longwarn 60 /backup.sh
```
