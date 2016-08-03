# webpack-rails-buildpack

A buildpack to support Heroku deployments with [webpack-rails](https://github.com/mipearson/webpack-rails).

## Installation

#### Heroku Dashboard

Add a custom buildpack to your to your applications Settings tab under
section Buildpacks by using the URL of this repository, instead of the
short name of Heroku's own buildpacks. It goes alongside your Ruby and 
Node buildpacks, placed in last position.

#### Heroku CLI

First, check your Heroku app has the Ruby and Node buildpacks added, in the command line run:

    heroku buildpacks

If they are added you should see:

    your-app-1234 Buildpack
    1. heroku/nodejs
    2. heroku/ruby

To add the Webpack Rails buildpack in the last index, run this command:

    heroku buildpacks:add --index 3 https://github.com/febeling/webpack-rails-buildpack.git

## Usage

On deployment, the buildpack runs the build command `bundle exec rake
webpack:compile`. Under default configuration that will output the
compiled assets under `public/webpack`.

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
