# Aspire Dashboard

## 簡単起動

```bash
docker run --rm -it -p 18888:18888 -p 4317:18889 -d --name aspire-dashboard mcr.microsoft.com/dotnet/aspire-dashboard:latest
```

## webapiをトレース

```bash
dotnet workload update
dotnet workload install aspire
```

## なんか動かないなと思ったら

GitHub Codespacesで動かしているときに動かないと思ったらTrusted Domainやプロトコル、公開の状態をみると良い。
