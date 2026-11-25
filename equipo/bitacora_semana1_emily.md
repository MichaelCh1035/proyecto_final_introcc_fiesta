# Semana 1 – Medición de las generaciones (Paso 7)

- Integrante: Emily Sofía Céspedes Quintero
- Usuario de GitHub: ecespedes
- Fecha: 25/11/2026
- Prueba en mi computador: Windows / CMD + Obsidian

## Qué hice

1. Exploré el problema **La fiesta** ejecutando el comando `python3 semana1/conocer.py fiesta` para revisar los 4 niveles disponibles, las restricciones de ubicación entre los invitados (quiénes se pelean y quiénes van en la cabecera o junto a la puerta) y el estado inicial del tablero vacío. 
2. Ejecuté el script de medición `python3 semana1/medir.py fiesta` para evaluar el rendimiento de las dos estrategias de búsqueda (**Generación 1 · a ciegas** y **Generación 2 · con hilo**) a través de los distintos niveles del problema.
3. Registré en una tabla los resultados obtenidos de soluciones, pasos, tropiezos y tiempo en segundos para cada nivel y generación.

**Tabla obtenida**:

| Nivel | Generación              | Soluciones | Pasos | Tropiezos | Segundos |
| ----- | ----------------------- | ---------- | ----- | --------- | -------- |
| 1     | Generacion 1 · a ciegas | 1          | 325   | 119       | 0.0      |
| 1     | Generacion 2 · con hilo | 1          | 59    | 50        | 0.0      |
| 2     | Generacion 1 · a ciegas | 1          | 1956  | 719       | 0.0      |
| 2     | Generacion 2 · con hilo | 1          | 289   | 479       | 0.0      |
| 3     | Generacion 2 · con hilo | 1          | 887   | 1354      | 0.0      |
| 4     | Generacion 2 · con hilo | 1          | 2237  | 4563      | 0.0      |
## Comandos y resultados que observé
El comando ejecutado en la terminal fue: 
```
cmd python3 semana1/medir.py fiesta
```
## Cómo interpreto el resultado
Al comparar ambas generaciones en los **niveles 1 y 2**, se observa una diferencia notable en la eficiencia de búsqueda:

- **Generación 1 · a ciegas:** Revisa las reglas al final, únicamente cuando ya ha asignado sillas a todos los invitados y tiene una configuración completa. Al no descartar errores a tiempo, explora muchas ramas inválidas del árbol de búsqueda antes de encontrar la solución. En la tabla esto se refleja en un número muy elevado de pasos (325 en el nivel 1 y 1956 en el nivel 2) y de tropiezos o retrocesos (119 en el nivel 1 y 719 en el nivel 2).

- **Generación 2 · con hilo:** Revisa las reglas de forma inmediata en cada paso, mientras va asignando cada silla. Si una asignación parcial ya viola una restricción, por ejemplo, sentar juntos a dos invitados que se pelean, detiene esa rama de inmediato y retrocede sin perder tiempo completando el resto de la mesa. En la tabla esto se refleja en una reducción drástica del trabajo:
- En el **nivel 1**, baja de 325 a 59 pasos (más de 5 veces menos) y de 119 a 50 tropiezos.
- En el **nivel 2**, baja de 1956 a 289 pasos (casi 7 veces menos) y de 719 a 479 tropiezos.
Además, esta eficiencia explica por qué en los niveles 3 y 4 el programa solo mide la Generación 2 · con hilo, ya que a medida que aumentan las restricciones y el tamaño del problema, la búsqueda a ciegas se vuelve demasiado costosa computacionalmente.

## Evidencia adjunta o dificultad encontrada

- **Resultado de ejecución:** Todos los niveles finalizaron encontrando `1` solución válida en `0.0` segundos en mi equipo.
![[evidencia-Paso 7 (Emily).png]]
- **Dificultades encontradas:** Ninguna durante la ejecución de los scripts en Python ni al registrar los datos en la bitácora.