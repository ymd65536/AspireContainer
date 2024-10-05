# Aspire Dashboard

## 簡単起動

```bash
docker run --rm -it -p 18888:18888 -p 4317:18889 -d --name aspire-dashboard mcr.microsoft.com/dotnet/aspire-dashboard:latest
```

```bash
dotnet run --project BlazorApp
```

```bash
dotnet run --project webapi
```

```text
https://fluffy-space-fortnight-jj6j4rgqwr2q759-5038.app.github.dev/weatherforecast
```

## webapiをトレース

```bash
dotnet workload update
dotnet workload install aspire
```

## Blazor ServerにAspireを導入する

おおまかな流れ

- appsettings.Development.jsonに環境変数を追加する
- BlazorApp.csprojを修正する
- Extensions.csを追加する
- Program.csにAddServiceDefaultsとMapDefaultEndpointsを追加する

## appsettings.Development.jsonに環境変数を追加する

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "OTEL_EXPORTER_OTLP_ENDPOINT": "http://localhost:4317",
  "OTEL_SERVICE_NAME": "BlazorServer"
}
```

ブラウザでアクセス

- [webapi](https://supreme-funicular-g4945xp7672vqqx-5038.app.github.dev/weatherforecast)
- [BlazorApp](https://supreme-funicular-g4945xp7672vqqx-5016.app.github.dev/)

## なんか動かないなと思ったら

GitHub Codespacesで動かしているときに動かないと思ったらTrusted Domainやプロトコル、公開の状態をみると良い。

## 片付け

```bash
docker stop $(docker ps -q)
docker rmi $(docker images -q)
```
