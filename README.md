# SD25
Proyecto de Sistemas Distribuidos | Universidad de Alicante

## Configuración

Copia el fichero `.env.example` a `.env` y establece las claves necesarias:

- `OPENWEATHER_API_KEY`: clave de la API de OpenWeather
- `OPENAI_API_KEY`: clave de OpenAI (opcional)
- `FERNET_KEY`: clave generada con `python -c "from cryptography.fernet import Fernet; print(Fernet.generate_key().decode())"`
- Parámetros `KAFKA_*` si se usa Kafka con SSL

Cada taxi recibe un token temporal al autenticarse. Este token se incluye en los
mensajes hacia la central y queda invalidado cuando el taxi regresa a la base.
