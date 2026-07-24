# ☕ DeliveryBot

DeliveryBot es una solución de automatización desarrollada en **n8n** que permite gestionar pedidos de cafetería mediante un chatbot de **Telegram**. El sistema busca reducir las filas, minimizar errores en la toma de pedidos y mejorar la comunicación entre los clientes y el personal de cocina.

![alt text](image.png)

- Google Sheets: https://docs.google.com/spreadsheets/d/14AMz5i5fAOS7Ja4Q7S6VHrxyUcMJo7B7z5Tc4NEKKWM/edit?usp=sharing

---

# 📖 Problemática

En instituciones como universidades, oficinas o centros de trabajo, la gestión de pedidos en cafeterías suele realizarse de forma manual, generando:

- Largas filas durante las horas de mayor demanda.
- Errores al registrar pedidos.
- Dificultad para controlar el inventario.
- Falta de comunicación entre la cocina y el cliente.
- Ausencia de reportes automáticos de ventas.

DeliveryBot digitaliza este proceso utilizando Telegram como interfaz conversacional y n8n como motor de automatización.

---

# 🎯 Objetivos

- Automatizar el proceso de pedidos mediante Telegram.
- Permitir la navegación por categorías del menú.
- Gestionar un carrito de compras.
- Validar disponibilidad de productos.
- Generar pedidos con identificadores únicos.
- Actualizar automáticamente el inventario.
- Notificar a cocina cuando exista un nuevo pedido.
- Informar al cliente sobre el estado de su orden.
- Generar reportes automáticos de ventas.

---

# 🛠 Tecnologías utilizadas

- n8n
- Telegram Bot API
- Google Sheets
- JavaScript
- Docker
- Ngrok

---

# 🗄 Base de Datos

El sistema utiliza Google Sheets como base de datos.

## MENU

| Campo | Descripción |
|---------|------------|
| id_producto | Identificador del producto |
| nombre | Nombre del producto |
| descripcion | Descripción |
| precio | Precio |
| categoria | Bebidas, Comidas o Snacks |
| stock | Cantidad disponible |

---

## PEDIDOS

| Campo | Descripción |
|---------|------------|
| id_pedido | Identificador del pedido |
| id_usuario | Usuario que realizó el pedido |
| detalles_pedido | Productos solicitados |
| total_pago | Valor total |
| estado | Estado actual |
| fecha | Fecha |
| hora | Hora |

---

## USUARIOS

| Campo | Descripción |
|---------|------------|
| telegram_id | ID del usuario |
| nombre_completo | Nombre |

---

## SESSIONS

Permite mantener el estado de la conversación.

| Campo | Descripción |
|---------|------------|
| telegram_id | Usuario |
| pantalla_actual | Estado del flujo |
| carrito_temporal | Productos seleccionados |
| ultimo_cambio | Última actualización |

---

# ⚙ Arquitectura del proyecto

El proyecto está dividido en tres workflows independientes.

## 1. Workflow Cliente

Se encarga de toda la interacción con el usuario.

### Funciones

- Registro automático del usuario.
- Consulta del menú.
- Navegación por categorías.
- Selección de productos.
- Gestión del carrito.
- Confirmación del pedido.
- Actualización de sesiones.
- Registro del pedido.
- Notificaciones al cliente.

---

## 2. Workflow Cocina

Responsable de administrar los pedidos recibidos.

### Funciones

- Consultar pedidos pendientes.
- Cambiar el estado del pedido.
- Notificar al cliente cuando el pedido cambia de estado.
- Marcar pedidos como entregados.

Estados utilizados:

- Recibido
- Preparación
- Entregado

---

## 3. Workflow Reportes

Workflow programado mediante un Trigger Scheduler.

Genera automáticamente:

- Total de ventas.
- Cantidad de pedidos.
- Productos más vendidos.
- Reporte diario enviado por correo.

---

# 🔄 Flujo del Cliente

```text
Inicio

↓

Registro automático

↓

Menú principal

↓

Seleccionar categoría

↓

Mostrar productos

↓

Elegir producto

↓

Elegir cantidad

↓

Agregar al carrito

↓

¿Agregar otro producto?

↓

No

↓

Confirmar pedido

↓

Validar stock

↓

Registrar pedido

↓

Actualizar inventario

↓

Notificar cocina

↓

Notificar cliente
```

---

# 🍔 Flujo de Cocina

```text
Nuevo pedido

↓

Consultar pedidos pendientes

↓

Seleccionar pedido

↓

Cambiar estado

↓

Actualizar Google Sheets

↓

Notificar al cliente
```

---

# 📊 Flujo de Reportes

```text
Scheduler

↓

Leer pedidos

↓

Calcular ventas

↓

Generar reporte

↓

Enviar correo
```

---

# 📌 Funcionalidades implementadas

✅ Registro automático de usuarios

✅ Consulta del menú

✅ Navegación por categorías

✅ Selección de productos

✅ Gestión del carrito

✅ Confirmación del pedido

✅ Registro automático en Google Sheets

✅ Actualización del inventario

✅ Gestión de estados del pedido

✅ Notificaciones por Telegram

✅ Reportes automáticos


---

# 🚀 Posibles mejoras

- Pago mediante Nequi o QR.
- Panel web para administración.
- Sistema de puntos y recompensas.
- Historial completo de pedidos.
- Estadísticas en tiempo real.
- Botones interactivos de Telegram.
- Integración con bases de datos SQL.

---

# 👨‍💻 Autores

Proyecto desarrollado por **MARIO ROJAS** como solución académica utilizando **n8n**, **Telegram** y **Google Sheets** para automatizar el proceso de pedidos de cafetería.

# Delivery Bot
![alt text](image-1.png)

# Cocina Bot
![alt text](image-2.png)