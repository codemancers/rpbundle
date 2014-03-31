# rpbundle

`rpbundle` is an extension to ruby-processing which allows you
to use rubygems in your ruby-processing sketches and manage gem dependencies
of your sketches using bundler.

## Why do I need this ?

First, some background.

There are 2 ways of running ruby-processing sketches :

1. Using system wide jruby installation
2. Using jruby-complete.jar which is nothing but jruby in a jar

### Why do we need 2 jrubies ?

Sadly, some sketches (like those which use `load_image`) require you to use
jruby-complete.jar by specifying `--nojruby` CLI argument to rp5. So that means
having a system wide jruby installation is not enough.

### So why can't I always use --nojruby flag ?

Using system jruby allows you to use gems and make use of bundler in the usual
way, whereas using --nojruby doesn't allow you to do the same because jruby-complete
is like ruby in a box, and it doesn't know where your system gems are by default.

### TL;DR

If there was a way to use rubygems with `--nojruby` flag, that would be the
ideal way to run sketches. `rpbundle` allows you to do that, and
that's why you need this.

## Installation

    $ gem install rpbundle

This gem has ruby-processing as a dependency so this installs `ruby-processing`
as well.

## Usage

This gem comes with an executable `rpbundle`.

Prerequisite step for setting up :
   
    $ rpbundle setup
    
The above command creates a directory at `~/.rpbundle` and installs `bundler`
gem into it.

Inside a sketch/project directory with a Gemfile, to install dependent gems :
    
    $ rpbundle install

To run/watch/<other subcommands supported by rp5> your sketch using
rp5 command and load your gem dependencies while doing so :
    
    $ rpbundle run/watch/.. my_sketch.rb

rp5bundle is a basically a wrapper around rp5 and does 2 things :

1. Loads bundler environment in your sketches
2. Uses jruby-complete.jar (So you don't need to specify --nojruby. It's always on.)

## Contributing

1. Fork it ( http://github.com/emilsoman/rpbundle/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
