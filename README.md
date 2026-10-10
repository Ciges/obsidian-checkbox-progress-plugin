# Checkbox Progress

Repositorio original: https://github.com/WallaceWyslas/obsidian-checkbox-progress

Plugin de Obsidian de Wallace Wyslas que muestra el progreso de las casillas de tarea de la nota activa: una barra y un contador `completadas/total (%)` en la barra de estado (escritorio) o en la cabecera de la nota (móvil), con un botón para resetear todas las casillas y otro para saltar a la siguiente casilla sin marcar. Ignora el frontmatter y los bloques de código.

Versión original: **1.0.0**. Es un fork de los ficheros compilados (no del código fuente), así que `main.js` está editado a mano. No se debe sobrescribir `main.js` al reinstalar o actualizar el plugin sin revisar antes estos cambios (están marcados con `// Fork Ciges`).

## Modificaciones

Adaptación a todos los estados de tarea del plugin Tasks (` `, `/`, `p`, `x`, `c`, `-`, `>`, `d`; ver el README principal del vault):

1. **Reseteo de casillas:** el botón y el comando "Reset all checkboxes in current note" ahora ponen en ` ` todos los estados distintos de ` ` (`/`, `p`, `x`, `X`, `c`, `-`, `>` y `d`). Antes solo reseteaban `x`, `X`, `-` y `/`.
2. **Contador de progreso:** ahora se reconocen todos los estados al contar. Cuentan como completadas `p`, `x`, `X`, `c`, `-` y `d`. Las casillas `/` (en curso) y `>` (delegada) cuentan en el total pero como pendientes (antes `/` contaba como completada, y `p`, `c`, `d` y `>` no se contaban).

No se ha modificado "Go to next unchecked checkbox", que sigue buscando solo `[ ]`.
