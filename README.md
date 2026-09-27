# Restaurante App 
## Tema
Componentes y contenedores con Tkinder

## Datos del estudiante

**Nombre**: Bonner Javier García Guanga

## Descripción del proyecto
Restaurante App es una aplicación desarrollada en Python utilizando Tkinder. El proyecto ha evolucionado progresivamente durante las diferentes semanas de la asignatra, amnteniendo la misma arquitectura basada en modelos, servicios, interfaz gráfica y persistencia de datos en archivos JSON.
En esta semana 15 se incorpora la gestión de ventas, permitiendo registrar las ventas realizadas a los usuarios mediante una interfaz amigable.

## Objetivo de la semana 15

El objetivo de esta práctica es continuar con la evolución del proyecto Restaurante App incorporando una nueva funcionalidad para el registro de ventas.
Además, se aplica el uso de eventos mediante `command=` y `callbacks` en Tkinder para responder a las acciones realizadas para el usuario dentro de la aplicación.

## Estructura del proyecto

```text
restaurante_app/
├── assets/
│   ├── icons/
│   │   ├── home.png
│   │   ├── users.png
│   │   ├── products.png
│   │   ├── sales.png        
│   │   ├── logout.png
│   │   ├── add.png
│   │   ├── edit.png
│   │   ├── delete.png
│   │   ├── search.png
│   │   └── clean.png
│   └── logo/
│       ├── logo.png
│       └── icono.png
├── datos/
│   ├── productos.json
│   ├── usuarios.json
│   └── ventas.json
├── modelos/
│   ├── usuario.py
│   ├── producto.py
│   └── venta.py
├── servicios/
│   ├── archivo_servicio.py
│   └── restaurante_servicio.py
├── ui/
│   ├── login_view.py
│   └── main_view.py
└── main.py
```

## Capas

`modelos/`: define las clases `Usuario` y `Producto` y `Venta`, con validaciones basicas para evitar campos vacios.

`servicios/`: contiene la logica de consulta, registro, actualizacion, eliminacion y persistencia. `RestauranteServicio` tambien registra ventas.

`datos/`: guarda la informacion persistente en archivos JSON.

`ui/`: contiene las vistas creadas con Tkinter.

`assets/icons/`: contiene los iconos PNG usados por los botones. 

`assets/logo/`: contiene la identidad visual principal de la aplicacion. `logo.png` se muestra dentro de la interfaz y `icono.png` se usa como icono de la ventana.

## Pantallas principales

`LoginView`: pantalla de inicio de sesion.

`Inicio`: panel de resumen con usuarios, libros y ventas.

`Usuarios`: pantalla de consulta de usuarios registrados.

`Productos`: pantalla de gestion con formulario, botones y tabla para el CRUD basico.

`Ventas`: pantalla nueva para seleccionar un usuario, seleccionar un producto y registrar una venta simple.

## Componentes Tkinter utilizados

`Label`: textos y titulos.

`Entry`: campos de entrada para login y formulario de productos.

`ttk.Combobox`: selectores de usuario y producto en la vista de ventas.

`ttk.Button`: botones de navegacion y acciones con `command=`.

`ttk.Treeview`: tablas de usuarios, productos y ventas.

`ttk.Scrollbar`: barra de desplazamiento para las tablas.

`messagebox`: mensajes simples de confirmacion o error.

## Nueva funcionalidad

La venta relaciona:

```text
Usuario + producto + Fecha -> Venta
```

La seccion `Ventas` permite:

- seleccionar un usuario registrado con `ttk.Combobox`;
- seleccionar un producto registrado con `ttk.Combobox`;
- pulsar el boton `Registrar venta`;
- ejecutar el callback `registrar_venta()` mediante `command=`;
- guardar la venta en `datos/ventas.json`;
- mostrar las ventas registradas en un `ttk.Treeview`.


## Persistencia

Los usuarios, productos y ventas se cargan desde JSON al iniciar la aplicacion.

```text
restaurante_app/datos/usuarios.json
restaurante_app/datos/productos.json
restaurante_app/datos/ventas.json
```

Al registrar una venta, el servicio agrega el objeto a la coleccion en memoria, convierte las ventas a datos serializables y escribe `ventas.json`.

## Flujo de funcionamiento

- El usuario inicia sesión.
- Se muestra el panel principal.
- El usuario puede consultar usuarios.
- Puede registrar, actualizar o eliminar productos.
- Puede registrar ventas seleccionando usuario, producto y cantidad.
- La información se guarda automáticamente en archivos JSON.
- Las tablas muestran la información actualizada en tiempo real.

## Ejecución del proyecto

1. Abrir el proyecto en Visual Studio Code.
2. Verificar que existan los archivos JSON dentro de la carpeta datos.
3. Ejecutar el archivo principal:
```text
python main.py
```
4. Ingresar con un usuario registrado.
5. Utilizar el menú lateral para acceder a Usuarios, Productos o Ventas.

## Credencial de demostración

Usuario: `admin`

Contrasena: `1234`

## Conclusión
Durante esta práctica se fortaleció el desarrollo de aplicaciones gráficas utilizando Tkinter. Se implementó una nueva funcionalidad para la gestión de ventas aplicando eventos mediante command= y callbacks para responder a las acciones del usuario. También se mantuvo la arquitectura modular del proyecto utilizando modelos, servicios e interfaz gráfica, además de la persistencia de información mediante archivos JSON, lo que facilita el mantenimiento y la evolución futura de la aplicación.