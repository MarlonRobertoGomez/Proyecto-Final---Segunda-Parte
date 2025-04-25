namespace BibliotecaApp.Shared
{
    public class Categoria
    {
        public int Id { get; set; }
        public string Nombre { get; set; }
    }
}

namespace BibliotecaApp.Client.Services
{
    public interface ICategoriaService
    {
        Task<List<Categoria>> GetCategoriasAsync();
        Task<Categoria> GetCategoriaByIdAsync(int id);
        Task<bool> CreateCategoriaAsync(Categoria categoria);
        Task<bool> UpdateCategoriaAsync(Categoria categoria);
        Task<bool> DeleteCategoriaAsync(int id);
    }
}

namespace BibliotecaApp.Client.Services
{
    public class CategoriaService : ICategoriaService
    {
        private readonly HttpClient _httpClient;
        private const string BaseUrl = "https://localhost:5001/api/categorias";

        public CategoriaService(HttpClient httpClient)
        {
            _httpClient = httpClient;
        }

        public async Task<List<Categoria>> GetCategoriasAsync()
        {
            return await _httpClient.GetFromJsonAsync<List<Categoria>>(BaseUrl);
        }

        public async Task<Categoria> GetCategoriaByIdAsync(int id)
        {
            return await _httpClient.GetFromJsonAsync<Categoria>($"{BaseUrl}/{id}");
        }

        public async Task<bool> CreateCategoriaAsync(Categoria categoria)
        {
            var response = await _httpClient.PostAsJsonAsync(BaseUrl, categoria);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> UpdateCategoriaAsync(Categoria categoria)
        {
            var response = await _httpClient.PutAsJsonAsync($"{BaseUrl}/{categoria.Id}", categoria);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> DeleteCategoriaAsync(int id)
        {
            var response = await _httpClient.DeleteAsync($"{BaseUrl}/{id}");
            return response.IsSuccessStatusCode;
        }
    }
}


public class Autor
{
    public int Id { get; set; }
    public string Nombre { get; set; } = string.Empty;
    public string Nacionalidad { get; set; } = string.Empty;
    public DateTime FechaNacimiento { get; set; }
    public string Biografia { get; set; } = string.Empty;
}

public class AutorService
{
    private readonly HttpClient _http;

    public AutorService(HttpClient http)
    {
        _http = http;
    }

    public async Task<List<Autor>> GetAutoresAsync()
    {
        return await _http.GetFromJsonAsync<List<Autor>>("api/autores") ?? new List<Autor>();
    }

    public async Task<Autor?> GetAutorByIdAsync(int id)
    {
        return await _http.GetFromJsonAsync<Autor>($"api/autores/{id}");
    }

    public async Task<bool> SaveAutorAsync(Autor autor)
    {
        if (autor.Id == 0)
            return (await _http.PostAsJsonAsync("api/autores", autor)).IsSuccessStatusCode;
        else
            return (await _http.PutAsJsonAsync($"api/autores/{autor.Id}", autor)).IsSuccessStatusCode;
    }

    public async Task<bool> DeleteAutorAsync(int id)
    {
        return (await _http.DeleteAsync($"api/autores/{id}")).IsSuccessStatusCode;
    }
}


namespace BibliotecaApp.Shared
{
    public class DetallePrestamo
    {
        public int Id { get; set; }
        public int PrestamoId { get; set; }
        public int LibroId { get; set; }
        public string LibroTitulo { get; set; }
        public DateTime FechaDevolucion { get; set; }
        public bool EsDevuelto { get; set; }
    }
}

namespace BibliotecaApp.Client.Services
{
    public interface IDetallePrestamoService
    {
        Task<List<DetallePrestamo>> GetDetallePrestamosAsync();
        Task<DetallePrestamo> GetDetallePrestamoByIdAsync(int id);
        Task<bool> CreateDetallePrestamoAsync(DetallePrestamo detallePrestamo);
        Task<bool> UpdateDetallePrestamoAsync(DetallePrestamo detallePrestamo);
        Task<bool> DeleteDetallePrestamoAsync(int id);
    }
}

namespace BibliotecaApp.Client.Services
{
    public class DetallePrestamoService : IDetallePrestamoService
    {
        private readonly HttpClient _httpClient;
        private const string BaseUrl = "https://localhost:5001/api/detalleprestamos";

        public DetallePrestamoService(HttpClient httpClient)
        {
            _httpClient = httpClient;
        }

        public async Task<List<DetallePrestamo>> GetDetallePrestamosAsync()
        {
            return await _httpClient.GetFromJsonAsync<List<DetallePrestamo>>(BaseUrl);
        }

        public async Task<DetallePrestamo> GetDetallePrestamoByIdAsync(int id)
        {
            return await _httpClient.GetFromJsonAsync<DetallePrestamo>($"{BaseUrl}/{id}");
        }

        public async Task<bool> CreateDetallePrestamoAsync(DetallePrestamo detallePrestamo)
        {
            var response = await _httpClient.PostAsJsonAsync(BaseUrl, detallePrestamo);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> UpdateDetallePrestamoAsync(DetallePrestamo detallePrestamo)
        {
            var response = await _httpClient.PutAsJsonAsync($"{BaseUrl}/{detallePrestamo.Id}", detallePrestamo);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> DeleteDetallePrestamoAsync(int id)
        {
            var response = await _httpClient.DeleteAsync($"{BaseUrl}/{id}");
            return response.IsSuccessStatusCode;
        }
    }
}


namespace BibliotecaApp.Shared
{
    public class Editorial
    {
        public int Id { get; set; }
        public string Nombre { get; set; }
    }
}

namespace BibliotecaApp.Client.Services
{
    public interface IEditorialService
    {
        Task<List<Editorial>> GetEditorialesAsync();
        Task<Editorial> GetEditorialByIdAsync(int id);
        Task<bool> CreateEditorialAsync(Editorial editorial);
        Task<bool> UpdateEditorialAsync(Editorial editorial);
        Task<bool> DeleteEditorialAsync(int id);
    }
}

namespace BibliotecaApp.Client.Services
{
    public class EditorialService : IEditorialService
    {
        private readonly HttpClient _httpClient;
        private const string BaseUrl = "https://localhost:5001/api/editoriales";

        public EditorialService(HttpClient httpClient)
        {
            _httpClient = httpClient;
        }

        public async Task<List<Editorial>> GetEditorialesAsync()
        {
            return await _httpClient.GetFromJsonAsync<List<Editorial>>(BaseUrl);
        }

        public async Task<Editorial> GetEditorialByIdAsync(int id)
        {
            return await _httpClient.GetFromJsonAsync<Editorial>($"{BaseUrl}/{id}");
        }

        public async Task<bool> CreateEditorialAsync(Editorial editorial)
        {
            var response = await _httpClient.PostAsJsonAsync(BaseUrl, editorial);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> UpdateEditorialAsync(Editorial editorial)
        {
            var response = await _httpClient.PutAsJsonAsync($"{BaseUrl}/{editorial.Id}", editorial);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> DeleteEditorialAsync(int id)
        {
            var response = await _httpClient.DeleteAsync($"{BaseUrl}/{id}");
            return response.IsSuccessStatusCode;
        }
    }
}


namespace BibliotecaApp.Shared
{
    public class Libro
    {
        public int Id { get; set; }
        public string Titulo { get; set; }
        public string Autor { get; set; }
        public string Categoria { get; set; }
        public string Editorial { get; set; }
    }
}

namespace BibliotecaApp.Client.Services
{
    public interface ILibroService
    {
        Task<List<Libro>> GetLibrosAsync();
        Task<Libro> GetLibroByIdAsync(int id);
        Task<bool> CreateLibroAsync(Libro libro);
        Task<bool> UpdateLibroAsync(Libro libro);
        Task<bool> DeleteLibroAsync(int id);
    }
}

namespace BibliotecaApp.Client.Services
{
    public class LibroService : ILibroService
    {
        private readonly HttpClient _httpClient;
        private const string BaseUrl = "https://localhost:5001/api/libros"; 

        public LibroService(HttpClient httpClient)
        {
            _httpClient = httpClient;
        }

        public async Task<List<Libro>> GetLibrosAsync()
        {
            return await _httpClient.GetFromJsonAsync<List<Libro>>(BaseUrl);
        }

        public async Task<Libro> GetLibroByIdAsync(int id)
        {
            return await _httpClient.GetFromJsonAsync<Libro>($"{BaseUrl}/{id}");
        }

        public async Task<bool> CreateLibroAsync(Libro libro)
        {
            var response = await _httpClient.PostAsJsonAsync(BaseUrl, libro);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> UpdateLibroAsync(Libro libro)
        {
            var response = await _httpClient.PutAsJsonAsync($"{BaseUrl}/{libro.Id}", libro);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> DeleteLibroAsync(int id)
        {
            var response = await _httpClient.DeleteAsync($"{BaseUrl}/{id}");
            return response.IsSuccessStatusCode;
        }
    }
}


namespace BibliotecaApp.Shared
{
    public class Prestamo
    {
        public int Id { get; set; }
        public string Usuario { get; set; }
        public string Libro { get; set; }
        public DateTime FechaPrestamo { get; set; }
        public DateTime FechaDevolucion { get; set; }
    }
}

namespace BibliotecaApp.Client.Services
{
    public interface IPrestamoService
    {
        Task<List<Prestamo>> GetPrestamosAsync();
        Task<Prestamo> GetPrestamoByIdAsync(int id);
        Task<bool> CreatePrestamoAsync(Prestamo prestamo);
        Task<bool> UpdatePrestamoAsync(Prestamo prestamo);
        Task<bool> DeletePrestamoAsync(int id);
    }
}

namespace BibliotecaApp.Client.Services
{
    public class PrestamoService : IPrestamoService
    {
        private readonly HttpClient _httpClient;
        private const string BaseUrl = "https://localhost:5001/api/prestamos";

        public PrestamoService(HttpClient httpClient)
        {
            _httpClient = httpClient;
        }

        public async Task<List<Prestamo>> GetPrestamosAsync()
        {
            return await _httpClient.GetFromJsonAsync<List<Prestamo>>(BaseUrl);
        }

        public async Task<Prestamo> GetPrestamoByIdAsync(int id)
        {
            return await _httpClient.GetFromJsonAsync<Prestamo>($"{BaseUrl}/{id}");
        }

        public async Task<bool> CreatePrestamoAsync(Prestamo prestamo)
        {
            var response = await _httpClient.PostAsJsonAsync(BaseUrl, prestamo);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> UpdatePrestamoAsync(Prestamo prestamo)
        {
            var response = await _httpClient.PutAsJsonAsync($"{BaseUrl}/{prestamo.Id}", prestamo);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> DeletePrestamoAsync(int id)
        {
            var response = await _httpClient.DeleteAsync($"{BaseUrl}/{id}");
            return response.IsSuccessStatusCode;
        }
    }
}


namespace BibliotecaApp.Shared
{
    public class Reserva
    {
        public int Id { get; set; }
        public int UsuarioId { get; set; }
        public int LibroId { get; set; }
        public DateTime FechaReserva { get; set; }
        public DateTime FechaLimite { get; set; }
        public bool EstaReservado { get; set; }
    }
}

namespace BibliotecaApp.Client.Services
{
    public interface IReservaService
    {
        Task<List<Reserva>> GetReservasAsync();
        Task<Reserva> GetReservaByIdAsync(int id);
        Task<bool> CreateReservaAsync(Reserva reserva);
        Task<bool> UpdateReservaAsync(Reserva reserva);
        Task<bool> DeleteReservaAsync(int id);
    }
}

namespace BibliotecaApp.Client.Services
{
    public class ReservaService : IReservaService
    {
        private readonly HttpClient _httpClient;
        private const string BaseUrl = "https://localhost:5001/api/reservas";

        public ReservaService(HttpClient httpClient)
        {
            _httpClient = httpClient;
        }

        public async Task<List<Reserva>> GetReservasAsync()
        {
            return await _httpClient.GetFromJsonAsync<List<Reserva>>(BaseUrl);
        }

        public async Task<Reserva> GetReservaByIdAsync(int id)
        {
            return await _httpClient.GetFromJsonAsync<Reserva>($"{BaseUrl}/{id}");
        }

        public async Task<bool> CreateReservaAsync(Reserva reserva)
        {
            var response = await _httpClient.PostAsJsonAsync(BaseUrl, reserva);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> UpdateReservaAsync(Reserva reserva)
        {
            var response = await _httpClient.PutAsJsonAsync($"{BaseUrl}/{reserva.Id}", reserva);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> DeleteReservaAsync(int id)
        {
            var response = await _httpClient.DeleteAsync($"{BaseUrl}/{id}");
            return response.IsSuccessStatusCode;
        }
    }
}


namespace BibliotecaApp.Shared
{
    public class Rol
    {
        public int Id { get; set; }
        public string Nombre { get; set; }
        public string Descripcion { get; set; }
    }
}

namespace BibliotecaApp.Client.Services
{
    public interface IRolService
    {
        Task<List<Rol>> GetRolesAsync();
        Task<Rol> GetRolByIdAsync(int id);
        Task<bool> CreateRolAsync(Rol rol);
        Task<bool> UpdateRolAsync(Rol rol);
        Task<bool> DeleteRolAsync(int id);
    }
}

namespace BibliotecaApp.Client.Services
{
    public class RolService : IRolService
    {
        private readonly HttpClient _httpClient;
        private const string BaseUrl = "https://localhost:5001/api/roles";

        public RolService(HttpClient httpClient)
        {
            _httpClient = httpClient;
        }

        public async Task<List<Rol>> GetRolesAsync()
        {
            return await _httpClient.GetFromJsonAsync<List<Rol>>(BaseUrl);
        }

        public async Task<Rol> GetRolByIdAsync(int id)
        {
            return await _httpClient.GetFromJsonAsync<Rol>($"{BaseUrl}/{id}");
        }

        public async Task<bool> CreateRolAsync(Rol rol)
        {
            var response = await _httpClient.PostAsJsonAsync(BaseUrl, rol);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> UpdateRolAsync(Rol rol)
        {
            var response = await _httpClient.PutAsJsonAsync($"{BaseUrl}/{rol.Id}", rol);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> DeleteRolAsync(int id)
        {
            var response = await _httpClient.DeleteAsync($"{BaseUrl}/{id}");
            return response.IsSuccessStatusCode;
        }
    }
}


namespace BibliotecaApp.Shared
{
    public class Ubicacion
    {
        public int Id { get; set; }
        public int LibroId { get; set; }
        public string Estante { get; set; }
        public string Seccion { get; set; }
        public string Pasillo { get; set; }
    }
}

namespace BibliotecaApp.Client.Services
{
    public interface IUbicacionService
    {
        Task<List<Ubicacion>> GetUbicacionesAsync();
        Task<Ubicacion> GetUbicacionByIdAsync(int id);
        Task<bool> CreateUbicacionAsync(Ubicacion ubicacion);
        Task<bool> UpdateUbicacionAsync(Ubicacion ubicacion);
        Task<bool> DeleteUbicacionAsync(int id);
    }
}

namespace BibliotecaApp.Client.Services
{
    public class UbicacionService : IUbicacionService
    {
        private readonly HttpClient _httpClient;
        private const string BaseUrl = "https://localhost:5001/api/ubicaciones";

        public UbicacionService(HttpClient httpClient)
        {
            _httpClient = httpClient;
        }

        public async Task<List<Ubicacion>> GetUbicacionesAsync()
        {
            return await _httpClient.GetFromJsonAsync<List<Ubicacion>>(BaseUrl);
        }

        public async Task<Ubicacion> GetUbicacionByIdAsync(int id)
        {
            return await _httpClient.GetFromJsonAsync<Ubicacion>($"{BaseUrl}/{id}");
        }

        public async Task<bool> CreateUbicacionAsync(Ubicacion ubicacion)
        {
            var response = await _httpClient.PostAsJsonAsync(BaseUrl, ubicacion);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> UpdateUbicacionAsync(Ubicacion ubicacion)
        {
            var response = await _httpClient.PutAsJsonAsync($"{BaseUrl}/{ubicacion.Id}", ubicacion);
            return response.IsSuccessStatusCode;
        }

        public async Task<bool> DeleteUbicacionAsync(int id)
        {
            var response = await _httpClient.DeleteAsync($"{BaseUrl}/{id}");
            return response.IsSuccessStatusCode;
        }
    }
}


public class Usuario
{
    public int UsuarioId { get; set; }
    public string Nombre { get; set; }
    public string Apellido { get; set; }
    public string Correo { get; set; }
    public string Telefono { get; set; }
    public string Direccion { get; set; }
    public string UsuarioLogin { get; set; }
    public string Clave { get; set; }
    public int RolId { get; set; }
}

using System.Net.Http.Json;

public class UsuarioService
{
    private readonly HttpClient _http;

    public UsuarioService(HttpClient http)
    {
        _http = http;
    }

    public async Task<List<Usuario>> GetUsuariosAsync()
    {
        return await _http.GetFromJsonAsync<List<Usuario>>("api/usuarios");
    }

    public async Task<Usuario> GetUsuarioByIdAsync(int id)
    {
        return await _http.GetFromJsonAsync<Usuario>($"api/usuarios/{id}");
    }

    public async Task<bool> SaveUsuarioAsync(Usuario usuario)
    {
        if (usuario.UsuarioId == 0)
        {
            var response = await _http.PostAsJsonAsync("api/usuarios", usuario);
            return response.IsSuccessStatusCode;
        }
        else
        {
            var response = await _http.PutAsJsonAsync($"api/usuarios/{usuario.UsuarioId}", usuario);
            return response.IsSuccessStatusCode;
        }
    }

    public async Task<bool> DeleteUsuarioAsync(int id)
    {
        var response = await _http.DeleteAsync($"api/usuarios/{id}");
        return response.IsSuccessStatusCode;
    }
}
