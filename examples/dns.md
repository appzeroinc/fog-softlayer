### DNS Examples

These examples all assume you have `~/.fog` which contains the following


   ```yaml  
   :softlayer_username: example-username
   :softlayer_api_key: 1a1a1a1a1a1a1a1a1a11a1a1a1a1a1a1a1a1a1
  ```

#### Create a connection to SoftLayer DNS Service

```ruby
	require 'fog/softlayer'
	@sl = Fog::DNS[:softlayer]
```

1. Create Operations

* Create Domain

  ```ruby
  @domain = @sl.domains.create('yourdomain.com')
  ```

* Create Record

  ```ruby
  record = {
    'data' => '127.0.0.1',
    'host' => '@',
    'type' => 'a'
  }
  @domain.create_record(record)
  ```

1. Read Operations

* List all domains

  ```ruby
  @domains = @sl.domains.all
  @domain = @domains.first
  ```

* Get specific domain by id

  ```ruby
  @domain = @sl.domains.get(123456)
  ```

* Get specific domain by name

  ```ruby
  @domain = @sl.domains.get_by_name('yourdomain.com')
  ```

* Get Domains Records

  ```ruby
  @domain = @sl.domains.get(123456)
  @domain.records
  ```

1. Update Operations

After this point we consider you have a Fog::DNS::Softlayer::Domain on @domain variable

* Update Record Entry

  ```ruby
  @domain.records
  @domain.records[3].value = "192.168.0.3"
  @domain.records[3].save
  ```

1. Destroy Operations

After this point we consider you have a Fog::DNS::Softlayer::Domain on @domain variable

* Destroy Domain

  ```ruby
  @domain = @sl.domains.get(123456)
  @domain.destroy
  ```

* Destroy Record

  ```ruby
  @domain = @sl.domains.get(123456)
  @domain.records.last.destroy
  ```