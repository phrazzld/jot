# jot
Quick markdown-formatted notes from the command line, stored in AWS S3 buckets.

## Setup
To start using **jot**, you need to:
1. Clone this repository to your local machine.
2. Add the path of the cloned **jot** repository to your local machine's PATH.
3. Set up an Amazon Web Services account.
4. Install the Amazon Web Services command line interface [here](https://docs.aws.amazon.com/cli/latest/userguide/installing.html).
5. Replace the values in the project `config` file with the directory you want your jots saved to, the URL of the AWS S3 bucket you want them backed up to, and the editor you want to write with (I strongly recommend Vim with the [Goyo](https://github.com/junegunn/goyo.vim) plugin). If you don't want to use Goyo, just set the value of GOYO in the config file to an empty string.
6. Add `alias jot=/path/to/cloned/jot-repo/jot` to your `.profile`.

And now you're ready to start using **jot**!

## Usage
Enter `jot` into your command line. This will create the path you defined in your config file if it doesn't exist. Then it will open the markdown file for the day (named in the format YYYYMMDD.md) in your selected editor, creating it if it doesn't exist.

To back up your local jots, run `backup_jots`. If the bucket you've defined in your config file doesn't exist, `backup_jots` will create it for you (so long as it's a valid AWS S3 bucket URL).

To pull saved jots from your S3 bucket, run `pull_remote_changes`.

Be careful with these two! Running `pull_remote_changes` will overwrite changes you have on your local machine that you haven't pushed yet.

Running the `flatcircle` command will open old jots in new terminal windows for you to review. By default it will open jots from yesterday, a week ago, a month ago, three months ago, six months ago, and every jot you wrote on this day any number of years ago.

## Currently developing
- Sync jots between S3 and your local machine based on each file's last modified date instead of the absurd and barbaric approach `aws s3 sync` takes by default, where it just totally overwrites target with source if they're different at all with no consideration for which one should actually overwrite the other.
- User authentication and configuration, so people other than me can use **jot** without setting up their own AWS S3 bucket and rewriting a few hardcoded lines.
- More elegant backup than the `backup_jots` script you have to run manually or manually configure in your own cronjob or systemd timer or whatever it is the kids are using these days to manage their periodic processes.
- Add more configuration options to `flatcircle` so it's easier to review past entries with more intent.
- Add a search mechanism that combines the utility of `grep` and `flatcircle`.

## LICENSE
[MIT](https://opensource.org/licenses/MIT)
