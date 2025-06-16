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
## Diagrama preliminar para radiación simple    
Presentamos el ejemplo de solución para el caso de radiación simple, donde se ingresan las distancias, ángulos (azimut) y coordenadas de apoyo, y a partir de estos datos se calculan las proyecciones en norte y este, las coordenadas de cada punto, y finalmente el área del polígono formado. Esta área se convierte automáticamente en hectáreas y fanegadas.

La estructura y lógica aplicada en este ejemplo está pensada para extenderse fácilmente a otros métodos, como la radiación doble, la poligonal cerrada y la poligonal abierta, obviamente, cada método requiere ciertos ajustes y condiciones específicas, pero la base del procedimiento (proyecciones, coordenadas, y cálculo de áreas) se mantiene. De esta manera el diagrama de flujo que representa el proceso completo es el siguiente:    
```mermaid
flowchart TD
    A[Inicio] --> B[Ingresar datos de estación]
    B --> C[Obtener distancias, azimut y coordenadas de apoyo]
    C --> E[Proy. norte = distancia por coseno del azimut]
    C --> F[Proy. este = distancia por seno del azimut]
    E --> G[Proy. norte más coord. = norte de apoyo]
    F --> H[Proy. este más coord. = este de apoyo]
    G --> I[Guardar coord. norte del punto]
    H --> J[Guardar coord. este del punto]
    I --> K{¿Hay más puntos?}
    J --> K
    K -->|Sí| C
    K -->|No| L[Sumar N1 por E2 menos N2 por E1]
    L --> M[Dividir resultado entre 2 para hallar área]
    M --> N[Convertir área a hectáreas]
    N --> O[Guardar área en hectáreas]
    N --> P[Convertir hectáreas a fanegadas]
    P --> Q[Guardar área en fanegadas]
    Q --> R[Fin]
    O --> R

```
