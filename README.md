# Arc Azure Storage Provider

**Arc Azure Provides an [`Arc`](https://github.com/stavro/arc) storage back-end for [`Azure Storage`](https://azure.microsoft.com/en-us/services/storage/).**

## Installation

The package can be installed
by adding `arc_azure` to your list of dependencies in `mix.exs` (along with other dependencies you need):

```elixir
def deps do
  [
    {:arc_azure, "~> 0.1.1"},
    {:arc, "~> 0.8.0"},
    {:erlazure, github: "dkataskin/erlazure"},
  ]
end
```

Run `mix deps.get` in your shell to fetch the dependencies.

## Configuration

arc_azure uses the [`ex_azure`](https://github.com/azukiapp/ex_azure) default environment variables so make sure you have set these:

```sh
export AZURE_ACCOUNT=<your-azure-account>
export AZURE_ACCESS_KEY=<your-azure-access-key>
```

Configure arc_azure with your container and cdn_url:

```elixir
config :arc_azure,
  container: "uploads",
  cdn_url: "https://#{System.get_env("AZURE_ACCOUNT")}.blob.core.windows.net"
  timeout_in_milliseconds: 30_000
```

Configure the Arc Storage Adapter:

```elixir
config :arc,
  storage: Arc.Storage.Azure
```

## License

Copyright 2017 Philip Alekseev

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
