# AudioAlchemy

El siguiente proyecto consiste en un encargo realizado por la compañía de venta online [El Ártico Discos](https://www.discogs.com/es/seller/elarticodiscos/profile "El Ártico Discos"). ![profile](https://github.com/jvr0/AudioAlchemy/blob/main/images/profile.jpg) Se ha propuesto un trabajo de ingeniería para la actualización automática del inventario. El objetivo es mejorar la ubicación de los items dentro de la plataforma [Discogs](https://www.discogs.com/es/ "Discogs").

**Índice**
1. [Funcionalidad en la API](#funcionalidad)
2. [Creación del entorno gráfico](#grafico)
3. [Creación del pipeline](#pipeline)
4. [Producción en AWS](#aws)

#### 1. Funcionalidad en la API <a name="funcionalidad"></a>

- autentificación de auth
- testeo con pruebas pequeñas
- lanzamiento de grandes paquetes

<details>
<summary>Función Items</summary>
<br>

```python
def lanzamiento ():

        url = 'https://api.discogs.com/inventory/upload/change' # url para actualización

        csv_file_path = '../data/upload.csv' # camino hacía los datos

        files = {'upload': ('upload.csv', open(csv_file_path, 'rb'), 'text/csv')} # apertura para lanzamiento

        res = req.post(url, auth=oauth, files=files) # envió a la API

        if res.status_code == 200:
            print('Successful update', res.status_code)
            print(res.headers['X-Discogs-Ratelimit-Remaining'])
    
        else:
            print('Something is wrong', res.status_code)
```
</details>

#### 2. Creación de entorno gráfico <a name="grafico"></a>

- entorno gráfico en streamlit para entregar a cliente
- decoración y colores

#### 3. Creación del pipeline <a name="pipeline"></a>

- establecer pipeline que permita conectar el entorno gráfico de streamlit con el src hospedado en el ordenador personal

#### 4. Producción en AWS <a name="aws"></a>

- enviar el src a AWS y conectarlo con el streamlit. todo de forma remota en la nube. De esta forma se establece un programa siempre activo que permité la continua iteración de los elementos del inventario en pequeños paquetes (cuentagotas)


# next step hard: creación de un entorno que permita la ejecución de todo a través de un solo botón. Este entorno permitirá la configuración de los parámetros deseados a través del entorno gráfico.