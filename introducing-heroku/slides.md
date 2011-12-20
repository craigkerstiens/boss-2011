<!SLIDE forget-servers commandline incremental>

# Forget servers

    $ git push heroku master
    Counting objects: 9, done.
    Delta compression using up to 2 threads.
    Compressing objects: 100% (5/5), done.
    Writing objects: 100% (5/5), 416 bytes, done.
    Total 5 (delta 4), reused 0 (delta 0)

    -----> Heroku receiving push
    -----> Ruby/Rails app detected
    -----> Installing dependencies using Bundler
    ...
    -----> Launching... done, v5
           http://some-app-1234.herokuapp.com deployed



<!SLIDE commandline incremental run-anything>

# Run anything

    $ cd /my-ruby-app
    $ git push heroku master

<!SLIDE commandline transition=fade run-anything>

# Run anything

    $ cd /my-python-app
    $ git push heroku master

<!SLIDE commandline transition=fade run-anything>

# Run anything

    $ cd /my-node-js-app
    $ git push heroku master

<!SLIDE commandline incremental see-everything>

# See everything

    $ heroku ps
    Process      State        Command
    -----------  -----------  -----------------------------
    web.1        up for 6s    bundle exec rails server
    worker.1     up for 5s    bundle exec rake resque:work

<!SLIDE commandline incremental see-everything>

# See everything

    $ heroku logs --tail
    2011-05-31 04:04:48 heroku[router]   GET / dyno=web.1
    2011-05-31 04:04:48 app[web.1]       66.75.123.123 - -

<!SLIDE bullets incremental whats-in-store>

# Trust & Manage

* Erosion Resistance
* Control Surfaces

<!SLIDE control-surface commandline incremental release>

# Control Surfaces

## Deployment & Release Management

    $ heroku releases
    Rel   Change                          By                    When
    ----  ----------------------          ----------            ----------
    v61   Add-on add redistogo:nano       craig@heroku.com      7 hours ago
    v60   Deploy 8ef908f                  craig@heroku.com      Mon Nov 07 12:36:16 +0000 2011
    v59   Deploy 5f52d96                  craig@heroku.com      Mon Nov 07 12:35:12 +0000 2011
    v58   Deploy 51cfb25                  craig@heroku.com      Mon Nov 07 12:28:41 +0000 2011

<!SLIDE control-surface commandline incremental>

# Control Surfaces

## Deployment & Release Management

    $ heroku rollback v61
    Rolled back to v61

<!SLIDE control-surface commandline incremental>

# Control Surfaces

## Add-ons and Config Vars

    $ heroku addons:add redistogo
    -----> Adding redistogo to your-app... done, v61 (free)

    $ heroku config:add AWS_SECRET=ADLKHGDKJS
    Adding config vars:
      AWS_SECRET => ADLKHGDKJS
    Restarting app... done, v63.


<!SLIDE control-surface commandline incremental>

# Control Surfaces

## Collaboration

    $ heroku sharing:add other-craig@heroku.com
    other-craig@heroku.com added as a collaborator on my-app.

<!SLIDE control-surface commandline incremental>

# Control Surfaces

## Scaling & Process Management

    $ heroku ps:scale web+20
    Scaling web processes... done, now running 22

    $ heroku ps:scale web-20
    Scaling web processes... done, now running 2

<!SLIDE control-surface commandline incremental>

# Control Surfaces

## Scaling & Process Management

    $ heroku ps:stop worker.2
    Stopping worker.2 process... done

<!SLIDE control-surface commandline incremental wide-logs>

# Control Surfaces

## Routing

    $ heroku logs --ps router --tail
    2011-11-09T10:24:15+00:00 heroku[router]: GET app.com/assets/screen-f840c7c750dc454279aa12307b9d3da4.css dyno=web.2 queue=0 wait=0ms service=9ms status=200 bytes=149989
    2011-11-09T10:24:17+00:00 heroku[router]: GET app.com/assets/noise-1261feea313cad67ba2d588381cf934b.png dyno=web.1 queue=0 wait=11ms service=21ms status=200 bytes=22346
    2011-11-09T10:24:23+00:00 heroku[router]: GET app.com/ dyno=web.2 queue=0 wait=0ms service=70ms status=200 bytes=4334
    2011-11-09T10:24:24+00:00 heroku[router]: GET app.com/ dyno=web.1 queue=0 wait=0ms service=33ms status=200 bytes=4334
    2011-11-09T10:24:33+00:00 heroku[router]: GET app.com/ dyno=web.2 queue=0 wait=0ms service=32ms status=200 bytes=4334
    2011-11-09T10:24:34+00:00 heroku[router]: GET app.com/robots.txt dyno=web.1 queue=0 wait=0ms service=4ms status=200 bytes=204
    2011-11-09T10:24:34+00:00 heroku[router]: GET app.com/login dyno=web.2 queue=0 wait=0ms service=33ms status=200 bytes=3119

<!SLIDE control-surface commandline incremental logging wide-logs>

# Control Surfaces

## Logging & Visibility

### (yes I've shown you this 3 times already)

    $ heroku logs
    2011-11-09T10:32:07+00:00 app[execer.6]: *** got: (Job{exec} | Cron::Jobs::Exec | [3841])
    2011-11-09T10:32:07+00:00 app[postgres]: [2-1] 2011-11-09 10:32:07 UTC dh3b3x3gyixs2lg LOG:  could not receive data from client: Connection reset by peer
    2011-11-09T10:24:34+00:00 heroku[router]: GET app.com/robots.txt dyno=web.1 queue=0 wait=0ms service=4ms status=200 bytes=204
    2011-11-09T10:24:34+00:00 heroku[nginx]: 66.249.71.147 - - [09/Nov/2011:02:24:34 -0800] "GET /robots.txt HTTP/1.1" 200 204 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)" habitual.ly
    2011-11-09T10:24:34+00:00 app[web.2]: Started GET "/login" for 66.249.71.161 at 2011-11-09 10:24:34 +0000
    2011-11-09T10:24:34+00:00 app[web.2]: cache: [GET /login] miss


<!SLIDE one-last-demo>

# More Demos
