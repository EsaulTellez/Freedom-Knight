# Matriz Inicial de Pruebas - Freedom Knight

Esta matriz documenta los casos de prueba ejecutados sobre el proyecto para verificar estabilidad, comportamiento en casos límite y la integración de la nueva característica.

## Casos de Prueba

| ID | Caso de Prueba | Categoría | Dispositivo / Entorno | Pasos de Ejecución | Resultado Esperado | Resultado Real | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-01** | Movimiento y Ataque Principal | Flujo Principal | macOS / Godot 4.x | 1. Iniciar juego.<br>2. Presionar teclas A/D (movimiento).<br>3. Presionar botón de ataque. | El personaje se desplaza fluidamente y ejecuta la animación de ataque sin trabas. | Movimiento y ataque fluidos; animaciones sincronizadas con el hitbox. | **PASÓ** |
| **TC-02** | Entrada de Datos / Teclas No Asignadas | Datos Inválidos | macOS / Godot 4.x | 1. Iniciar juego.<br>2. Presionar teclas no mapeadas en InputMap (ej. J, K, L). | El motor ignora las entradas no registradas sin generar excepciones ni congelamientos. | No se generaron errores en consola; el juego responde solo a entradas válidas. | **PASÓ** |
| **TC-03** | Pausa y Reanudación de Escena | Recreación / Ciclo de Vida | macOS / Godot 4.x | 1. Durante la partida, presionar tecla de pausa (`MenuPausa.gd`).<br>2. Seleccionar Reanudar/Reiniciar. | El árbol de escenas detiene el procesamiento en pausa y se reanuda correctamente. | El árbol se congela adecuadamente y se recupera el control al despausar. | **PASÓ** |
| **TC-04** | Modo Solitario / Red No Disponible | Red y Conectividad | macOS / Godot 4.x | 1. Iniciar juego en modo local/arcade sin servidor multijugador activo. | El juego opera localmente omitiendo llamadas RPC sin crashear. | Funciona en solitario; `NetworkManager` maneja adecuadamente la ausencia de pares. | **PASÓ** |
| **TC-05** | Agotamiento de Vidas y Game Over | Estado Alterno / Feature | macOS / Godot 4.x | 1. Permitir que el caballero reciba daño continuo hasta perder todas sus vidas. | Se decrementan las vidas; al llegar a 0 vidas se activa el estado Game Over y se desactiva el control. | Se activa la pantalla de Game Over y se impide el movimiento del personaje. | **PASÓ** |
