# webpack-rails-buildpack

A buildpack to support Heroku deployments for applications using [webpack-rails](https://github.com/mipearson/webpack-rails).

Name on [Heroku's buildpack registry](https://devcenter.heroku.com/articles/buildpack-registry): __febeling/webpack-rails__

_Note: Now that Rails (>= 5.1) has the webpacker gem there are few reasons to use this buildpack. 
The default Heroku Ruby buildpack can handle webpacker, too._

## Installation

#### Heroku Dashboard

Add a custom buildpack to your to your application's Settings tab
under section Buildpacks by using the URL of this repository, instead
of the short name of Heroku's own buildpacks. It goes alongside your
Ruby and Node buildpacks, placed in last position.

After the release of registered buildpacks, it will be available under
the name `febeling/webpack-rails`, adhearing to the suggested naming
conventions there.

#### Heroku CLI

First, check your Heroku app has the Ruby and Node buildpacks added,
in the command line run:

    heroku buildpacks

If they are added you should see:

    your-app-1234 Buildpack
    1. heroku/nodejs
    2. heroku/ruby

To add the Webpack Rails buildpack in the last index, run this command:

    heroku buildpacks:add --index 3 febeling/webpack-rails

## Usage

On deployment, the buildpack runs the build command `bundle exec rake
webpack:compile`. Under default configuration that will output the
compiled assets under `public/webpack`.

### Package Manager

Heroku supports both NPM and Yarn as Javascript package managers. This
buildpack will detect which one to use automatically, based on the
persence of a version-lock file.  Projects that use yarn have a
`yarn.lock` file, while those that use npm have a `package-lock.json`
(or none if using an older version of `npm`).

This buildpack will set the `YARN` environment variable accordingly, which
will make that the effective package manager for Javascript.

## Using the latest buildpack code

The `febeling/webpack-rails` buildpack from the [Heroku
Registry](https://devcenter.heroku.com/articles/buildpack-registry)
contains the latest stable version of the buildpack. If you'd like to
use the latest buildpack code from this Github repository, you can set
your buildpack to the Github URL:

    heroku buildpacks:add --index 3 https://github.com/febeling/webpack-rails-buildpack

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

Started on 5 June 2016.

## Credits

Created by Florian Ebeling.

## License

See LICENSE.md file.
