# Coinbase

This gem helps you integrate with the [Coinbase API](https://coinbase.com/docs/api/overview) to add bitcoin payments or data to your application.

This gem uses the [api key authentication method](https://coinbase.com/docs/api/overview).

If you would like to do an OAuth2 integration instead, you may want to try the [OAuth2 Ruby Gem](https://github.com/intridea/oauth2).

## Installation

Add this line to your application's Gemfile:

    gem 'coinbase'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install coinbase

## Usage

Start by [enabling the API Key on your account](http://localhost:3000/account/integrations).

Next you can create an instance of the client and pass it your API Key as the only parameter.

```ruby
COINBASE = Coinbase.new(ENV['COINBASE_API_KEY'])
```

Notice here that we did not hard code the API key into our codebase, but used an environment variable instead.  Keeping your credentials separate from your code base is a good [security practice](https://coinbase.com/docs/api/overview#security).

Now you can call methods on `COINBASE` similar to the ones described in the [api reference](https://coinbase.com/api/doc).  For example:

```ruby
puts JSON.parse(COINBASE.balance)
=> {"amount"=>"50.00000000", "currency"=>"BTC"}
```

## Security Notes

If someone gains access to your API Key they will have complete control of your Coinbase account.  This includes the abillity to send all of your bitcoins elsewhere.

For this reason, API access is disabled on all Coinbase account by default.  If you decide to enable API access it's important that you understand the risks and take precautions to store your API key securely in your application.

## Contributing

1. Fork it
2. Make some changes and commit (`git commit -am 'Add some feature'`)
4. Add a test if applicable and run the existing tests with `rake spec` to make sure they pass
6. Push to your form `git push origin master`
7. Bump the version number
8. Create new Pull Request