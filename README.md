### dashing-rails
---

https://github.com/gottfrois/dashing-rails


```
gem 'dashing-rails'
gem 'puma'
bundle
rails g dashing:install
redis-server
rails s
curl http://localhost:3000/dashing/dashboards

curl -X PUT http://localhost:3000/dashing/widgets/welcome -d "widget[text]=Dashing is awesome"
curl -X PUT http://localhost:3000/dashing/widgets/karma -d "widget[current]=100" -d "auth_token_YOUR_AUTH_EOKEN"
rails g dashing:widget my_widget
rake
```

```ruby
config.allow_concurrency = true

Dashing.scheduler.ever '1m', first_in: 1.second.since do |job|
  Dashing.send_event('karma', { current: rand(1000) })
end

Dashing.send_event(widget_id, json_formatted_data)

config.redis_host = '127.0.0.1'
config.redis_port = '61379'
config.redis_password = '123456'

dashing_events.*

redis.with do |redis_connection|
  redis_connection.publish("dashing_events.create", {})
end

config.redis_namespace = 'your_redis_namespace'
HTTPartiy.pot('http://localhost:3000/dashing/widgets/karma',
  body: { auth_token: "YOUR_AUTH_TOKEN", current: 1000 }.to_json)

```

```

```

