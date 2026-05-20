# Autoload y Carga Automática con PSR-4 en PHP

## Descripción

Este proyecto consiste en una demostración práctica de la implementación de la carga automática (**Autoload**) de clases en PHP utilizando Composer bajo el estándar **PSR-4**.

El propósito del ejercicio es eliminar la necesidad de incluir archivos de clases manualmente mediante múltiples instrucciones `require` o `include`, optimizando la estructura del proyecto y profesionalizando la gestión de dependencias y espacios de nombres (*Namespaces*).

---

## Funcionamiento

El programa organiza el código en una estructura limpia de directorios, definiendo clases independientes con sus respectivos espacios de nombres.

El flujo de ejecución es el siguiente:

- Se configuran los mapeos de directorios y namespaces en el archivo `composer.json`.
- Se genera el cargador automático ejecutando comandos de Composer en la terminal.
- El archivo principal (`prueba.php`) incluye únicamente el cargador universal `vendor/autoload.php`.
- Se instancian las clases `User` y `Product`, invocando sus métodos sin importar manualmente cada archivo.

---

## Código utilizado

### 1. Configuración de Autocarga (`composer.json`)

```json
{
    "autoload": {
        "psr-4": {
            "App\\": "app/",
            "Database\\": "database/"
        }
    }
}
```

### 2. Estructura de Clases de Ejemplo

#### Clase User (`app/User.php`)

```php
<?php

namespace App;

class User {

    public function getName() {
        return "Hilda";
    }
}
```

#### Clase Product (`database/models/Product.php`)

```php
<?php

namespace Database\Models;

class Product {

    public function getId() {
        return 123;
    }
}
```

### 3. Archivo de Ejecución (`prueba.php`)

```php
<?php

// Requerir el autoload generado por Composer
require_once __DIR__ . '/vendor/autoload.php';

use App\User;
use Database\Models\Product;

// Instancia de la clase User
$user = new User();
echo "Usuario: " . $user->getName() . "<br>";

// Instancia de la clase Product
$product = new Product();
echo "Producto ID: " . $product->getId() . "<br>";

?>
```

---

## Cómo ejecutar el proyecto

1. Instalar PHP y Composer en el sistema.

2. Crear la siguiente estructura de carpetas:

```plaintext
app/
database/models/
```

3. Guardar las clases correspondientes en cada carpeta.

4. Crear el archivo `composer.json` en la raíz del proyecto.

5. Abrir una terminal en la carpeta principal del proyecto.

6. Ejecutar el siguiente comando para generar la carpeta `vendor` y el autoload:

```bash
composer install
```

Si PowerShell presenta errores, puede ejecutarse con:

```bash
cmd /c composer install
```

7. Ejecutar el archivo principal:

```bash
php prueba.php
```

---

## Ejemplo de salida

```plaintext
Usuario: hilda
Producto ID: 123
```

---

## Objetivos de aprendizaje

- Comprender el funcionamiento del concepto de **Autoload** en PHP.
- Configurar correctamente el archivo `composer.json` utilizando el estándar profesional **PSR-4**.
- Utilizar Composer para la gestión de dependencias y generación automática de clases.
- Implementar `namespace` y `use` para organizar el código y evitar colisiones de nombres.
- Mejorar la estructura y escalabilidad de proyectos PHP.

---

## Autor

Hilda Acosta
