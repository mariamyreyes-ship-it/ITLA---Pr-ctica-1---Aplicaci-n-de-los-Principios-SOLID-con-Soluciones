# ITLA - Práctica - 1 - Aplicación de los Principios SOLID con Soluciones
class Program
{
    static void Main(string[] args)
    {
        // SRP - Principio de Responsabilidad Unica
        var pedido = new Pedido("Ana", "Laptop");
        new ServicioPedido().CrearPedido(pedido);
        new ServicioEnvio().EnviarPedido(pedido, "Santo Domingo");
        new ServicioFactura().ImprimirFactura(pedido);

        Console.WriteLine("------");

        // OCP - Principio de Abierto/ Cerrado
        var calculadora = new CalculadoraDeDescuentos();
        double descuento = calculadora.CalcularDescuento(1000, new DescuentoPremium());
        Console.WriteLine($"Descuento aplicado: {descuento}");

        Console.WriteLine("------");

        // LSP - Principio de Sustitución de Liskov
        Vehiculo miVehiculo = new Coche();
        miVehiculo.Conducir();

        Vehiculo miBici = new Bicicleta();
        miBici.Conducir();

        Console.WriteLine("------");

        // ISP - Principio de Segregación de Interfaces
        ITrabajador programador = new Programador();
        programador.Trabajar();

        ITrabajador gerente = new Gerente();
        gerente.Trabajar();

        Console.WriteLine("------");

        // DIP - Principio de Inversión de Dependencias
        IClienteCorreo smtp = new SmtpCliente();
        var envio = new EnvioDeCorreo(smtp);
        envio.EnviarCorreo("cliente@correo.com", "Hola desde SOLID");
    }
}
