[chadmcelligott.com][]
----------------------

This is my personal website that I am currently hosting using Amazon S3.  I don't have much time to work on it, but I would like to slowly add content to it and progressively enhance the look and feel as needed.
I need to move from deploying via s3_website to using the grunt task [grunt-aws-s3][].

###Setup

This site uses Jekyll to build the static assets, and s3_website to publish to Amazon S3. Both of these tools require the Ruby programming language runtime to be installed, so if you need to install that:
- for windows, use [RubyInstaller][]
- for mac/linux, use [RVM][] by executing this at the command line: `\curl -L https://get.rvm.io | bash -s stable --ruby`

Once ruby is installed, install s3_website and jekyll by running:
```shell
bundle install
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

The deployment requires two environment variables to be set to your amazon settings in order to properly deploy:
- `PERSONAL_AWS_ACCESS_KEY_ID`
- `PERSONAL_AWS_SECRET_ACCESS_KEY`

Once those are set:
```shell
s3_website push
```

[chadmcelligott.com]: http://chadmcelligott.com
[grunt-aws-s3]: https://github.com/MathieuLoutre/grunt-aws-s3
[RubyInstaller]: http://rubyinstaller.org/
[RVM]: https://rvm.io/
