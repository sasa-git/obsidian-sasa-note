`docker compose run --rm web mix phx.gen.context Service AccountDailyStat account_daily_stats account_id:references:accounts year:integer month:integer day:integer scenario_created_count:integer loadtest_execution_count:inte
ger loadtest_execution_time:integer`

> The SampleWeb.Service context currently has 73 functions and 11 files in its directory.
> 
>   * It's OK to have multiple resources in the same context as long as they are closely related. But if a context grows too > large, consider breaking it apart
> 
>   * If they are not closely related, another context probably works better
> 
> The fact two entities are related in the database does not mean they belong to the same context.
> 
> If you are not sure, prefer creating a new context over adding to the existing one.

