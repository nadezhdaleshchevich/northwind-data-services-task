# Northwind Data Services

## Задача 2 - Northwind REST Service

Цели:
* Научиться создавать веб-приложения, используя ASP.NET Core.
* Научиться создавать базовый CRUD RESTful API.
* Научиться использовать версионированный API.
* Научиться документировать API.
* Научиться размещать веб-приложения на платформе Heroku.


### Создание базового приложения ASP.NET Core

1. Изучите:

* [Create web APIs with ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/web-api/?view=aspnetcore-2.2)
* [Tutorial: Create a web API with ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-2.2&tabs=visual-studio)
* [How to: Add Query Options to a Data Service Query (WCF Data Services)](https://docs.microsoft.com/en-us/dotnet/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services)

2. Создайте новое приложение ASP.NET Core:

```
mkdir northwind-basic-app
cd northwind-basic-app
dotnet new webapi -n NorthwindWebApiApp
dotnet new sln -n NorthwindBasicApp
dotnet sln NorthwindBasicApp.sln add NorthwindWebApiApp\NorthwindWebApiApp.csproj
dotnet add NorthwindWebApiApp\NorthwindWebApiApp.csproj package Microsoft.Data.Services.Client
dotnet build
dotnet run --project NorthwindWebApiApp
```

3. Добавьте в проект файлы:

* [OrdersController](task02/northwind-basic-app/NorthwindWebApiApp/Controllers/OrdersController.cs) в папку Controllers.
* [BriefOrderModel.cs](task02/northwind-basic-app/NorthwindWebApiApp/Models/BriefOrderModel.cs) и [FullOrderModel.cs](task02/northwind-basic-app/NorthwindWebApiApp/Models/FullOrderModel.cs) в папку Models.
* [IOrderService.cs](task02/northwind-basic-app/NorthwindWebApiApp/Services/IOrderService.cs) и [OrderService.cs](task02/northwind-basic-app/NorthwindWebApiApp/Services/OrderService.cs) в папку Services.
* Поместите [NorthwindDataService.cs](task02/northwind-basic-app/NorthwindWebApiApp/ExternalServices/NorthwindDataService.cs) (версия 3) в папку External Services.

4. Зарегистрируйте сервис в Startup.cs:

```cs
public void ConfigureServices(IServiceCollection services)
{
	services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
	services.AddScoped<IOrderService, OrderService>();
}
```

#### Создание приложения ASP.NET Web API

https://www.restapitutorial.com/index.html
https://restfulapi.net/

![Northwind OData Service](images/northwind-odata-service.png)

## Ссылки


## Задача 2 - Northwind WebAPI