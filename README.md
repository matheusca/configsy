# Configsy

Configsy (config(uration) (ea)sy) help avoid duplicate method to load
config files.

## Installation

Add in your Gemfile

```ruby
gem 'configsy'
```

And then execute:

    $ bundle

## Usage

Put your file into ```config/``` directory and than include module how
described below.

```lang
#My config file
test: 'test'
```

```ruby
class MyOwnClass
  include Configsy
  configsy :my_config_file

  def test
    my_config_file.test
  end
end
```

Maybe the method create by default it's being use, so you might change the
method name.

```ruby
class MyOwnClass
  include Configsy
  configsy :my_config_file, name: :config

  def test
    config.test
  end
end
```

By default Configsy has implemented YAML config extension, but you
could implement your own config adapter.

```ruby
class IniAdapter < Configsy::Adapter
  extension :ini

  def load
    # Your strategy to read config values.
  end
end
```

## Contributing

1. Fork it ( https://github.com/matheusca/configsy/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
