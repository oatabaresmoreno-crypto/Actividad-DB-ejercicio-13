CREATE DATABASE TECHWORLD;

USE TECHWORLD;

CREATE TABLE categorias1(
	ID INT AUTO_INCREMENT,
	Computadoras VARCHAR (10) NOT NULL,
	Smartphones VARCHAR (12) NOT NULL,
	Accesorios VARCHAR (6) NOT NULL,
	PRIMARY KEY (ID)
);

DESCRIBE categorias1;

CREATE TABLE Documento_de_identidad(
	ID INT AUTO_INCREMENT,
	Registro_civil INT (2) NOT NULL,
	Tarjeta_de_identidad INT (2) NOT NULL,
	Cedula_de_ciudadania INT (2) NOT NULL,
	Pasaporte VARCHAR (2) NOT NULL,
	Cedula_de_extranjeria INT (2) NOT NULL,
	PRIMARY KEY (ID)
	
);

DESCRIBE Documento_de_identidad;

CREATE TABLE facturas(
	ID INT AUTO_INCREMENT,
	Fecha_de_emision DATE NOT NULL,
	Numero_de_factura VARCHAR (4) NOT NULL,
	Impuestos INT (2) NOT NULL,
	Total INT (8) NOT NULL,
	PRIMARY KEY (ID)
);

DESCRIBE facturas;

CREATE TABLE metodo_de_pago(
	ID INT AUTO_INCREMENT,
	Efectivo INT (8) NOT NULL,
	Tarjeta INT (2) NOT NULL,
	Transferencia INT (2) NOT NULL,
	PRIMARY KEY (ID)
);

DESCRIBE metodo_de_pago;

CREATE TABLE producto(
	ID INT AUTO_INCREMENT,
	Codigo_unico VARCHAR (5) NOT NULL,
	Nombre VARCHAR (40) NOT NULL,
	Marca VARCHAR (20) NOT NULL,
	Precio FLOAT (10) NOT NULL,
	Stock_disponible INT (5) NOT NULL,
	categorias_id INT,
	PRIMARY KEY (ID),
	FOREIGN KEY (categorias_id) REFERENCE categorias1(ID)
);

DESCRIBE producto;

CREATE TABLE clientes(
	ID INT AUTO_INCREMENT,
	Nombre_completo VARCHAR	(40) NOT NULL,
	Direccion VARCHAR	(30) NOT NULL,
	Telefono	INT (10) NOT NULL,
	Correo_electronico VARCHAR	(30) NOT NULL,
	documento_de_identidad_id INT,
	producto_id INT,
	metodo_de_pago_id INT,
	PRIMARY KEY (ID),
	FOREIGN KEY (documento_de_identidad_id) REFERENCES documento_de_identidad(ID),
	FOREIGN KEY (producto_id) REFERENCES producto(ID),
	FOREIGN KEY (metodo_de_pago_id) REFERENCES metodo_de_pago(ID)
);

DESCRIBE clientes;

CREATE TABLE venta(
	ID INT AUTO_INCREMENT,
	Fecha DATE NOT NULL,
	Produtos_vendidos INT (2) NOT NULL,
	Monto_total INT (8) NOT NULL,
	facturas_id INT,
	metodo_de_pago_id INT,
	PRIMARY KEY (ID),
	FOREIGN KEY (facturas_id) REFERENCES facturas (ID),
	FOREIGN KEY (metodo_de_pago_id) REFERENCE metodo_de_pago (ID)
	
);

DESCRIBE venta;

CREATE TABLE tecnicos2(
	ID INT AUTO_INCREMENT,
	Codigo_del_tecnico VARCHAR (10) NOT NULL,
	Nombre VARCHAR (40) NOT NULL,
	Especialidad VARCHAR (30) NOT NULL,
	producto_id INT,
	PRIMARY KEY (ID),
	FOREIGN KEY (producto_id) REFERENCES producto(ID)
);

DESCRIBE tecnicos2;


DESCRIBE categorias1;
DESCRIBE Documento_de_identidad;
DESCRIBE facturas;
DESCRIBE metodo_de_pago;
DESCRIBE producto;
DESCRIBE clientes;
DESCRIBE venta;
DESCRIBE tecnicos2;
