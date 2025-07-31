# Documento de Requisitos del Producto (PRD)

## Introducción
Free Queue Manager (FQM) es un sistema de gestión de filas basado en la web. Permite organizar la atención de clientes mediante tickets impresos, pantallas de monitor y avisos por voz. Está construido con Python Flask y utiliza Bootstrap y jQuery para la interfaz.

## Objetivos
- Facilitar la administración de filas en oficinas o centros de servicio.
- Proporcionar una interfaz personalizable y multilenguaje.
- Permitir el uso de impresoras POS USB para generar tickets.
- Ofrecer avisos mediante síntesis de voz.

## Funcionalidades clave
- **Gestión de tickets**: creación, asignación y cierre de turnos.
- **Soporte multilenguaje**: traducciones definidas en `gt_cached.json` y configurables.
- **Anuncios por voz**: utilizando configuraciones en `static/tts.json`.
- **Impresión de tickets**: a través de dispositivos USB configurables.
- **Panel administrativo**: opciones de configuración y ajustes de usuarios.

## Requisitos de usuario
1. Como administrador quiero definir los servicios y mostrarlos en una pantalla para que los clientes generen su turno.
2. Como operador deseo llamar al siguiente cliente y ver su número de turno.
3. Como monitor quiero visualizar en pantalla los turnos llamados y los mensajes de texto.

## Requisitos técnicos
- Aplicación web construida con Python 3.8 o superior.
- Uso de Docker para despliegues en producción.
- Base de datos SQLite por defecto con opción futura a PostgreSQL.
- Dependencias gestionadas a través de `requirements/`.

## Consideraciones
- El sistema soporta múltiples roles de usuario (administrador, monitor y operador).
- La configuración de la impresora requiere ajustes manuales en `docker-compose.yml`.
- Para personalizar idiomas o ajustes se modifican los archivos de la carpeta `docs` y la configuración del proyecto.

