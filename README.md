# jot
Quick markdown-formatted notes from the command line, stored in AWS S3 buckets.

## Currently developing
- User authentication and configuration, so people other than me can use `jot` without setting up their own AWS S3 bucket and rewriting a few hardcoded lines.
- More elegant backup than the `backup_jots` script you have to run manually or manually configure in your own cronjob or systemd timer or whatever it is the kids are using these days to manage their periodic processes.
- Add more configuration options to `flatcircle` so it's easier to review past entries with more intent.
- Add a search mechanism that combines the utility of `grep` and `flatcircle`.
