# Frontend 2021 Winter Challenge

El proposito de este challenge es medir las habilidades y conocimientos de los principios fundamentales de React del participante.

## Descripcion del problema

Un despacho de contadores requiere el desarrollo de una interfaz para controlar las cuentas por cobrar de sus clientes morosos.  En esta interfaz no se puede actualizar la informacion de un cliente, cuenta por cobrar o abono. Solo se puede ver informacion y crear nuevos abonos. Esto, debido a la relacion que un abono tiene con una cuenta por cobrar y que esta tiene con un cliente se actualiza toda la informacion de una forma consistente.

Un cliente del despacho puede tener muchas cuentas por cobrar de una sola factura, las cuentas por cobrar pueden tener multiples abonos, es la suma de estos abonos lo que nos permite estimar el total abonado, el total original menos el total abonado nos da el saldo restante.

La REST API que alimenta al frontend esta siendo desarrollada asi que se debera usar **JSON Server** para simular el flujo de informacion.

Los recursos del API con sus metodos HTTP estan descritos de la siguiente manera:

 - GET **/clientes**
	 
	 -  nombre: `str`. Nombre del cliente.
	 -  tipo: `str`. Tipo de cliente juridico o fisico.
	 -  identificacion: `int`. Numero de identificacion.
	 -  telefono: `int`. Numero de telefono.
	 -  horario: `str`. Horario de atencion del cliente.
	 -  estado: `bool`. Determina si este cliente se encuentra activo.
	 - cuentas-por-cobrar: `array<Obj<str, int>>`. Arreglo de objetos de ids de cuentas por cobrar de este cliente.
- GET **/cuentasPorCobrar**
	
	-id: `int`. ID unico de una cuenta por cobrar. 
	- cliente-identificacion: `int`. Identificacion del cliente al que esta cuenta por cobrar pertenece.
	- cliente-nombre: `str`. Nombre del cliente al que esta cuenta por cobrar pertenece.
	- numero-factura: `int`. Numero unico de factura de la cuenta por cobrar.
	- condicion: `str`. Tipo de cuenta por cobrar.
	- plazo-vencimiento: `str`. Duracion de la cuenta por cobrar.
	- total-original: `int`. Total original .
	- saldo-restante: `int`. Monto pediente resultante del total original menos el total de abonos.
	- abonos: `array<Obj>`: Un arreglo de objetos `Abono` con la siguiente informacion para cada uno:
		- id: `int`. Identificador unico del abono.
		- metodo-de-pago: `str`. El metodo de pago **siempre** sera efectivo.
		- monto: `int`. Monto del abono.
- GET **/abonos**
	
	- cuenta-por-cobrar-id: `int` ID unico de la cuenta por cobrar al que este abono pertenece.
	- id: `int`. Identificador unico del abono.
	- metodo-de-pago: `str`. El metodo de pago **siempre** sera efectivo
	- monto: `int`. Monto del abono
- POST **/abonos**
- 
	- cuenta-por-cobrar-id: `int` ID unico de la cuenta por cobrar al que este abono pertenece. Tiene que ser un id valido de 	una cuenta por cobrar
	- id: `int`. Identificador unico del abono.
	- metodo-de-pago: `str`. El metodo de pago **siempre** sera efectivo
	- monto: `int`. Monto del abono

## Diseño
La aplicacion consistira de 2 paginas y un modal. Los diseños de la aplicacion final deberan ser lo mas parecido al diseño propuesto:

🎨. [Diseño Figma - App Cuentas por Cobrar](https://www.figma.com/file/3bongHs6ujubRLg4GKFU9d/App-Cuentas-Por-Cobrar?node-id=0%3A1)

## Informacion de Implementacion
Inicializar el fake API de JSON Server con 7 clientes, y cada cliente tiene que tener al menos 2 cuentas por cobrar.

Se recomienda utilizar las siguientes librerias para el desarrollo de la aplicacion, estas cubren las diferentes necesidades que puedan surgir:
- [react-router-dom](https://v5.reactrouter.com/web/guides/quick-start)
- Cliente HTTP: 
	- [axios](https://axios-http.com/); ó
	- [Fetch API (nativo de JS)](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
- [MaterialUI](https://mui.com/)
- [Material Icons (from MUI)](https://mui.com/components/material-icons/)
- [React Context API](https://reactjs.org/docs/context.html)
