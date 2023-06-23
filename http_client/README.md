# HTTP Client

HTTP client with object oriented API. Most of all have procedural API.


```ruby

# Delacrative API
GetRequest.new(
  'http://example.com',
  params: { a: 123 },
  headers: {}
).response.body


# Immutable chaining
request = GetRequest.new('http://example.com')
  .with_params(a: 123)
  .with_headers(content_type: 'application/json')

response = request.response
response.code
response.body

```
