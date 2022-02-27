# Flamegraphs

```shell
mix archive.install hex phx_new
mix phx.new flamegraphs --no-ecto
cd flamegraphs
```

add deps

```elixir
{:flame_on, "~> 0.2.1"},
{:surface, "~> 0.7.1"}
```

```shell
mix deps.get
mix surface.init --demo
```

add page to dashboard

```elixir
live_dashboard "/dashboard",
  metrics: FlamegraphsWeb.Telemetry,
  additional_pages: [
    flame_on: FlameOn.DashboardPage
  ]
```

run the dev server

```shell
iex.bat -S mix phx.server
```

## test it

- go to `/dashboard/flame_on` and click `Flame On!`
- load `localhost:4000`
- check flame
- :)

- go to `/dashboard/flame_on` and click `Flame On!`
- load `localhost:4000/demo`
- check iex
- :(


```shell
iex(1)> [error] GenServer :eflambe_server terminating
** (stop) {:not_mocked, :cowboy_handler}
    c:/Users/simon/code/flamegraphs/deps/meck/src/meck_proc.erl:491: :meck_proc.gen_server/3
    c:/Users/simon/code/flamegraphs/deps/meck/src/meck.erl:484: :meck.unload/1
    (eflambe 0.2.2) c:/Users/simon/code/flamegraphs/deps/eflambe/src/eflambe_server.erl:182: :eflambe_server.maybe_unload_meck/1
    (eflambe 0.2.2) c:/Users/simon/code/flamegraphs/deps/eflambe/src/eflambe_server.erl:123: :eflambe_server.handle_call/3
    (stdlib 3.17) gen_server.erl:721: :gen_server.try_handle_call/4
    (stdlib 3.17) gen_server.erl:750: :gen_server.handle_msg/6
    (stdlib 3.17) proc_lib.erl:226: :proc_lib.init_p_do_apply/3
Last message (from #PID<0.575.0>): {:stop_trace, #Reference<0.2355251988.3090677764.183233>}
State: {:state, [{:trace, #Reference<0.2355251988.3090677764.183233>, 1, 1, false, #PID<0.576.0>, [meck: :cowboy_handler, output_directory: "flame_on_output_delete_me"]}, {:trace, #Reference<0.2355251988.3090677762.192711>, 1, 1, false, #PID<0.554.0>, [meck: :cowboy_handler, output_directory: "flame_on_output_delete_me"]}]}
Client #PID<0.575.0> is alive

    (stdlib 3.17) gen.erl:214: :gen.do_call/4
    (stdlib 3.17) gen_server.erl:243: :gen_server.call/3
    (eflambe 0.2.2) c:/Users/simon/code/flamegraphs/deps/eflambe/src/eflambe.erl:125: :eflambe.stop_trace/1
    (eflambe 0.2.2) c:/Users/simon/code/flamegraphs/deps/eflambe/src/eflambe.erl:54: anonymous fn/5 in :eflambe.capture/3
    c:/Users/simon/code/flamegraphs/deps/meck/src/meck_code_gen.erl:178: :meck_code_gen.eval/5
    (cowboy 2.9.0) c:/Users/simon/code/flamegraphs/deps/cowboy/src/cowboy_stream_h.erl:306: :cowboy_stream_h.execute/3
    (cowboy 2.9.0) c:/Users/simon/code/flamegraphs/deps/cowboy/src/cowboy_stream_h.erl:295: :cowboy_stream_h.request_process/3
    (stdlib 3.17) proc_lib.erl:226: :proc_lib.init_p_do_apply/3
iex(1)> [error] Ranch protocol #PID<0.575.0> of listener FlamegraphsWeb.Endpoint.HTTP (connection #PID<0.561.0>, stream id 3) terminated
an exception was raised:
    ** (ErlangError) Erlang error: {{{:not_mocked, :cowboy_handler}, [{:meck_proc, :gen_server, 3, [file: 'c:/Users/simon/code/flamegraphs/deps/meck/src/meck_proc.erl', line: 491]}, {:meck, :unload, 1, [file: 'c:/Users/simon/code/flamegraphs/deps/meck/src/meck.erl', line: 484]}, {:eflambe_server, :maybe_unload_meck, 1, [file: 'c:/Users/simon/code/flamegraphs/deps/eflambe/src/eflambe_server.erl', line: 182]}, {:eflambe_server, :handle_call, 3, [file: 'c:/Users/simon/code/flamegraphs/deps/eflambe/src/eflambe_server.erl', line: 123]}, {:gen_server, :try_handle_call, 4, [file: 'gen_server.erl', line: 721]}, {:gen_server, :handle_msg, 6, [file: 'gen_server.erl', line: 750]}, {:proc_lib, :init_p_do_apply, 3, [file: 'proc_lib.erl', line: 226]}]}, {:gen_server, :call, [:eflambe_server, {:stop_trace, #Reference<0.2355251988.3090677764.183233>}, :infinity]}}
        (stdlib 3.17) gen_server.erl:247: :gen_server.call/3
        (eflambe 0.2.2) c:/Users/simon/code/flamegraphs/deps/eflambe/src/eflambe.erl:125: :eflambe.stop_trace/1
        (eflambe 0.2.2) c:/Users/simon/code/flamegraphs/deps/eflambe/src/eflambe.erl:54: anonymous fn/5 in :eflambe.capture/3
        (cowboy 2.9.0) c:/Users/simon/code/flamegraphs/deps/cowboy/src/cowboy_stream_h.erl:306: :cowboy_stream_h.execute/3
        (cowboy 2.9.0) c:/Users/simon/code/flamegraphs/deps/cowboy/src/cowboy_stream_h.erl:295: :cowboy_stream_h.request_process/3
        (stdlib 3.17) proc_lib.erl:226: :proc_lib.init_p_do_apply/3
        (cowboy 2.9.0) :cowboy_handler.execute(%{bindings: %{}, body_length: 0, cert: :undefined, has_body: false, headers: %{"accept" => "text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8", "accept-encoding" => "gzip, deflate", "accept-language" => "en-AU,en-GB;q=0.8,en-US;q=0.5,en;q=0.3", "connection" => "keep-alive", "cookie" => "user_data=eyJoZXhfY29sb3IiOiIjRkE4MDcyIiwibmFtZSI6bnVsbH0=; grafana_session=7dde5e08e1d826ff50815b29a27fbbce; _logacy_key=SFMyNTY.g3QAAAABbQAAAAtfY3NyZl90b2tlbm0AAAAYekp0UE9EWU9fUzNfVEtENkd0MW1ibVhw.VnbPLi1CWqtreS39MiwO61osS_q201h3Co3wxT64nR8; _livebook_key=SFMyNTY.g3QAAAAEbQAAAAo4MDgwOnRva2VubQAAACAlIl8rH-oxpWcBD8OULBvXMw1phz6RxvAqAHhzjTzgiG0AAAALX2NzcmZfdG9rZW5tAAAAGDhXbU1yM19JRmh2c2JpeDlnTThaWEZJNG0AAAAPY3VycmVudF91c2VyX2lkbQAAACA2b3N6emxzc3Zwa3VheDVsYW1kem1obGl4N2U1dWZ0eW0AAAAJdXNlcl9kYXRhdAAAAAJtAAAACWhleF9jb2xvcm0AAAAHI0ZBODA3Mm0AAAAEbmFtZWQAA25pbA.5la-XDwBoQdrTtBtuGAFbdwn2Isnt2S1pA-ePEQzfN4; _flamegraphs_key=SFMyNTY.g3QAAAABbQAAAAtfY3NyZl90b2tlbm0AAAAYQnU0c0NUSTNDRWJ2V1QxSS05ckVtOXRf.S4XjQhTKAhl-ViMkrCK1P8rCQyz5hZU2-4h4gje0-dc; _liveview_async_load_key=SFMyNTY.g3QAAAABbQAAAAtfY3NyZl90b2tlbm0AAAAYeWpXUUNtLW1Zdi1rWmhPS1I4R1JuVnlJ.T7YZ5jd5TT0IeIzce48C9y29r6lsmoT-tH0yYv0NHbg", "dnt" => "1", "host" => "localhost:4000", "sec-fetch-dest" => "document", "sec-fetch-mode" => "navigate", "sec-fetch-site" => "none", "sec-fetch-user" => "?1", "sec-gpc" => "1", "upgrade-insecure-requests" => "1", "user-agent" => "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:97.0) Gecko/20100101 Firefox/97.0"}, host: "localhost", host_info: :undefined, method: "GET", path: "/demo", path_info: :undefined, peer: {{127, 0, 0, 1}, 58074}, pid: #PID<0.561.0>, port: 4000, qs: "", ref: FlamegraphsWeb.Endpoint.HTTP, scheme: "http", sock: {{127, 0, 0, 1}, 4000}, streamid: 3, version: :"HTTP/1.1"}, %{dispatch: [{:_, [], [{:_, [], Phoenix.Endpoint.Cowboy2Handler, {FlamegraphsWeb.Endpoint, []}}]}], handler: Phoenix.Endpoint.Cowboy2Handler, handler_opts: {FlamegraphsWeb.Endpoint, []}})
```
