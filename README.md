# Habitatize

"Habitatize Yourself" (tm) in this web application.


## Build

Install Habitat and Docker https://www.habitat.sh/tutorials/download/ for your platform.

    $ Clone / Download this repository
    $ Run `hab studio enter` witin the source directory
    $ Invoke `build` from within the Habitat Studio
    $ Run `hab pkg export docker learn-chef/habitatize` to export to a runnable Docker Image
    $ Invoke `exit` to leave the Habitat Studio

## Run

    $ run `docker run -p 8000:8000 learn-chef/habitatize`

## About

This application can be run locally, outside of the Habitat package, if you:

1. Install Ruby
2. Install Imagemagick
3. `$ gem install bundler`
4. Clone / Download this repository
5. Run `bundle install` from within the source directory
6. Run `rackup` from within the source directory

When you run the application through the command `rackup`, the `rackup` command will look for and load the `config.ru` in the current working directory. This file is the Rackup (The 'ru' stands for Rackup) configuration file.

The Rackup configuration file loads the file that contains the website application and then launches this classic style Sinatra application.

The default port that Rackup will launch the application is 9292. When you visit that site you will be executing the code defined in the `lib/service.rb`. The default index page routes to the block of code defined for `get '/'`. It will render the index template found in `lib/views`. This will render a simple form that will request an image.

When you select an image and press 'Upload image', you will be routed to the block of code defined for `post 'habitatized'`. This will find the images provided by you and then pass that image to the method (defined in `lib/meme.rb`) that creates the animation. That animated image is then saved to the websites public directory (a temporary directory) and then served up by the habitatized template found in `lib/views`
