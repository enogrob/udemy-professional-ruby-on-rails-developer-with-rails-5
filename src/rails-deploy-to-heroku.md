### [gist-rails-deploy-to-heroku](https://gist.github.com/15ac88dde34682d4eb1e5bda3f18b346)

**rails-deploy-to-heroku**

This describes a procedure in order to deploy a `Rails` app to [Heroku](http://www.heroku.com/).

1. Then pull up your `Gemfile`, move the `sqlite3` gem to group `development` and add the `pg` to group `production`:
```shell
6,7d5
< # Use sqlite3 as the database for Active Record
< gem 'sqlite3'
35a34,35
>   # Use sqlite3 as the database for Active Record
>   gem 'sqlite3'
48a49,52
>
> group :production do
>   gem 'pg'
> end
```

2. Then run:
```shell
bundle install --without production

```

3. Then do another `commit` to capture the updates:
```shell
git add .
git commit -am "performed-app-production-ready"
git push

```

4. Then log-in to your `heroku` account, and enter in your email and password:
```shell
heroku login

```

5. Add your public `ssh key` to your `Heroku` account and enter `Y` when asked whether to upload public `ssh key` to `Heroku`.
```shell
heroku keys:add

```

6. Create a new production app in `Heroku`:
```shell
heroku create

```

7. Rename it to something you like:
```shell
heroku rename <appname>

```

8. Deploy your local app to heroku:
```shell
git push heroku master

```

9. Then run the migrations in heroku:
```shell
heroku run rails db:migrate

```

10. Now check out your app in `Heroku` at [appname](appname.herokuapp.com). Or in [Heroku Dashboard](https://dashboard.heroku.com/apps).
