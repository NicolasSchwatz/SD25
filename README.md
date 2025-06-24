# SD25
Proyecto de Sistemas Distribuidos | Universidad de Alicante

## Configuración

Copia el fichero `.env.example` a `.env` y establece las claves necesarias:

- `OPENWEATHER_API_KEY`: clave de la API de OpenWeather
- `OPENAI_API_KEY`: clave de OpenAI (opcional)
- `FERNET_KEY`: clave generada con `python -c "from cryptography.fernet import Fernet; print(Fernet.generate_key().decode())"`
- Parámetros `KAFKA_*` si se usa Kafka con SSL

Si `OPENAI_API_KEY` está definido, el módulo EC_CTC consultará a ChatGPT para
determinar el estado del tráfico a partir de la temperatura obtenida de
OpenWeather.

Cada taxi recibe un token temporal al autenticarse. Este token se incluye en los
mensajes hacia la central y queda invalidado cuando el taxi regresa a la base.

La Central genera un fichero `LOGS/audit.log` con los eventos de autenticación y
comandos. Puede consultarse a través del endpoint `/get_audit_logs` o desde la
página `/audit` que refresca la información periódicamente.
