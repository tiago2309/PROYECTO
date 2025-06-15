# PROYECTO FINAL
## TopograficTool - Herramienta para Cálculos Topográficos en Ingeniería Civil
## Autores
- Santiago Ramos Barriga
- Maria Camila Palomo

Curso: Programación de Computadores  
Grupo: 404 CNF (Chill Not Found)  
Universidad Nacional de Colombia

## Problema
En la Ingeniería Civil, una de las actividades fundamentales en proyectos de obras civiles (como carreteras, redes de acueducto, edificaciones, puentes, etc.) es la topografía, que permite conocer y representar el terreno de forma precisa. Actualmente estamos cursando la asignatura de Geomática Básica dónde hemos encontrdo dificultades a la hora de hallar soluciones rapidas a los problemas dados, ya que la toma de datos se realiza muchas veces manualmente o en hojas de cálculo, lo cual consume tiempo y puede generar errores. Se necesita una herramienta por consola que automatice este proceso para estudiantes y técnicos.

## Solución
La idea de este programa es crear una herramienta por consola en Python llamada TopograficTool, que permita a los usuarios calcular coordenadas, cierres, y correcciones de poligonales (abiertas y cerradas) y radiaciones (simples y dobles), usando datos ingresados manualmente o desde archivos ".txt" o ".csv".

## ¿Cómo funcionaría?
Un estudiante está en clase de Geomática. Luego de levantar datos con el teodolito (insumo utilizado en las prácticas para medir distancias y ángulos de un terreno), debe procesarlos:
- Cargar los puntos medidos
- Calcular las coordenadas de los puntos y las distancias
- Verificar si es poligonal abierta o cerrada
- Corregir errores
- Exportar los resultados a un informe

## Diagrama preliminar

```mermaid
flowchart TD
    A[Inicio] --> B{Mostrar menu}
    B --> C1[Poligonal]
    B --> C2[Radiacion]
    B --> C3[Leer archivo]
    B --> C4[Guardar]
    B --> C5[Salir]

    C1 --> D1[Ingresar datos]
    D1 --> E1[Calcular coords]
    E1 --> F1[Verificar cierre]
    F1 --> B

    C2 --> D2[Ingresar estacion]
    D2 --> E2[Calcular coords]
    E2 --> B

    C3 --> D3[Seleccionar archivo]
    D3 --> E3[Validar datos]
    E3 --> B

    C4 --> D4[Nombre archivo]
    D4 --> E4[Guardar .txt o .csv]
    E4 --> B

    C5 --> Z[Fin]
```
