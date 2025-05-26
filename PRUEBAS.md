# Guía de pruebas para la solución del comando /evidencia

Este documento proporciona instrucciones para verificar que la solución implementada para el comando `/evidencia` funciona correctamente.

## Preparación

Antes de realizar las pruebas, asegúrate de que:

1. Has implementado correctamente la solución (reemplazando el archivo `handlers/evidencias.py`)
2. Has reiniciado el bot para que los cambios surtan efecto
3. Tienes acceso a Telegram para interactuar con el bot

## Casos de prueba

### Caso 1: Flujo completo de evidencia para una compra

1. Inicia una conversación con el bot en Telegram
2. Ejecuta el comando `/evidencia`
3. Selecciona la opción "🛒 Compras"
4. El bot mostrará una lista de compras recientes. Selecciona una de ellas
5. El bot solicitará una imagen. Envía una foto como evidencia
6. Confirma la operación seleccionando "✅ Confirmar"
7. Verifica que se muestre un mensaje de éxito con el ID de la evidencia generada

**Resultado esperado**: La evidencia se guarda correctamente y se muestra un mensaje de confirmación con los detalles.

### Caso 2: Selección múltiple de gastos

1. Ejecuta el comando `/evidencia`
2. Selecciona la opción "📊 Gastos"
3. El bot mostrará una lista de gastos con botones. Selecciona varios gastos
4. Finaliza la selección con el botón "✅ Finalizar selección"
5. Envía una imagen como evidencia
6. Confirma la operación

**Resultado esperado**: Se deben mostrar correctamente los gastos seleccionados y el monto total, y la evidencia debe guardarse con un ID compuesto.

### Caso 3: Cancelación durante el proceso

1. Ejecuta el comando `/evidencia`
2. Selecciona un tipo de operación (por ejemplo, "💰 Ventas")
3. Cuando se muestre la lista de operaciones, selecciona "❌ Cancelar"

**Resultado esperado**: El proceso debe cancelarse correctamente y el bot debe mostrar un mensaje indicando que la operación ha sido cancelada.

### Caso 4: Manejo de errores

1. Ejecuta el comando `/evidencia`
2. Selecciona un tipo de operación que no tenga registros (o si todos tienen, puedes probar con "💼 Capitalización" si es nueva)

**Resultado esperado**: El bot debe mostrar un mensaje indicando que no hay operaciones de ese tipo registradas y sugerir usar el comando correspondiente para registrar una nueva.

## Verificación en la base de datos

Después de realizar las pruebas exitosas:

1. Accede a la hoja de cálculo de Google Sheets donde se almacenan los datos
2. Verifica que las evidencias se hayan registrado correctamente en la hoja "evidencias"
3. Comprueba que los siguientes campos estén correctamente registrados:
   - ID de evidencia
   - Fecha
   - Tipo de operación
   - ID de operación
   - Monto
   - Ruta de archivo
   - Nombre de archivo
   - ID de archivo en Drive (si está habilitado)
   - Enlace al archivo en Drive (si está habilitado)
   - Descripción
   - Registrado por

## Verificación de archivos

Si tienes acceso al servidor:

1. Verifica que los archivos de imagen se hayan guardado correctamente en la carpeta correspondiente (`uploads/compras`, `uploads/ventas`, etc.)
2. Si Google Drive está habilitado, verifica que los archivos también se hayan subido a las carpetas correspondientes en Drive.

## Solución de problemas comunes

Si encuentras algún problema durante las pruebas:

1. **El bot no responde al comando**: Asegúrate de que el bot esté en funcionamiento y que hayas reiniciado correctamente después de implementar los cambios.

2. **Error al seleccionar una operación**: Verifica que las operaciones existan en la base de datos y que tengan el formato correcto.

3. **Error al subir la imagen**: Asegúrate de que las carpetas de destino tengan los permisos correctos y que haya espacio suficiente en el disco.

4. **Error al guardar en Google Sheets**: Verifica que las credenciales de Google Sheets estén configuradas correctamente y que la hoja "evidencias" exista.

5. **Error al subir a Google Drive**: Comprueba que las credenciales y los IDs de carpetas de Drive estén configurados correctamente.

Si después de revisar estos puntos sigues teniendo problemas, consulta los logs del bot para obtener información más detallada sobre el error y contacta al administrador del sistema.
