WP-BLANK
=========

This is a template for installing and running [WordPress](http://wordpress.org/) on managed hosting.

It is a much simplified version of [heroku-wp](https://github.com/xyu/heroku-wp), using [Composer](https://getcomposer.org) to manage Wordpress base install and plugin dependencies.

It is designed to be used with "post-receive hook"- based deployment.

WordPress and most included plugins are installed by Composer on build. To add new plugins or upgrade versions of plugins simply update the `composer.json` file and then generate the `composer.lock` file with the following command locally:

```bash
$ composer update --ignore-platform-reqs
```

To customize the site simply place files into `/public.custom` which upon deploy to Heroku will be copied on top of the standard WordPress install and plugins specified by Composer.

Usage
------------

Clone the repository from Github

    $ git clone git://github.com/ericgj/wp-blank.git

Create a new production branch for your app

    $ git checkout -b production

On the target server, create a bare repo and set up the post-receive hook.
(For an example, see [wp-deploy-scripts](https://github.com/ericgj/wp-deploy-scripts) ).

Locally, set the remote repo

    $ git remote add deploy ssh://user@target/path/to/repo.git

Deploy
 
    $ git push deploy production


