# NetBank

NetBank es una aplicación web bancaria (Internet Banking) robusta desarrollada en **ASP.NET Core (C#)** siguiendo los principios de **Onion Architecture** (Arquitectura Cebolla) y el patrón **MVC** para la capa de presentación. 

Este proyecto simula las operaciones completas de un banco comercial, permitiendo la gestión de usuarios, cuentas de ahorro, tarjetas de crédito, préstamos y diferentes tipos de pagos y transferencias.

## 🏛️ Arquitectura

La solución está estructurada en múltiples capas para garantizar la separación de responsabilidades y un bajo acoplamiento, siguiendo los principios de la **Onion Architecture** (Arquitectura Cebolla):

*   **NetBank.Core.Domain**: Contiene las entidades principales del negocio (Product, Transaction, Payment, Beneficiarie) y las enumeraciones.
*   **NetBank.Core.Application**: Implementa la lógica de negocio, interfaces de servicios, DTOs y ViewModels.
*   **NetBank.Infraestructure.Identity**: Maneja la autenticación, autorización y gestión de roles genéricos.
*   **NetBank.Infraestructure.Persistence**: Gestiona en Entity Framework Core todo el contexto de base de datos y los repositorios.
*   **NetBank.Infraestructure.Shared**: Proporciona servicios compartidos como el envío de correos electrónicos.
*   **NetBank.WebApp**: La capa de presentación (Frontend) implementada con ASP.NET Core MVC.

## 🚀 Características Principales

El sistema opera bajo un modelo basado en roles, ofreciendo funcionalidades específicas para cada uno:

### Panel de Administrador
*   **Dashboard Estadístico**: Visualización rápida del total de clientes, transacciones, productos y pagos activos en el sistema.
*   **Gestión de Usuarios**: Creación, edición, activación e inactivación de usuarios (clientes u otros administradores).
*   **Gestión de Productos**: 
    *   Asignación y creación de productos financieros a los clientes (Cuentas de Ahorro, Tarjetas de Crédito, Préstamos).
    *   Eliminación de productos (con validación de deudas pendientes antes de borrar).

### Panel de Cliente (Internet Banking)
*   **Resumen de Cuentas**: Vista consolidada de todos los productos del cliente al iniciar sesión, mostrando balances, límites de crédito o montos adeudados.
*   **Transferencias**: Movimiento de fondos entre cuentas de ahorro del mismo cliente.
*   **Pagos y Transacciones**:
    *   **Pago Expreso**: Transferencias directas a cuentas de terceros.
    *   **Pago a Beneficiario**: Transferencias rápidas a cuentas previamente guardadas en la libreta.
    *   **Pago de Tarjeta de Crédito**: Abonos a tarjetas descontando del balance de ahorro.
    *   **Pago de Préstamo**: Pago de cuotas de préstamos debitando de la cuenta de ahorro.
*   **Avance de Efectivo**: Transferencia de fondos desde el límite de una Tarjeta de Crédito hacia una Cuenta de Ahorro.
*   **Gestión de Beneficiarios**: Agregar, visualizar y eliminar cuentas de terceros frecuentes.

## 🛠️ Tecnologías Utilizadas

*   **Backend**: C# 10+, .NET 6/7 (ASP.NET Core MVC)
*   **Base de Datos**: Entity Framework Core
*   **Arquitectura**: Onion Architecture, Patrón Repositorio, Inyección de Dependencias
*   **Frontend**: Razor Views, Bootstrap, HTML5, CSS3

## ⚙️ Configuración y Ejecución

1.  **Clonar el repositorio**:
    ```bash
    git clone https://github.com/tu-usuario/NetBank.git
    cd NetBank/NetBank
    ```
2.  **Configurar Base de Datos**: Asegúrate de tener configurada tu cadena de conexión (Connection String) en el archivo `appsettings.json` o usando User Secrets.
3.  **Aplicar Migraciones**:
    ```bash
    dotnet ef database update --project NetBank.Infraestructure.Persistence --startup-project NetBank.WebApp
    dotnet ef database update --project NetBank.Infraestructure.Identity --startup-project NetBank.WebApp
    ```
4.  **Ejecutar el proyecto**:
    ```bash
    dotnet run --project NetBank.WebApp
    ```

### 🔑 Credenciales por Defecto (Semillas)

*   **Administrador**:
    *   Usuario: `basicAdmin`
    *   Contraseña: `321Enm#@word!`
*   **Cliente**:
    *   Usuario: `basicClient`
    *   Contraseña: `123Enm#@word!`

---
*Desarrollado para propósitos educativos y de demostración de arquitectura de software.*
