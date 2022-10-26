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
require "virtual_fs"

run VirtualFS::FileSystem.new(
  Storage.new
).expose(
  VirtualFS::WebDAV.new "/"
)
```

