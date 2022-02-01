# Validación de documentos mexicanos

Validación de documentos emitidos por el SAT, Infonavit e IMSS:

- Cédula Identificación Fiscal
- Opinión Cumplimiento
- Opinión IMSS
- Opinión Infonavit
- Opinión REPSE
- Resumen Liquidación Bimestral
- Cédula Determinación Bimestral
- PDF de CFDI

Mas información y pruebas:
https://rapidapi.com/nekszer/api/validacion-de-documentos-sat-imss1/details


# DEFINICION DE API

BaseURL:

https://validacion-de-documentos-sat-imss1.p.rapidapi.com

| PATH                                     | METHOD       | DESCRIPCION                                            |
| ---------------------------------------- | ------------ | ------------------------------------------------------ |
| /evalidaDocumentosApi/api/documents/     | GET          | Lista los tipos de documentos validos en elsistema     | 
| /evalidaDocumentosApi/api/documents/     | POST         | Realiza la comprobacion de un documento en formato PDF |
| /evalidaDocumentosApi/api/documents/decodeData | GET    | Convierte el resultado en base64 a un objeto JSON del tipo de documento |


# EXAMPLES
## Listar los tipos de documentos que tienen validación contra el portal del SAT, IMSS o Infonavit

```
[GET] /evalidaDocumentosApi/api/documents/
```

### RESPONSE
```
[
    {
        "Id": 0,
        "Name": "Ninguno"
    },
    {
        "Id": 301,
        "Name": "Cédula Identificación Fiscal"
    },
    {
        "Id": 101,
        "Name": "Opinión Cumplimiento"
    },
    {
        "Id": 501,
        "Name": "Opinión IMSS"
    },
    {
        "Id": 401,
        "Name": "Opinión Infonavit"
    },
    {
        "Id": 601,
        "Name": "Opinión REPSE"
    },
    {
        "Id": 801,
        "Name": "Resumen Liquidación Bimestral"
    },
    {
        "Id": 701,
        "Name": "Cédula Determinación Bimestral"
    },
    {
        "Id": 201,
        "Name": "PDF de CFDI"
    }
]
```
- - -

## Subir documento PDF para validar

### REQUEST 
```
[POST] /evalidaDocumentosApi/api/documents/

[Body Form-Data] 'Ver coleccion en postman para su mayor entendimiento'
[documentId] = [101],
[file] = [archivo]
```

### RESPONSE
```
{
    "Data": "eyJSRkMiOiJCQUdNOTAwNTMxMzk5IiwiUVJVcmwiOiJodHRwczovL3NpYXQuc2F0LmdvYi5teC9hcHAvcXIvZmFjZXMvcGFnZXMvbW9iaWxlL3ZhbGlkYWRvcnFyLmpzZj9EMT0xMCZEMj0xJkQzPTE2MDEwMTAzNzI5X0JBR005MDA1MzEzOTkiLCJJc1ZhbGlkIjp0cnVlLCJOb21icmUiOiJNQU5VRUwgQUxFSkFORFJPIEJBRVogR0FSSUJBWSIsIkVzdGF0dXNQYWRyb24iOiJBQ1RJVk8iLCJGZWNoYUluaWNpb0RlT3BlcmFjaW9uZXMiOiIyMDEzLTA1LTA2VDAwOjAwOjAwIiwiRmVjaGFDYW1iaW9VbHRpbW9Fc3RhZG8iOiIyMDEzLTA1LTA2VDAwOjAwOjAwIiwiQ29ycmVvIjoicGljaG9csdiYWV6QGhvdG1haWwuY29tIiwiVGVsZWZvbm8iOiI5OTk5MjYyMjEzIiwiRGlyZWNjaW9uIjp7IkNQIjoiOTcyMDMiLCJUaXBvVmlhbGlkYWQiOiJDQUxMRSIsIk5vbWJyZVZpYWxpZGFkIjoiNDMiLCJOdW1lcm9FeHRlcmlvciI6IjM1NyIsIk51bWVyb0ludGVyaW9yIjoiIiwiTG9jYWxpZGFkIjoiRlJBQ0NJT05BTUlFTlRPIEZSQU5DSVNDTyBERSBNT05URUpPIiwiTXVuaWNpcGlvIjoiTUVSSURBIiwiRXN0YWRvIjoiWVVDQVRBTiIsIkVudHJlQ2FsbGUiOiJDQUxMRSA1MiIsIllDYWxsZSI6IkNBTExFIDU0In0sIlRlbGVmb25vTW92aWwiOiIwNDQ5OTkyOTg4NzUxIiwiQWN0aXZpZGFkZXNFY29ub21saweY2FzIjpbeyJPcmRlbiI6MSwiRGVzY3JpcGNpb24iOiJDb25zdHJ1Y2Npw7NuIGRlIGlubXVlYmxlcyB21lcmNpYWxlcywgaW5zdGl0dWNpb25hbGVzIHkgZGUgc2VydmljaW9zICIsIlBvcmNlbnRhamUiOjEwMCwiRmVjaGFGaW4iOm51bGwsIkZlY2hhSW5pY2lvIjoiMjAxNC0wMS0wMVQwMDowMDowMCJ9XSwiRmVjaGEiOiIyMDIxLTA5LTI5VDAwOjAwOjAwIn0=", // DATOS EN BASE64 del Objeto final como resultado de la validación
    "Validations": [
        {
            "Property": "RFC: XXXXXX - COINCIDE CON EL PORTAL DEL SAT",
            "Status": true, // permite saber si fue correcta la validación
            "CurrentValue": "XXXXXX", // valor del PDF
            "DesiredValue": "XXXXXX", // valor del SAT
            "Required": true, // Permite saber si es requerido este dato para la validacion
            "Key": "RFC" // clave de la validacion
        },
        {
            "Property": "Razón social: XXXXXX XX XX XX",
            "Status": true,
            "CurrentValue": "XXXXXX XX XX XX",
            "DesiredValue": "XXXXXX XX XX XX",
            "Required": false,
            "Key": "Razón social"
        },
        {
            "Property": "Fecha documento: 29-09-2021",
            "Status": false,
            "CurrentValue": 125.16917052707176, // Dias transcuridos hasta hoy
            "DesiredValue": 60, // dias requeridos
            "Required": false,
            "Key": "Fecha"
        },
        {
            "Property": "Estatus: ACTIVO", // Estado del PDF en el SAT
            "Status": true,
            "CurrentValue": "ACTIVO",
            "DesiredValue": "ACTIVO",
            "Required": true,
            "Key": "Estatus"
        }
    ]
}
```
- - -
## Obtener JSON original del documento validado

### REQUEST
```
[GET] /evalidaDocumentosApi/api/documents/decodeData?documentId=101&base64Data=DAHDHADWIHDIAJHDKSHAKDHWDKAHWD=
```

### RESPONSE
```
{
    "RFC": "XXXXXXXXXX",
    "QRUrl": "https://siat.sat.gob.mx/app/qr/faces/pages/mobile/validadorqr.jsf?D1=10&D2=1&D3=4215472377200_XXXXXXXXXX", // url del QR del documento
    "IsValid": true, // si el documento es valido contra los datos del SAT
    "Nombre": "XXXXXXXXXXXX XX XX XX",
    "EstatusPadron": "ACTIVO",
    "FechaInicioDeOperaciones": "1997-11-21T00:00:00",
    "FechaCambioUltimoEstado": null,
    "Correo": "XXXX@XXXXXX",
    "Telefono": "XXXXXXXXXX",
    "Direccion": {
        "CP": "XXXXXX",
        "TipoVialidad": "XXXXX",
        "NombreVialidad": "XXXXX",
        "NumeroExterior": "XX",
        "NumeroInterior": "X",
        "Localidad": "XX",
        "Municipio": "X",
        "Estado": "XX",
        "EntreCalle": "XXXX",
        "YCalle": "XXX"
    },
    "TelefonoMovil": "XXXXXXXXX",
    "ActividadesEconomicas": [ // en beta, podria fallar este resultado
        {
            "Orden": 1,
            "Descripcion": "Captación, tratamiento y suministro de agua para uso distinto al doméstico ",
            "Porcentaje": 100,
            "FechaFin": null,
            "FechaInicio": "2014-07-25T00:00:00"
        }
    ],
    "Fecha": "2019-10-07T00:00:00"
}
```