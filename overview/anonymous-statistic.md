# Anonymous Statistic

By default, our app collects anonymous data in order to optimize the user experience and understand how the app is being used. This data includes information about operating system being used. This data is not linked to any personal information and is collected anonymously. We use this data to replicate issues that may arise on specific devices and to make updates that will benefit our users. If you would prefer not to participate in this data collection process, you can opt-out in the app's settings.

## Disable Anonymous Statistic

Anonymou Statistic can be disabled by editing bqckup configuration in `/etc/bqckup/bqckup.cnf`

set `anonymous_statistic` value to 0

```
; Before
anonymous_statistic=1

; After
anonymous_statistic=0
```
