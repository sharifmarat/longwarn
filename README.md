# longwarn
`longwarn` returns non-zero exit code if a command takes longer than desired.

For example, the following command returns non-zero exit code, because `sleep 5` takes longer than 3 seconds:
```shell
longwarn 3 sleep 5
```

## Cron jobs

`longwarn` is useful in monitoring of cron jobs. If a job takes longer than expected, you will get notified:
```shell
MAILTO=monitoring@example.com
11 11 * * * longwarn 60 /backup.sh
```

You can also combine it with `cronic`:
```shell
MAILTO=monitoring@example.com
11 11 * * * cronic longwarn 60 /backup.sh
```

## Examples

Show usage:
```shell
longwarn 
```

Failed return codes:
```shell
longwarn 1 sleep 3
longwarn 500 script-that-returns-error
```

Success (usually):
```shell
longwarn 3 sleep 1
longwarn 500 ls /
```
