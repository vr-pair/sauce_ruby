sauce
=====

Ruby access to SauceLab's features

Features
--------
Current:

*   Treat tunnels like ruby objects. Find/create/destroy

Planned:

*   ActiveRecord-like interface for video recordings, jobs logs, reverse tunnels
*   Start/stop local instances of Sauce RC

Install
-------
Make sure you're pulling in gems from gemcutter, and then:

`gem install sauce`

Example
-------
Here's how to start a tunnel using the Sauce gem
    require 'rubygems'
    require 'sauce'
    
    account = YAML.load_file "live_account.yml"
    client = Sauce::Client.new(:username => account["username"],
                               :access_key => account["access_key"])
    tunnel = client.create_tunnel('DomainNames' => ["123.456.789.123"])
    tunnel.refresh!
    
    client.tunnels # => [#<Sauce::Tunnel:0x1250e6c
                             @host=nil,
                             @status="running",
                             @id="389a1c2a3d49861474c512e9a904be9e",
                             @client=#<RestClient::Resource:0x1257fb4
                               @block=nil,
                               @url="https://username:access_key@saucelabs.com/rest/username/",
                               @options={}>,
                             @owner="username">]

    tunnel.destroy # or client.destroy_all_tunnels

Note on Patches/Pull Requests
----------------------------- 
*   Fork the project.
*   Make your feature addition or bug fix.
*   Add tests for it. This is important so I don't break it in a future version unintentionally.
*   Commit, do not mess with rakefile, version, or history. (if you want to have your own version, that is fine but bump version in a commit by itself I can ignore when I pull)
*   Send me a pull request. Bonus points for topic branches.

Copyright
---------
Copyright (c) 2010 Sauce Labs Inc. See LICENSE for details.