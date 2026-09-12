# 🏢 RedArbor Employee API (`redarbor-aspnetcore-ado`)

> High-performance RESTful Web API built with **ASP.NET Core** and raw **ADO.NET** data access, Swagger documentation, and Docker support. Developed as an enterprise technical assessment for RedArbor.

---

## 🏛️ Architecture & Design Decisions

- **ADO.NET Direct Data Access** — Bypasses heavy ORM abstractions in favor of direct `SqlConnection` and `SqlCommand` operations with parameterized queries for predictable, low-latency database interactions.
- **Repository Pattern & DI** — Complete separation between HTTP controllers, business service contracts, and ADO.NET persistence repositories via ASP.NET Core built-in Dependency Injection.
- **AutoMapper Integration** — Clean mapping between database data transfer objects (DTOs) and API request/response view models.
- **Swagger / OpenAPI** — Interactive API exploration and contract definition enabled via Swashbuckle.
- **Dockerized Packaging** — Multi-stage Dockerfile for containerized deployment across environments.

---

## 📡 API Endpoints Specification

Base route: `/api/redarbor`

| Method | Route | Description | Expected Status |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/redarbor` | Retrieve all employee records | `200 OK` |
| `GET` | `/api/redarbor/{id}` | Retrieve employee by primary key identifier | `200 OK` / `404 Not Found` |
| `POST` | `/api/redarbor` | Create a new employee entry | `201 Created` / `400 Bad Request` |
| `PUT` | `/api/redarbor/{id}` | Update existing employee record | `200 OK` / `404 Not Found` |
| `DELETE` | `/api/redarbor/{id}` | Delete employee record by ID | `200 OK` / `404 Not Found` |

---

## 🛠️ Tech Stack

- **Framework**: .NET Core / ASP.NET Core Web API
- **Language**: C#
- **Data Access**: ADO.NET (`Microsoft.Data.SqlClient`)
- **Mapping**: AutoMapper
- **Documentation**: Swagger / Swashbuckle
- **Containerization**: Docker

---

## 🚀 Running Locally

### Prerequisites
- [.NET SDK](https://dotnet.microsoft.com/download)
- SQL Server (LocalDB, Docker, or Azure SQL)

### Running via .NET CLI

```bash
# Clone the repository
git clone https://github.com/oscarlopez1991/redarbor-aspnetcore-ado.git
cd redarbor-aspnetcore-ado

# Run database setup scripts (located in scripts/)
# sqlcmd -S localhost -U sa -P YourPassword -i scripts/setup.sql

# Restore dependencies & run the API
dotnet restore
dotnet run --project RedArbor.AspNetCore.WebApi.App
```

Once running, navigate to `http://localhost:5000/swagger` to inspect and test the interactive API documentation.

### Running with Docker

```bash
docker build -t redarbor-api -f RedArbor.AspNetCore.WebApi.App/Dockerfile .
docker run -p 5000:80 redarbor-api
```

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
