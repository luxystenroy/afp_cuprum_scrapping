# API AFP Cuprum
API que obtiene el saldo total de la cuenta AFP Cuprum, realizada con Python Web Scrapping.

## Stack

 - Python 3.6
 
## Variables de entorno

| Variable      | Description | Ejemplo|
| ----------- | ----------- |----------|
| TIMEOUT      | Tiempo de espera en ejecutar la API interna de AFP Cuprum| 30 |
| PORT   | Puerdo de la aplicación |5009|


## API Request

    /cuprum/{RUT}/{PASSWORD}

| Variable      | Description | Ejemplo|
| ----------- | ----------- |----------|
| RUT      | Rut del usuario, sin puntos, con guión y digito verificador| 17123123-2 |
| PASSWORD   | Contraseña del usuario | 123123123|

## API Response
    {
        "accounts": [
            {
                "kind": "E",
                "name": "Ahorro Obligatorio",
                "price": 123123.0
            },
            {
                "kind": "E",
                "name": "Cotizaciones Voluntarias",
                "price": 123123.0
            }
        ],
        "total": 123123.0
    }

| Variable      | Description | Ejemplo|
| ----------- | ----------- |----------|
| kind      | Fondo | A,B,C,D |
| name   | Nombre o descripción | Ahorro Obligatorio|
| price   | Monto de la cuenta | 123123.0|
| total   | Monto total de las cuentas | 123123.0|



## Pruebas locales

Ejecutar la API en python

    docker build -t api-cuprum:latest .
    docker run -d -e PORT=5000 -e TIMEOUT=30  -p 5000:5000 api-cuprum:latest
Ejecutar la API

    http localhost:5000/cuprum/123123123-2/123123123
