### Neo4j.rb
---
https://github.com/neo4jrb/neo4j

https://neo4jrb.readthedocs.io/en/9.2.x/
https://github.com/neo4jrb/neo4j/wiki
https://github.com/neo4jrb/neo4j-core/wiki

```ruby
person.friends.favorite_beers.country_of_origin(:country).
  order('count(country) DESC').
  pluck(:country, count: 'count(country)')
```

```ruby
person = Person.create(name: 'James', age: 15)
person= Person.find_by(name: 'James', age: 15)
person.houses.map(&:address)
Person.where(name: 'James').order(age: :desc).first
person.vehicles(:v).where('v.year < 2005').owners(:other).to_a

gem 'neo4j', '~> 9.0.0'
require 'neo4j/railtie'
class Application < Rails::Application
  config.generators { |g| g.orm :neo4j }
end

NEO4J_URL=http://localhost:7474
NEO4J_URL=http://user:pass@localhost:7474
NEO4J_TYPE=bolt
NEO4J_URL=bolt://user:pass@localhost:7687
NEO4J_TYPE=embedded
NEO4J_PATH=/path/to/graph.db

config.neo4j.session.type = :http
config.neo4j.session.url = 'http://localhost:7474'

config.neo4j.session.type = :blot
config.neo4j.session.url = 'bolt://localhost:7687'

config.neo4j.session.type = :embedded
config.neo4j.session.path = '/path/to/graph.db'

config.neo4j.session.url = 'http://neo4j:password@localhost:7474'

config.neo4j.session.options = {initialize: { ssl: { verify: true }}}

config.neo4j.session.options = {
  faraday_configurator: proc do |faraday|
    faraday.adapter :typhoeus
    faraday.options[:open_timeout] = 5
    faraday.optoins[:ssl] = { verify: true }
  end
}

require 'neo4j/core/cypher_session/adapters/http'
faraday_configurator = proc do |faraday|
end
require 'neo4j/core/cypher_session/adaptors/http'
http_adaptor = Neo4j::Core::CypherSession::Adapters::HTTP.new('http://neo4j:passWlocalhost:7474', faradaay_configurator: faraday_configurator)

gem 'neo4j', '~> 9.0.0'
gem 'neo4j-core', '~> 8.0.0'

require 'neo4j/rake_tasks'

Neo4j::Session.open(:http)

require 'neo4j/core/cypher_session/adaptors/embedded'
neo4j_adaptor = Neo4j::Core::CypherSession::Adapters::Embedded.new('/file/path/to/graph.db')
neo4j_session = Neo4j::Core::CypherSession.new(neo4j_adaptor)

require 'neo4j/core/cypher_session/adaptors/http'
neo4j_adaptor = Neo4j::Core::CypherSession::Adaptors::HTTP.new('http://user:pass@host:7474')
Neo4j::ActiveBase.on_establish_session { Neo4j::Core::CypherSession.new(neo4j_adaptor) }

Neo4j::ActiveBase.current_session = Neo4j::Core::CypherSession.new(neo4j_adaptor)

heroku addons:create graphenedb
heroku addons:create graphstory

```

```yml
development:
  type: http
  url: http://localhost:7474
test:
  type: http
  url: http://localhost:7575
production:
  type: http
  url: http://neo4j:password@localhost:7000

```

```
rails new myapp -m http://neo4jrb.io/neo4j/neo4j.rb -O
rails new myapp -m http://neo4jrb.io/neo4j/neo4j.rb -O
cd myapp
rake neo4j:install[community-latest]
rake neo4j:start
rails g scaffold User name:string email:string
rails g
open http://localhost:1000/users



```


