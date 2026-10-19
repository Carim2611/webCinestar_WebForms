# webCinestar WebForms

Sitio web de una cadena de multicines desarrollado con **ASP.NET Web Forms** y **SQL Server**. Muestra la cartelera, los próximos estrenos y la información de cada cine (dirección, tarifas y horarios por película).

> Proyecto académico de SENATI. Es una recreación con fines educativos del sitio de Multicines Cinestar; no tiene relación oficial con la empresa, y las marcas e imágenes pertenecen a sus dueños.

La misma aplicación también está hecha con MVC: [webCinestar_MVC](https://github.com/Carim2611/webCinestar_MVC).

## Tecnologías

- C# y ASP.NET Web Forms (.NET Framework 4.8.1)
- Master Page (`Cinestar.Master`) y controles `Repeater` para mostrar los datos
- SQL Server con ADO.NET (`System.Data.SqlClient`)
- Acceso a datos mediante **stored procedures**
- HTML y CSS

## Funcionalidades

- **Cartelera** y **próximos estrenos**: listado de películas con sinopsis, botón de más información y de tráiler.
- **Detalle de película**: título, sinopsis, fecha de estreno, género, director, reparto y tráiler.
- **Nuestros cines**: listado con dirección, detalle y teléfonos.
- **Detalle de cine**: tarifas por días de la semana y películas con sus horarios.
- Redirección a la página de inicio cuando falta un parámetro o no hay datos.

## Estructura del proyecto

```text
webCinestar_WebForms/
├── Controllers/
│   ├── CinestarController.cs   # Llama a los stored procedures
│   └── Db.cs                   # Conexión y ejecución con SqlClient
├── Views/
│   ├── Cinestar.Master         # Plantilla común
│   ├── index.aspx
│   ├── cines.aspx
│   ├── cine.aspx
│   ├── peliculas.aspx
│   └── pelicula.aspx
└── Contents/                   # CSS e imágenes
```

## Páginas

| Página | Descripción |
| ------ | ----------- |
| `Views/index.aspx` | Inicio |
| `Views/cines.aspx` | Listado de cines |
| `Views/cine.aspx?id={id}` | Detalle de un cine |
| `Views/peliculas.aspx?id=cartelera` | Películas en cartelera |
| `Views/peliculas.aspx?id=estrenos` | Próximos estrenos |
| `Views/pelicula.aspx?id={id}` | Detalle de una película |

## Base de datos

Usa una base de datos SQL Server llamada `CineStar` y consume estos stored procedures:

`sp_getCines`, `sp_getCine`, `sp_getCineTarifas`, `sp_getCinePeliculas`, `sp_getPeliculas`, `sp_getPelicula`

## Capturas

## Capturas

| Nuestros cines | Detalle de cine |
| :---: | :---: |
| <img width="450" alt="Nuestros cines" src="https://github.com/user-attachments/assets/724433df-7cd6-4b0a-bb2d-ef0614c2d770" /> | <img width="450" alt="Detalle de cine" src="https://github.com/user-attachments/assets/614af341-1ff0-4b79-bf49-7eb5b311e1c7" /> |

| Cartelera | Detalle de película |
| :---: | :---: |
| <img width="450" alt="Cartelera" src="https://github.com/user-attachments/assets/d33a7865-25c1-4a38-8445-bbca19af7559" /> | <img width="450" alt="Detalle de película" src="https://github.com/user-attachments/assets/e731218a-17d9-4278-8420-70bdb0f9ca25" /> |

## Instalación y ejecución

### Requisitos

- Visual Studio con la carga de trabajo de desarrollo web ASP.NET
- .NET Framework 4.8.1
- SQL Server (LocalDB, Express o superior)

### Pasos

1. Clonar el repositorio:

   ```bash
   git clone https://github.com/Carim2611/webCinestar_WebForms.git
   ```

2. Crear la base de datos `CineStar` en SQL Server con sus tablas y los stored procedures indicados arriba.
3. Abrir `webCineStar_WebForms_202620.sln` en Visual Studio; los paquetes NuGet se restauran automáticamente.
4. Configurar la cadena de conexión en `Web.config`, dentro de `<connectionStrings>`, con el nombre `cnCineStar` apuntando a tu servidor:

   ```xml
   <add name="cnCineStar"
        connectionString="Data Source=.;Initial Catalog=CineStar;Integrated Security=True;TrustServerCertificate=True"
        providerName="System.Data.SqlClient" />
   ```

5. Ejecutar con `F5` (IIS Express) y abrir `Views/index.aspx`.

## Autor

**Carim Estrada** — [@Carim2611](https://github.com/Carim2611)
