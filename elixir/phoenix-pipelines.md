Pipelines are really just collections of "plugs":

```elixir
pipeline :browser do
  plug :accepts, ["html"]
  plug :fetch_session
  plug :fetch_flash
  plug :protect_from_forgery
end

scope "/", Reporting do
  pipe_through :browser # will do all the :browser plugs
end
```
