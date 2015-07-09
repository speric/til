* You can't "just" run migrations on a db that's being shared by a Rails app, if that db has been created via Rails migrations (and all that come with those)
* You *can* read from a Rails DB, simply specify the schema inside the Model:

```elixir
defmodule MyApp.User do
  use Ecto.Model
  
  schema "users" do
    field :name
  end
end
```
