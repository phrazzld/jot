# jot
Quick markdown-formatted notes from the command line, stored in AWS S3 buckets.

## Config file
jot depends on a config file that should look something like this:
```
JOT_USERNAME=yourname
JOT_BUCKET=jots-for-$JOT_USERNAME
JOT_LOCAL_DIR=/path/to/jots
JOT_S3_URL="s3://$JOT_BUCKET"
AWS_ACCESS_KEY_ID=yourawsaccesskeyid
AWS_SECRET_ACCESS_KEY=yoursecretkey
AWS_DEFAULT_REGION=yourdefaultregion
AWS_PATH=~/.aws
```

This lets jot know where to save everything, locally and on S3, and how to set up your AWS configuration and credentials.

## Currently developing
- Sync jots between S3 and your local machine based on each file's last modified date instead of the absurd and barbaric approach `aws s3 sync` takes by default, where it just totally overwrites target with source if they're different at all with no consideration for which one should actually overwrite the other.
- User authentication and configuration, so people other than me can use `jot` without setting up their own AWS S3 bucket and rewriting a few hardcoded lines.
- More elegant backup than the `backup_jots` script you have to run manually or manually configure in your own cronjob or systemd timer or whatever it is the kids are using these days to manage their periodic processes.
- Add more configuration options to `flatcircle` so it's easier to review past entries with more intent.
- Add a search mechanism that combines the utility of `grep` and `flatcircle`.
