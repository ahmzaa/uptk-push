# UPTK-Push

## What

UPTK-Push or uptime kuma push is a shell script that simply curls the URL given to you by Uptime kuma when you select the push monitor type.

I use the push monitor type as a way to let uptime kuma know that my hosts in AWS are alive.

The Push method of monitoring means Uptime kuma is passive and awaits a response from the target instead of actively checking.

## Why

Crontab ...
Uptime kuma requires the host to request the URL on the heartbeat interval and Crontab allows us to do that. However we need to provide a clean script that we can call using crontab.

## How

This is a very basic script. It simply checks to see if you have provided a URL as an argument if not it will tell you so and if you have it will curl the URL.

## Notes

### Curl hanging even after successful push

I found that when copying the Push URL you get something simmilar to what you see below.

```
https://example.ahmza.com/api/push/<monitor-id>?status=up&msg=OK&ping=
```

to fix this I simply removed `&ping=` from the end so it looks like the following.

```
https://example.ahmza.com/api/push/<monitor-id>?status=up&msg=OK