# Virtual FS

It is possible to present any data as tree of directories and files. Then it could be accesed via diffrerent adapters like: WebDAV, ftp, ssh, etc


## Define storage

```ruby
class Dir
  def each
    ["foo.txt", "bar.txt", "somedir"].each do |name|
      yield name
    end
  end

  def file?(name)
    ["foo.txt", "bar.txt"].include?(name)
  end

  def read(file_name)
    # IO object
  end
end
```

## Expose

Run as rack up

```ruby
# config.ru
require "virtual_fs"
require_relative "./storage"

run VirtualFS::WebDAV.new(
  "/webdav",
  VirtualFS::FileSystem.new(Storage.new)
).rack
```

