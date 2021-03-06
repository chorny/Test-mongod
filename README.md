# NAME

Test::mongod - run a temporrary instance of MongoDB

# SYNOPSIS

     use Test::mongod;
     my $mongod = Test::mongod->new;  # thats it, you get a mongod server on a random port and in a /tmp dir

     ... more

     $mongod->port; # get the port the server is listening on
     $mongod->dbpath; # get the db dir
    
     

# DESCRIPTION

Test::mongod automatically sets up a temporary instance of MongoDB and destroys it when the script ends.

The latest version of this is always at
[https://github.com/jshy/Test-mongod](https://github.com/jshy/Test-mongod)
This is `ALPHA` code.

# METHODS

## `new`

    my $mongod = Test::mongod->new;

This creates a new instance of `Test::mongod` and instanciates a temporary MongoDB server
This uses the moose BUILD method to go ahead and launche the server. This method blocks till the server is listening and ready to work.

## `stop`

    $mongo->stop;

Stops the MongoDB instance and tears down the temporary directory. This method is called by DEMOLISH when the object goes out of scope.

# ATTRIBUTES

## bind\_ip

The IP to bind the server on. Defaults to 127.0.0.1. Must be an IP on the localhost.

## port

The port for the server to listen on. Defaults to a random port. Use this to get the port to feed to your client. 

## dbpath

The diorectory for the database server to put ts files. This defaults to a /tmp directory that will be cleaned up when the script finishes. Changes this will cause the directory to persist. Must be a path on the localhost.

## pid

Contains the pid of the forked child process.

## config

a hashref of config options 
you can give ether 

    config => { } or 
    config_file => 'relative/path/to/conf/file'

config file must be something Config::Any recognizes. SEE EXAMPLE t/etc/mongo.conf
if you have a t/etc/mongod.conf file then it will get picked up automatically
NOTE: If you use config no config file gets read.

# AUTHOR

Jesse Shy <jshy@cpan.org>

# COPYRIGHT

Copyright 2014- Jesse Shy

# LICENSE

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# SEE ALSO
