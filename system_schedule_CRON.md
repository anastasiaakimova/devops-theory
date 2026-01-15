# How to setup system schedule (cron)

`crontab -e`
`crontab -l` - list of crons

`minute` `hour` `day_of_month` `month` `day_of_week` `command_to_execute`

| Field | Allowed Values | Description | Example |
|-------|----------------|-------------|---------|
| Minute | 0-59  | The minute of the hour the command will run | `0` — start at the beginning of the hour |
| Hour | 0-23 | The hour of the day the command will run | `14` — run at 14:00 |
| Day of Month | 1-31 |  The day of the month the command will run | `15` — run on the 15th of the month |
| Month | 1-12 или JAN-DEC | The month of the year the command will run | `JAN` or `1` — run in January |
| Day of Week | 0-7 или SUN-SAT | The day of the week the command will run (0 or 7 is Sunday) | `0` or `SUN` — run on Sunday |
| Command to Execute |  | The full path to the script or command you want to run | `/home/user/script.sh` |

## Special Characters:

| Symbol | Meaning | Example |
|--------|---------|---------|
| `*` | Represents "every" | `*` in the minute field means every minute |
| `,` | Separates multiple values | `1,15` in day of month means 1st and 15th |
| `-` | Specifies a range | `9-17` in hour means 9 AM to 5 PM |
| `/` | Specifies step values | `*/10` in minute means every 10 minutes |
