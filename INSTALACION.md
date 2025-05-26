# Instrucciones de instalación

Este documento detalla los pasos para implementar la corrección del comando `/evidencia` en el bot de Telegram para gestión de café.

## Opción 1: Actualizar el archivo directamente

Esta es la forma más rápida de implementar la solución.

1. Accede al servidor donde se ejecuta tu bot de Telegram
2. Localiza el directorio del proyecto `cafe-bot-telegram`
3. Haz una copia de seguridad del archivo original:
   ```bash
   cp handlers/evidencias.py handlers/evidencias.py.backup
   ```
4. Descarga el nuevo archivo de este repositorio:
   ```bash
   wget -O handlers/evidencias.py https://raw.githubusercontent.com/sofiaqsy/cafe-bot-telegram-fork-fix/main/handlers/evidencias.py
   ```
5. Reinicia el bot para que los cambios surtan efecto:
   ```bash
   # Si estás usando systemd:
   sudo systemctl restart cafe-bot.service
   
   # O si estás ejecutando manualmente:
   pkill -f bot.py
   python bot.py &
   ```

## Opción 2: Crear un Pull Request

Si prefieres seguir un enfoque más formal y mantener un historial completo de cambios:

1. Haz un fork del repositorio original `cafe-bot-telegram`
2. Clona tu fork localmente:
   ```bash
   git clone https://github.com/TU_USUARIO/cafe-bot-telegram.git
   cd cafe-bot-telegram
   ```
3. Crea una nueva rama para los cambios:
   ```bash
   git checkout -b fix-evidencia-command
   ```
4. Descarga y reemplaza el archivo evidencias.py:
   ```bash
   wget -O handlers/evidencias.py https://raw.githubusercontent.com/sofiaqsy/cafe-bot-telegram-fork-fix/main/handlers/evidencias.py
   ```
5. Realiza un commit de los cambios:
   ```bash
   git add handlers/evidencias.py
   git commit -m "Fix: Implementar funcionalidades faltantes en el comando /evidencia"
   ```
6. Empuja los cambios a tu fork:
   ```bash
   git push origin fix-evidencia-command
   ```
7. Crea un Pull Request desde la interfaz web de GitHub para que los cambios sean revisados e integrados en el repositorio principal.

## Verificación

Después de implementar los cambios, verifica que el comando `/evidencia` funciona correctamente:

1. Inicia una conversación con el bot
2. Ejecuta el comando `/evidencia`
3. Selecciona un tipo de operación (compra, venta, etc.)
4. Selecciona una operación específica
5. Sube una imagen como evidencia
6. Confirma la operación

El proceso debería completarse sin errores y la evidencia debería quedar registrada correctamente.

## Solución de problemas

Si encuentras algún problema después de la implementación:

1. **Verifica los logs del bot** para identificar errores específicos:
   ```bash
   # Si estás usando un archivo de log:
   tail -f logs/bot.log
   
   # O en la salida estándar si estás ejecutando manualmente:
   journalctl -u cafe-bot.service -f
   ```

2. **Comprueba las dependencias**: Asegúrate de que todas las dependencias necesarias están instaladas:
   ```bash
   pip install -r requirements.txt
   ```

3. **Reinstala desde cero**: Si los problemas persisten, considera reinstalar el bot desde cero utilizando la versión corregida.

4. **Contacta con soporte**: Si necesitas ayuda adicional, abre un issue en el repositorio del fix o contacta directamente con el mantenedor.