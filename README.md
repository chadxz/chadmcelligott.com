[chadmcelligott.com][]
----------------------

This is my personal website that I am currently hosting using Amazon S3.  I don't have much time to work on it, but I would like to slowly add content to it and progressively enhance the look and feel as needed.
I need to move from deploying via s3_website to using the grunt task [grunt-aws-s3][].

###Setup

```shell
gem install jekyll
gem install s3_website
```

###Build

```shell
jekyll build
```
If you want to work on the site and have it auto-refresh as you make changes:

```shell
jekyll serve --watch
```

###Deploy

The deployment requires two environment variables to be set to your amazon settings in order to properly deploy: `AWSAccessKeyId` and `AWSSecretKey`.  Once those are set:

```shell
s3_website push
```

[chadmcelligott.com]: http://chadmcelligott.com
[grunt-aws-s3]: https://github.com/MathieuLoutre/grunt-aws-s3