# Supervisor... it keeps your app running!

supervisor is a nice thing. It keeps your app running.

    sudo apt-get install supervisor    

Config goes in...
    
    /etc/supervisor/conf.d/ directory    

You might for example add a file helloworld.conf in the required place with content such as

    $ cat helloworld.conf
    [program:helloworld]
    command=/usr/bin/dotnet /home/leon/publish/MvcMovie.dll
    #var/aspnetcore/HelloMVC/HelloMVC.dll
    #directory=/var/aspnetcore/HelloMVC/
    directory=/home/leon/publish/
    autostart=true
    autorestart=true
    stderr_logfile=/var/log/helloworld.err.log
    stdout_logfile=/var/log/helloworld.out.log
    environment=ASPNETCORE_ENVIRONMENT=Production
    user=www-data
    stopsignal=INT


Here's how to view the last 20 lines of the supervisor log, using `tail`

    $ sudo tail -n 20 -f /var/log/supervisor/supervisord.log 
    