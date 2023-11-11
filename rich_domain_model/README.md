# Rich Domain Model

It's difficult to built rich domain model with rails/ruby application using ActiveRecord, sequel, rom-rb, hanami, etc. It could be great to have some repo solution able to save/load PORO-objects and track changes to save only dirty data.

```ruby
class Article
  def initialize(title:, body:)
    @title = title
    @body = body
  end
end

article = repo.find(id)
article.title = "New Title"

repo.save article # updates title only
```
