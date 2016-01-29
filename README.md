# Heroku buildpack: Laravel

![php](http://blog.legacyteam.info/wp-content/uploads/2014/10/laravel-logo-white.png)


The official [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for PHP applications + support for running Laravel artisan commands during the deploy.

## Usage

You'll need to use at least an empty `composer.json` in your application.

    echo '{}' > composer.json
    git add composer.json
    git commit -m "add composer.json for PHP app detection"

If you also have files from other frameworks or languages that could trigger another buildpack to detect your application as one of its own, e.g. a `package.json` which might cause your code to be detected as a Node.js application even if it is a PHP application, then you need to manually set your application to use this buildpack:

    heroku buildpacks:set https://github.com/lifekent/heroku-buildpack-laravel.git

Please refer to [Dev Center](https://devcenter.heroku.com/categories/php) for further usage instructions.

To run post deploy commands set config variable 
"DEPLOY_ARTISAN_TASKS" with the command name, f.e:
KEY: DEPLOY_ARTISAN_TASKS 
VALUE: migrate --force
 
Use "--force" parameter if you running production environment, so then laravel won't ask you if you are really 
want to run migrations.

Running multiple artisan commands, f.e:
KEY: DEPLOY_ARTISAN_TASKS
VALUE: "migrate && php artisan route:cache"