# Heroku aria2c

This is a fork of https://github.com/maple3142/heroku-aria2c/

Things edited here are:
1. Fixed deploy button (I saw it here: https://github.com/maple3142/heroku-aria2c/commit/d6670a2a4eab67ea1d2a344c402c5faf51616ff8) 
2. Changed the login page into a better one (see this: https://jsfiddle.net/x1u6aspb/)
3. Fixed bugs (The changes were based on: https://github.com/MrRobotGOD/heroku-aria2c)
4. Beautified AriaNg/index.php (formerly just one line, using https://www.jpkc.com/tools/beautify/)

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/sagirisayang/heroku-aria2c/tree/master)

> Do not overuse it, or your account might be banned by Heroku.

## Optionally sync downloaded file to your cloud drive with Rclone

1. Setup Rclone locally by following offical instructions: https://rclone.org/docs/
2. Find your `rclone.conf` file, it should look like this:

```conf
[DRIVENAME]
type = WHATEVER
client_id = WHATEVER
client_secret = WHATEVER
scope = WHATEVER
token = WHATEVER

others entries...
```

3. Find the drive you want to use, and copy its `type = ...` to  `... token = ...` section.
4. Replace all linebreaks with `\n`
5. Deploy with the button above, and paste that text in `RCLONE_CONFIG`
6. Set `RCLONE_DESTINATION` to a path you want to store your downloaded files.

## FAQ

### It automatically stop after 30 minutes, and files were lost.

It is because Heroku's free dyno will idle when there is no incoming request within 30 minutes, and your files will be deleted too, this is why you might want to use Rclone.

### Can I delete files?

No. Just wait for its idling, and your files will be deleted.

### You said it will idle automatically, so I can't download large files?

It will generate fake requests when there are downloading or uploading tasks, so it won't idle when your files aren't completed.

### I don't know how to setup Rclone, can you help me?

No. I thought the instructions above are enough.
