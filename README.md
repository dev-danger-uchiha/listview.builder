itemCount → dice cuántos componentes hay en la lista.

itemBuilder → es la receta de cómo se dibuja cada componente. 
              Flutter lo llama cada vez que necesita mostrar uno.

Lazy loading → Flutter no crea todos los ítems de golpe, solo los que caben en pantalla. 
               Cuando haces scroll, construye los nuevos y destruye los viejos.

// Importamos el paquete principal de Flutter.
// Esto nos da acceso a widgets como MaterialApp, Scaffold, ListView, etc.
import 'package:flutter/material.dart';

// Función principal de la app.
// 'runApp' arranca la aplicación y dibuja el widget que le pasemos.
void main() {
  runApp(MyApp());
}

// Creamos un widget sin estado (StatelessWidget).
// Esto significa que no cambia dinámicamente, solo muestra lo que definimos.
class MyApp extends StatelessWidget {
  // Lista de componentes de computador que vamos a mostrar.
  // Es un simple array de Strings con emojis y nombres.
  final List<String> componentes = [
    "💻 Procesador Ryzen 7 7800X3D",
    "🖥️ Tarjeta Gráfica RTX 4080",
    "🔧 Placa Madre B650",
    "💾 Memoria RAM 32GB DDR5",
    "📀 SSD NVMe 1TB",
    "🔌 Fuente de Poder 750W",
    "🌀 Sistema de Refrigeración Líquida",
    "🖱️ Mouse Gamer",
    "⌨️ Teclado Mecánico",
    "🖥️ Monitor 4K 144Hz",
  ];

  // Método build: aquí definimos cómo se dibuja la interfaz.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      // MaterialApp es el contenedor principal de la app con estilo Material Design.
      home: Scaffold(
        // Scaffold es la estructura básica: AppBar arriba y body en el centro.
        appBar: AppBar(title: Text("Componentes de Computador")),
        
        // El cuerpo de la app será un ListView.builder.
        body: ListView.builder(
          // itemCount: cuántos elementos tendrá la lista.
          // Aquí usamos el tamaño de la lista 'componentes'.
          itemCount: componentes.length,

          // itemBuilder: función que construye cada ítem de la lista.
          // Flutter la llama cada vez que necesita mostrar un elemento en pantalla.
          itemBuilder: (context, index) {
            // Usamos ListTile, un widget listo para listas con título, subtítulo e ícono.
            return ListTile(
              leading: Icon(Icons.computer), // Ícono al inicio de cada fila.
              title: Text(componentes[index]), // El nombre del componente.
              subtitle: Text("Ítem número $index"), // Texto adicional con el índice.
            );
          },
        ),
      ),
    );
  }
}
