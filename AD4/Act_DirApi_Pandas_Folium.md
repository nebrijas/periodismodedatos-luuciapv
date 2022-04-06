# API Pandas Folium

- API
- Pandas
- Folium,mapas

## Instalar librerías

El primer paso a realizar es instalar la librería Panda. Esto otorga herramientas que permiten leer y escribir datos en diferentes formatoscomo CSV, Microsoft Excel, bases SQL y formato HDF5. Además, esta herramienta da la opción de seleccionar y filtrar fácilmnete las tablas de datos en función de la posición, el valor o las propias etiquetas, así como fusionar y unir datos.


```python
!pip install pandas folium
```

    Requirement already satisfied: pandas in c:\programdata\anaconda3\lib\site-packages (1.2.4)
    Requirement already satisfied: folium in c:\programdata\anaconda3\lib\site-packages (0.12.1.post1)
    Requirement already satisfied: branca>=0.3.0 in c:\programdata\anaconda3\lib\site-packages (from folium) (0.4.2)
    Requirement already satisfied: numpy in c:\programdata\anaconda3\lib\site-packages (from folium) (1.20.1)
    Requirement already satisfied: requests in c:\programdata\anaconda3\lib\site-packages (from folium) (2.25.1)
    Requirement already satisfied: jinja2>=2.9 in c:\programdata\anaconda3\lib\site-packages (from folium) (2.11.3)
    Requirement already satisfied: MarkupSafe>=0.23 in c:\programdata\anaconda3\lib\site-packages (from jinja2>=2.9->folium) (1.1.1)
    Requirement already satisfied: python-dateutil>=2.7.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2.8.1)
    Requirement already satisfied: pytz>=2017.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2021.1)
    Requirement already satisfied: six>=1.5 in c:\programdata\anaconda3\lib\site-packages (from python-dateutil>=2.7.3->pandas) (1.15.0)
    Requirement already satisfied: urllib3<1.27,>=1.21.1 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (1.26.4)
    Requirement already satisfied: idna<3,>=2.5 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2.10)
    Requirement already satisfied: certifi>=2017.4.17 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2020.12.5)
    Requirement already satisfied: chardet<5,>=3.0.2 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (4.0.0)
    

## Configurar librerías

La configuración de las librerías se basa en importarlas para utilizarlas en este notebook. Se consigue a través de estas funciones:


```python
import pandas as pd
import folium
```

## Variables

Las variables que vamos a utilizar son estas:
- La URL
- Las coordenadas de la ciudad escigida, en este caso Zaragoza, que llamaremos `coords_zrgz` y cuyas coordenadas exactas son `[41.649693, -0.887712]`
- El mapa, que es una variable considerada también un objeto. Lo haremos haciendo una llamada a `folium`

La primera variable que vamos a usar es la URL de donde queremos exportar los datos, en este caso la accidentalidad en el tráfico en la ciudad de Zaragoza. 

Para hacer el mapa llamaremos a la libreria folium, a la que le pediremos la localización y cuyo valor serán las coordenadas de Zaragoza, aquí llamadas `coords_zrgz`


```python
url = 'https://www.zaragoza.es/sede/servicio/transporte/accidentalidad-trafico/accidente.csv?rows=20'
coords_zrgz = [41.649693,-0.887712]
mapa = folium.Map(location=coords_zrgz)
```

Ahora tenemos que colocar al mapa. Se escribe el término `mapa`, ya que es la palabra elegida para dar valor de las coordenadas de Zaragoza.


```python
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_945d50150c4748958778ffb9163f18fb%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_945d50150c4748958778ffb9163f18fb%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_945d50150c4748958778ffb9163f18fb%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_945d50150c4748958778ffb9163f18fb%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_928aa7c6db974125a91930fdcfcfbcbb%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_945d50150c4748958778ffb9163f18fb%29%3B%0A%20%20%20%20%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



Creamos un data frame `df`, que es como llama Python a las tablas. Sin embargo, tenemos que delimitar el link con el código `delimiter`, que en este caso es el punto y coma `;`. Así le comunidcamos a la librería que lea la función de Panda `read csv`, pero como no delimitamos mediante comas `,`, sino por puntos y comas `;`, se lo tenemos que decir para que muestre bien los datos.


```python
df = pd.read_csv(url,delimiter=';')
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>year</th>
      <th>type</th>
      <th>accidentType</th>
      <th>firstAddress</th>
      <th>secondAddress</th>
      <th>geometry</th>
      <th>reason</th>
      <th>area</th>
      <th>creationDate</th>
      <th>daniosMateriales</th>
      <th>falloMecanico</th>
      <th>estadoPavimento</th>
      <th>tipoEstadoPavimento</th>
      <th>estadoAtmosfera</th>
      <th>tipoEstadoAtmosfera</th>
      <th>afectado</th>
      <th>vehiculo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>COSTA, JOAQUIN</td>
      <td>PERAL, ISAAC</td>
      <td>-0.8818527060979306,41.649027473051156</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2014-10-09T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CADENA(MARQUES DE LA)</td>
      <td>NaN</td>
      <td>-0.8645810716721081,41.661585829868585</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>2560.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>GOMEZ AVELLANEDA, G.</td>
      <td>CASTRO, R. (POETA)</td>
      <td>-0.887776415002892,41.666992622958105</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2598.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS FRONTOLATERAL</td>
      <td>NaN</td>
      <td>MONZON</td>
      <td>GARCIA CONDOY, H.</td>
      <td>-0.8825260453930127,41.62957498750602</td>
      <td>CEDA EL PASO, no respetar prioridad de paso</td>
      <td>2555.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NAVARRA, AVENIDA DE</td>
      <td>-0.908314757720389,41.6562121210704</td>
      <td>PERDIDA del control por VELOCIDAD INADECUADA</td>
      <td>2554.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>5</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>MUEL</td>
      <td>NaN</td>
      <td>-0.8691088511672924,41.65949772773082</td>
      <td>Caída de ocupante en Transporte Público</td>
      <td>2578.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>6</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>PIGNATELLI, RAMON VIA</td>
      <td>NaN</td>
      <td>-0.8880337913721866,41.633353667694024</td>
      <td>PEATÓN cruza calz SIN PREFER. fuera de paso</td>
      <td>2606.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>7</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>CAIDA SOBRE CALZADA</td>
      <td>NaN</td>
      <td>ALIERTA, AV. CESAREO</td>
      <td>AULA, LUIS</td>
      <td>-0.8708838775078237,41.6390382112928</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>2583.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>8</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>NaN</td>
      <td>CERBUNA, PEDRO</td>
      <td>NaN</td>
      <td>-0.8970649943808023,41.64083344974765</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2556.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>9</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>ASALTO</td>
      <td>COCCI, JORGE</td>
      <td>-0.8718525605769747,41.64904657717317</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>4657.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>10</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>ARAGON (CORONA DE)</td>
      <td>SAN ANTONIO M CLARET</td>
      <td>-0.8964627561577849,41.64322365075108</td>
      <td>Caída de ocupante en Transporte Público</td>
      <td>63.0</td>
      <td>2013-12-21T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>11</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>FRAGUA, LA</td>
      <td>GASSIER, PIERRE</td>
      <td>-0.8778095796207178,41.68753087470739</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4780.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>12</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>PIRINEOS, AV. DE LOS</td>
      <td>NaN</td>
      <td>-0.8812157329722801,41.661646612715046</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4661.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>13</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>TORRES, CAMINO DE LAS</td>
      <td>NaN</td>
      <td>-0.8762000299022707,41.6454384961757</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4667.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>14</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NAVARRA, AVENIDA DE</td>
      <td>-0.9089013552408617,41.65543768899759</td>
      <td>PEATÓN cruza calz SIN PREFER. en PASO CON semá...</td>
      <td>4664.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>15</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>ITALIA</td>
      <td>NaN</td>
      <td>-0.9004729973337304,41.65180346604993</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4671.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>16</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>AGUSTIN, PASEO MARIA</td>
      <td>MAYANDIA (GENERAL)</td>
      <td>-0.8917562993466011,41.65233828238132</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>18.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>17</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>AGUSTIN, PASEO MARIA</td>
      <td>SANTA ANA</td>
      <td>-0.888856043735591,41.65040494617356</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4718.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>18</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CASPE, AV.COMPROMISO</td>
      <td>NaN</td>
      <td>-0.8629911318784169,41.645335650478316</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4723.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>19</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>MURANO, ISLA DE AV.</td>
      <td>NaN</td>
      <td>-0.8870207060655807,41.609992514227066</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
  </tbody>
</table>
</div>



## Exploración de la tabla

Ahora vamos a ver cuales son los nombres de las columnas:


```python
df.columns
```




    Index(['id', 'year', 'type', 'accidentType', 'firstAddress', 'secondAddress',
           'geometry', 'reason', 'area', 'creationDate', 'daniosMateriales',
           'falloMecanico', 'estadoPavimento', 'tipoEstadoPavimento',
           'estadoAtmosfera', 'tipoEstadoAtmosfera', 'afectado', 'vehiculo'],
          dtype='object')



Para que nos enseñe la geometría, lo hacemos con la misma función vista arriba, qué categorías son a las que podemos acceder. También podemos  a otras como `year`, `creationDate` o `tipoEstadoAtmosfera`, entre más opciones.


```python
df['geometry']
```




    0     -0.8818527060979306,41.649027473051156
    1     -0.8645810716721081,41.661585829868585
    2      -0.887776415002892,41.666992622958105
    3      -0.8825260453930127,41.62957498750602
    4        -0.908314757720389,41.6562121210704
    5      -0.8691088511672924,41.65949772773082
    6     -0.8880337913721866,41.633353667694024
    7       -0.8708838775078237,41.6390382112928
    8      -0.8970649943808023,41.64083344974765
    9      -0.8718525605769747,41.64904657717317
    10     -0.8964627561577849,41.64322365075108
    11     -0.8778095796207178,41.68753087470739
    12    -0.8812157329722801,41.661646612715046
    13      -0.8762000299022707,41.6454384961757
    14     -0.9089013552408617,41.65543768899759
    15     -0.9004729973337304,41.65180346604993
    16     -0.8917562993466011,41.65233828238132
    17      -0.888856043735591,41.65040494617356
    18    -0.8629911318784169,41.645335650478316
    19    -0.8870207060655807,41.609992514227066
    Name: geometry, dtype: object




```python
df.info ()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 20 entries, 0 to 19
    Data columns (total 18 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   id                   20 non-null     object 
     1   year                 20 non-null     int64  
     2   type                 20 non-null     object 
     3   accidentType         0 non-null      float64
     4   firstAddress         20 non-null     object 
     5   secondAddress        11 non-null     object 
     6   geometry             20 non-null     object 
     7   reason               20 non-null     object 
     8   area                 18 non-null     float64
     9   creationDate         20 non-null     object 
     10  daniosMateriales     20 non-null     bool   
     11  falloMecanico        20 non-null     bool   
     12  estadoPavimento      20 non-null     object 
     13  tipoEstadoPavimento  0 non-null      float64
     14  estadoAtmosfera      20 non-null     object 
     15  tipoEstadoAtmosfera  0 non-null      float64
     16  afectado             15 non-null     object 
     17  vehiculo             20 non-null     object 
    dtypes: bool(2), float64(4), int64(1), object(11)
    memory usage: 2.7+ KB
    

A info le añadimos unos parénteisis porque es una función. Para ver los tipo de datos que tiene el dataframe que viene de la URL de la api de Zaragoza. El object es un texto natural, es decir, un accidente por ejemplo, allí donde hay texto. Es un texto que hace referencia a algo.
Ahora hacemos la función describe. Nos sive porque nos da información sobre la columnas númericas, en este caso son años.


```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>accidentType</th>
      <th>area</th>
      <th>tipoEstadoPavimento</th>
      <th>tipoEstadoAtmosfera</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>20.000000</td>
      <td>0.0</td>
      <td>18.000000</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2013.450000</td>
      <td>NaN</td>
      <td>3234.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.510418</td>
      <td>NaN</td>
      <td>1551.515843</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>18.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>2557.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>2602.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2014.000000</td>
      <td>NaN</td>
      <td>4666.250000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2014.000000</td>
      <td>NaN</td>
      <td>4780.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



La próxima opción es type que es una columna que la encadeno a la descripción de los valores únicos: salida, alcance, calzada o colisión frontal. Así se ven las valores de la columna type, qué valores únicos hay.


```python
df['type'].unique()
```




    array(['SALIDA CALZADA', 'COLISIÓN ALCANCE', 'COLIS FRONTOLATERAL',
           'OTRAS', 'ATROPELLO', 'CAIDA SOBRE CALZADA', 'COLIS. MARCHA ATRÁS',
           'COLISIÓN LATERAL'], dtype=object)



Me voy a geometry de la misma forma que he accedido a type. Lo que aparece son filas con números de principio a fin. En la columna geometry selecciono una opción en concreto y lo encapsulo. Hay que acceder a la fila 0 mediante la función `type` que dice qué tipo de datos es. Lo que leo es un string, una línea de caracteres.


```python
df['geometry']
```




    0     -0.8818527060979306,41.649027473051156
    1     -0.8645810716721081,41.661585829868585
    2      -0.887776415002892,41.666992622958105
    3      -0.8825260453930127,41.62957498750602
    4        -0.908314757720389,41.6562121210704
    5      -0.8691088511672924,41.65949772773082
    6     -0.8880337913721866,41.633353667694024
    7       -0.8708838775078237,41.6390382112928
    8      -0.8970649943808023,41.64083344974765
    9      -0.8718525605769747,41.64904657717317
    10     -0.8964627561577849,41.64322365075108
    11     -0.8778095796207178,41.68753087470739
    12    -0.8812157329722801,41.661646612715046
    13      -0.8762000299022707,41.6454384961757
    14     -0.9089013552408617,41.65543768899759
    15     -0.9004729973337304,41.65180346604993
    16     -0.8917562993466011,41.65233828238132
    17      -0.888856043735591,41.65040494617356
    18    -0.8629911318784169,41.645335650478316
    19    -0.8870207060655807,41.609992514227066
    Name: geometry, dtype: object




```python
type(df['geometry'][0])
```




    str



Esta cadena de caracteres la tenemos que separar a través de una coma , separamos los datos de la izquierda y la derecha. Las separamos con la función split y el separador se entrecomilla.


```python
df['geometry'][0].split(',')
```




    ['-0.8818527060979306', '41.649027473051156']



Se ha creado una lista que se puede comenzar a manipular. He creado una tabla nueva con una sola fila. Creamos un punto llamado `point` igual a lo realizado anteriormente, es decir, mirar a la celda de la columna geometría. La dividimos con la coma, el resultado es el mismo, hemos credao un objeto nuevo que crea los datos de esa columna y hace la división que es una cadena de caracteres.


```python
point = df['geometry'][0].split(',')
point
```




    ['-0.8818527060979306', '41.649027473051156']



Con la siguiente función, `point`es ahora una lista de dos elementos


```python
type(point)
```




    list



Creamos una serie que la denominamos `longitudes` para guardar elementos. Tambiém creamos `latitudes`, son dos listas sin datos


```python
longitudes = []
latitudes = []
```


```python
longitudes
```




    []




```python
type(longitudes)
```




    list



For es un elemento input, llamamos a cualquier elemento que hace el bucle. Lo denominamos`for i`. Para cada uno de los elementos del dataframe geometry voy a hacer un split para separar. Para cada una de las filas, la i, hace una separación.
Hacemos un for, un bucle, para cada uno de los elementos de la tabla de datos, solo lo aplicamos a los elementos de la columna `geometry`. Vamos a llamar al punto de coordenadas la separación entre las celdas de punto geometry. Añadimos al objeto longitudes el segundo valor de punto coordenadas.


```python
for i in df['geometry']:
    punto_coord = i.split(',')
    longitudes += [float(punto_coord[1])]
longitudes
```




    [41.649027473051156,
     41.661585829868585,
     41.666992622958105,
     41.62957498750602,
     41.6562121210704,
     41.65949772773082,
     41.633353667694024,
     41.6390382112928,
     41.64083344974765,
     41.64904657717317,
     41.64322365075108,
     41.68753087470739,
     41.661646612715046,
     41.6454384961757,
     41.65543768899759,
     41.65180346604993,
     41.65233828238132,
     41.65040494617356,
     41.645335650478316,
     41.609992514227066]



Seguimos el mismo procedimeinto con `latitudes`


```python
for i in df['geometry']:
    punto_coord = i.split(',')
    latitudes += [float(punto_coord[0])]
latitudes
```




    [-0.8818527060979306,
     -0.8645810716721081,
     -0.887776415002892,
     -0.8825260453930127,
     -0.908314757720389,
     -0.8691088511672924,
     -0.8880337913721866,
     -0.8708838775078237,
     -0.8970649943808023,
     -0.8718525605769747,
     -0.8964627561577849,
     -0.8778095796207178,
     -0.8812157329722801,
     -0.8762000299022707,
     -0.9089013552408617,
     -0.9004729973337304,
     -0.8917562993466011,
     -0.888856043735591,
     -0.8629911318784169,
     -0.8870207060655807]



Ahora realizamos un dataframe de las coordenadas de las dos columnas, longitudes y latitudes


```python
df_coord = pd.DataFrame({'long':longitudes,'lat':latitudes})
df_coord
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>41.649027</td>
      <td>-0.881853</td>
    </tr>
    <tr>
      <th>1</th>
      <td>41.661586</td>
      <td>-0.864581</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41.666993</td>
      <td>-0.887776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41.629575</td>
      <td>-0.882526</td>
    </tr>
    <tr>
      <th>4</th>
      <td>41.656212</td>
      <td>-0.908315</td>
    </tr>
    <tr>
      <th>5</th>
      <td>41.659498</td>
      <td>-0.869109</td>
    </tr>
    <tr>
      <th>6</th>
      <td>41.633354</td>
      <td>-0.888034</td>
    </tr>
    <tr>
      <th>7</th>
      <td>41.639038</td>
      <td>-0.870884</td>
    </tr>
    <tr>
      <th>8</th>
      <td>41.640833</td>
      <td>-0.897065</td>
    </tr>
    <tr>
      <th>9</th>
      <td>41.649047</td>
      <td>-0.871853</td>
    </tr>
    <tr>
      <th>10</th>
      <td>41.643224</td>
      <td>-0.896463</td>
    </tr>
    <tr>
      <th>11</th>
      <td>41.687531</td>
      <td>-0.877810</td>
    </tr>
    <tr>
      <th>12</th>
      <td>41.661647</td>
      <td>-0.881216</td>
    </tr>
    <tr>
      <th>13</th>
      <td>41.645438</td>
      <td>-0.876200</td>
    </tr>
    <tr>
      <th>14</th>
      <td>41.655438</td>
      <td>-0.908901</td>
    </tr>
    <tr>
      <th>15</th>
      <td>41.651803</td>
      <td>-0.900473</td>
    </tr>
    <tr>
      <th>16</th>
      <td>41.652338</td>
      <td>-0.891756</td>
    </tr>
    <tr>
      <th>17</th>
      <td>41.650405</td>
      <td>-0.888856</td>
    </tr>
    <tr>
      <th>18</th>
      <td>41.645336</td>
      <td>-0.862991</td>
    </tr>
    <tr>
      <th>19</th>
      <td>41.609993</td>
      <td>-0.887021</td>
    </tr>
  </tbody>
</table>
</div>



Creamos otro dataframe denominado `accidentes`que va aconcotenar el dataframe primero con el creado de coordenadas. 


```python
df_accidentes = pd.concat([df['type'],df_coord],axis=1)
df_accidentes
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SALIDA CALZADA</td>
      <td>41.649027</td>
      <td>-0.881853</td>
    </tr>
    <tr>
      <th>1</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.661586</td>
      <td>-0.864581</td>
    </tr>
    <tr>
      <th>2</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.666993</td>
      <td>-0.887776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>COLIS FRONTOLATERAL</td>
      <td>41.629575</td>
      <td>-0.882526</td>
    </tr>
    <tr>
      <th>4</th>
      <td>SALIDA CALZADA</td>
      <td>41.656212</td>
      <td>-0.908315</td>
    </tr>
    <tr>
      <th>5</th>
      <td>OTRAS</td>
      <td>41.659498</td>
      <td>-0.869109</td>
    </tr>
    <tr>
      <th>6</th>
      <td>ATROPELLO</td>
      <td>41.633354</td>
      <td>-0.888034</td>
    </tr>
    <tr>
      <th>7</th>
      <td>CAIDA SOBRE CALZADA</td>
      <td>41.639038</td>
      <td>-0.870884</td>
    </tr>
    <tr>
      <th>8</th>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>41.640833</td>
      <td>-0.897065</td>
    </tr>
    <tr>
      <th>9</th>
      <td>COLISIÓN LATERAL</td>
      <td>41.649047</td>
      <td>-0.871853</td>
    </tr>
    <tr>
      <th>10</th>
      <td>OTRAS</td>
      <td>41.643224</td>
      <td>-0.896463</td>
    </tr>
    <tr>
      <th>11</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.687531</td>
      <td>-0.877810</td>
    </tr>
    <tr>
      <th>12</th>
      <td>SALIDA CALZADA</td>
      <td>41.661647</td>
      <td>-0.881216</td>
    </tr>
    <tr>
      <th>13</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.645438</td>
      <td>-0.876200</td>
    </tr>
    <tr>
      <th>14</th>
      <td>ATROPELLO</td>
      <td>41.655438</td>
      <td>-0.908901</td>
    </tr>
    <tr>
      <th>15</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.651803</td>
      <td>-0.900473</td>
    </tr>
    <tr>
      <th>16</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.652338</td>
      <td>-0.891756</td>
    </tr>
    <tr>
      <th>17</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.650405</td>
      <td>-0.888856</td>
    </tr>
    <tr>
      <th>18</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.645336</td>
      <td>-0.862991</td>
    </tr>
    <tr>
      <th>19</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.609993</td>
      <td>-0.887021</td>
    </tr>
  </tbody>
</table>
</div>



El siguiente pasio es cerar un marcador para que aparezca un punto en el apa con la función de folium que se llama marker. Va atener las coordenadas de Zaragoza y en el pop up, la información  que salga cuando pinche, saldrá Zaragoza. Le tenemos que decir al mapa que añada el marcador, y luego que muestre el mapa.


```python
marcador = folium.Marker(coords_zrgz, popup="¡Hola, Zaragoza!")
mapa = mapa.add_child(marcador)
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_945d50150c4748958778ffb9163f18fb%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_945d50150c4748958778ffb9163f18fb%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_945d50150c4748958778ffb9163f18fb%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_945d50150c4748958778ffb9163f18fb%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_928aa7c6db974125a91930fdcfcfbcbb%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_945d50150c4748958778ffb9163f18fb%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_06c06b393eea410688e963ec37a0e21e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_945d50150c4748958778ffb9163f18fb%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a4b86fba2e08415cb1015fbc9266fc8b%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_36be7690c701436f9d6747f4a9426087%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_36be7690c701436f9d6747f4a9426087%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3E%C2%A1Hola%2C%20Zaragoza%21%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a4b86fba2e08415cb1015fbc9266fc8b.setContent%28html_36be7690c701436f9d6747f4a9426087%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_06c06b393eea410688e963ec37a0e21e.bindPopup%28popup_a4b86fba2e08415cb1015fbc9266fc8b%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



Vamos a hacer un mapa con todos los puntos que tiene nuestra tabla. La función `iterrows` signifca marca todo por cada fila.


```python
!pip install pandas folium
import pandas as pd
import folium
url = 'https://www.zaragoza.es/sede/servicio/transporte/accidentalidad-trafico/accidente.csv?rows=20'
coord = [41.64,-0.88]
mapa = folium.Map(location=coord)
df = pd.read_csv(url,delimiter=';')
longitudes = []
for i in df['geometry']:
    longlat = i.split(',')
    longitudes += [float(longlat[0])]
latitudes = []
for i in df['geometry']:
    longlat = i.split(',')
    latitudes += [float(longlat[1])]
df_coord = pd.DataFrame({'long':longitudes, 'lat': latitudes})
df_tipo = pd.concat([df['type'],df_coord], axis=1)
for index, fila in df_tipo.iterrows():
    marcador = folium.Marker([fila['lat'],fila['long']],popup=fila['type'])
    mapa.add_child(marcador)
mapa
    
```

    Requirement already satisfied: pandas in c:\programdata\anaconda3\lib\site-packages (1.2.4)
    Requirement already satisfied: folium in c:\programdata\anaconda3\lib\site-packages (0.12.1.post1)
    Requirement already satisfied: requests in c:\programdata\anaconda3\lib\site-packages (from folium) (2.25.1)
    Requirement already satisfied: jinja2>=2.9 in c:\programdata\anaconda3\lib\site-packages (from folium) (2.11.3)
    Requirement already satisfied: numpy in c:\programdata\anaconda3\lib\site-packages (from folium) (1.20.1)
    Requirement already satisfied: branca>=0.3.0 in c:\programdata\anaconda3\lib\site-packages (from folium) (0.4.2)
    Requirement already satisfied: MarkupSafe>=0.23 in c:\programdata\anaconda3\lib\site-packages (from jinja2>=2.9->folium) (1.1.1)
    Requirement already satisfied: pytz>=2017.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2021.1)
    Requirement already satisfied: python-dateutil>=2.7.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2.8.1)
    Requirement already satisfied: six>=1.5 in c:\programdata\anaconda3\lib\site-packages (from python-dateutil>=2.7.3->pandas) (1.15.0)
    Requirement already satisfied: idna<3,>=2.5 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2.10)
    Requirement already satisfied: certifi>=2017.4.17 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2020.12.5)
    Requirement already satisfied: chardet<5,>=3.0.2 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (4.0.0)
    Requirement already satisfied: urllib3<1.27,>=1.21.1 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (1.26.4)
    




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_235c52551e154205bb9aca4e91ea3a1f%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_235c52551e154205bb9aca4e91ea3a1f%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_235c52551e154205bb9aca4e91ea3a1f%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_235c52551e154205bb9aca4e91ea3a1f%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.64%2C%20-0.88%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_28d85ea92ba344e0aae5443e32463148%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d4a94cc8097e4658aef6ee426f10b02f%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649027473051156%2C%20-0.8818527060979306%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_9cb70c8ef4d74cf48a10cb60bc8e1a74%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_099c5d1478014747a651c6ea07bea400%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_099c5d1478014747a651c6ea07bea400%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_9cb70c8ef4d74cf48a10cb60bc8e1a74.setContent%28html_099c5d1478014747a651c6ea07bea400%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d4a94cc8097e4658aef6ee426f10b02f.bindPopup%28popup_9cb70c8ef4d74cf48a10cb60bc8e1a74%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_1f12d9c162a3477db124464cfe606a97%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.661585829868585%2C%20-0.8645810716721081%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d11f0f7e8cf54a8f9216b9fed486dde9%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b2058ca7e117474daf41bd8d155cdd2d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b2058ca7e117474daf41bd8d155cdd2d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d11f0f7e8cf54a8f9216b9fed486dde9.setContent%28html_b2058ca7e117474daf41bd8d155cdd2d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_1f12d9c162a3477db124464cfe606a97.bindPopup%28popup_d11f0f7e8cf54a8f9216b9fed486dde9%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_9ed16b7de96440d4bad3f0271abf0c60%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.666992622958105%2C%20-0.887776415002892%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b65f6343c88f4dce8284684998bca7a1%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c8a40d77007944a899b04a7bb0d113df%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c8a40d77007944a899b04a7bb0d113df%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b65f6343c88f4dce8284684998bca7a1.setContent%28html_c8a40d77007944a899b04a7bb0d113df%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_9ed16b7de96440d4bad3f0271abf0c60.bindPopup%28popup_b65f6343c88f4dce8284684998bca7a1%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_7f0c5d2c8be04fc2b59e114c92cb15a5%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.62957498750602%2C%20-0.8825260453930127%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_09b3cec9d920472ba7370dc2d0001971%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a2426d1297684daebdace07af10f3bcc%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a2426d1297684daebdace07af10f3bcc%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_09b3cec9d920472ba7370dc2d0001971.setContent%28html_a2426d1297684daebdace07af10f3bcc%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_7f0c5d2c8be04fc2b59e114c92cb15a5.bindPopup%28popup_09b3cec9d920472ba7370dc2d0001971%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_adbb303a59b24e6b9db0f02a9e0ee717%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.6562121210704%2C%20-0.908314757720389%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_37fab0510572483cbe53a8fe39f4d5ac%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ab779e8fc9054ec882e106fb34b5dfdf%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ab779e8fc9054ec882e106fb34b5dfdf%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_37fab0510572483cbe53a8fe39f4d5ac.setContent%28html_ab779e8fc9054ec882e106fb34b5dfdf%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_adbb303a59b24e6b9db0f02a9e0ee717.bindPopup%28popup_37fab0510572483cbe53a8fe39f4d5ac%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_29722c23aab044f196c8a0d0e3cd0bb6%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65949772773082%2C%20-0.8691088511672924%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_bb089c0e0fc045619bfbc744ba2f9a12%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_009a3fdc88804ca9934d394e78cdad08%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_009a3fdc88804ca9934d394e78cdad08%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_bb089c0e0fc045619bfbc744ba2f9a12.setContent%28html_009a3fdc88804ca9934d394e78cdad08%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_29722c23aab044f196c8a0d0e3cd0bb6.bindPopup%28popup_bb089c0e0fc045619bfbc744ba2f9a12%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_690de71596b1498aad86c66f717d7897%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.633353667694024%2C%20-0.8880337913721866%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_ffd7e55dc35d4a03b70f7ed91f4c5dbc%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_9ff5b9554a324c94a030d815c6fd6575%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_9ff5b9554a324c94a030d815c6fd6575%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_ffd7e55dc35d4a03b70f7ed91f4c5dbc.setContent%28html_9ff5b9554a324c94a030d815c6fd6575%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_690de71596b1498aad86c66f717d7897.bindPopup%28popup_ffd7e55dc35d4a03b70f7ed91f4c5dbc%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_38256b2f259e4f409a141efbee288b68%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.6390382112928%2C%20-0.8708838775078237%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_5a7d1c5214e84c8e8901451e5bdedac5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_14a8e36af0524b8eba87267b3f32fd24%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_14a8e36af0524b8eba87267b3f32fd24%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_5a7d1c5214e84c8e8901451e5bdedac5.setContent%28html_14a8e36af0524b8eba87267b3f32fd24%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_38256b2f259e4f409a141efbee288b68.bindPopup%28popup_5a7d1c5214e84c8e8901451e5bdedac5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_baf9074bb70948d9856e0c5ba7845d72%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.64083344974765%2C%20-0.8970649943808023%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_498a69b76d044acd8050d0c8dc114fda%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0e02db23a77b4276a9bae03e913efc7b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0e02db23a77b4276a9bae03e913efc7b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_498a69b76d044acd8050d0c8dc114fda.setContent%28html_0e02db23a77b4276a9bae03e913efc7b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_baf9074bb70948d9856e0c5ba7845d72.bindPopup%28popup_498a69b76d044acd8050d0c8dc114fda%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d13feb51991f4a01855a01cedf27e5c4%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.64904657717317%2C%20-0.8718525605769747%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_655f2b98e2f342acaf1284783897260e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_17f8a494c4f0440cb5320017c274590b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_17f8a494c4f0440cb5320017c274590b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_655f2b98e2f342acaf1284783897260e.setContent%28html_17f8a494c4f0440cb5320017c274590b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d13feb51991f4a01855a01cedf27e5c4.bindPopup%28popup_655f2b98e2f342acaf1284783897260e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_813c6f60313b4fd5823ce927982b9516%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.64322365075108%2C%20-0.8964627561577849%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b1ec835fa41c4863bb2f6640d7bcad9c%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_abb3a9e440694190b65b6952e3a7b0a8%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_abb3a9e440694190b65b6952e3a7b0a8%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b1ec835fa41c4863bb2f6640d7bcad9c.setContent%28html_abb3a9e440694190b65b6952e3a7b0a8%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_813c6f60313b4fd5823ce927982b9516.bindPopup%28popup_b1ec835fa41c4863bb2f6640d7bcad9c%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_bb6f717b9ea44fbabb9eadb7969272de%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.68753087470739%2C%20-0.8778095796207178%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_6d013716b21b4fee906130e939272ff4%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_fbbc3e07f1394d8b9757a9389f7364d9%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_fbbc3e07f1394d8b9757a9389f7364d9%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_6d013716b21b4fee906130e939272ff4.setContent%28html_fbbc3e07f1394d8b9757a9389f7364d9%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_bb6f717b9ea44fbabb9eadb7969272de.bindPopup%28popup_6d013716b21b4fee906130e939272ff4%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_67617d912f68423e9c2151b164c3e370%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.661646612715046%2C%20-0.8812157329722801%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_5ae085d2a460450482abefe665c13e79%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d74ebe65e07145c5ac4530e1eb293414%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d74ebe65e07145c5ac4530e1eb293414%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_5ae085d2a460450482abefe665c13e79.setContent%28html_d74ebe65e07145c5ac4530e1eb293414%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_67617d912f68423e9c2151b164c3e370.bindPopup%28popup_5ae085d2a460450482abefe665c13e79%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3ece34314172411d8b9d671b2363420d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.6454384961757%2C%20-0.8762000299022707%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_178fd2d94ddd4a24906d589a77fa9be5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_3a016877c7574c51a8bac44f34e020bb%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_3a016877c7574c51a8bac44f34e020bb%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_178fd2d94ddd4a24906d589a77fa9be5.setContent%28html_3a016877c7574c51a8bac44f34e020bb%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3ece34314172411d8b9d671b2363420d.bindPopup%28popup_178fd2d94ddd4a24906d589a77fa9be5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f4b5d221e67d40ff918f03de04b56009%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65543768899759%2C%20-0.9089013552408617%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_506dc629dd9c41678be09202f0e02c1c%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5211c8c83204445eb495d60b2523f3f6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5211c8c83204445eb495d60b2523f3f6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_506dc629dd9c41678be09202f0e02c1c.setContent%28html_5211c8c83204445eb495d60b2523f3f6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f4b5d221e67d40ff918f03de04b56009.bindPopup%28popup_506dc629dd9c41678be09202f0e02c1c%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3385c5c2d4584bf691693957c68ba830%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65180346604993%2C%20-0.9004729973337304%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_5027064d5675408c9ca33e67d060f264%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_4e9fe9d9644d47ca98d4d6de677a055a%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_4e9fe9d9644d47ca98d4d6de677a055a%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_5027064d5675408c9ca33e67d060f264.setContent%28html_4e9fe9d9644d47ca98d4d6de677a055a%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3385c5c2d4584bf691693957c68ba830.bindPopup%28popup_5027064d5675408c9ca33e67d060f264%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_985ccd354d9b4d0785cbc4ef35638945%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65233828238132%2C%20-0.8917562993466011%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_cda8a9383831404a97afc140b7e0c26c%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_dbdb2448a41e4561a54ef7be2a118990%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_dbdb2448a41e4561a54ef7be2a118990%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_cda8a9383831404a97afc140b7e0c26c.setContent%28html_dbdb2448a41e4561a54ef7be2a118990%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_985ccd354d9b4d0785cbc4ef35638945.bindPopup%28popup_cda8a9383831404a97afc140b7e0c26c%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f7e157bc635c400b9f3589b21b1577c5%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65040494617356%2C%20-0.888856043735591%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a4110910a32e41498a3bb2156abac236%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ad19ca99c3724e2ba94fa44ddcf16256%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ad19ca99c3724e2ba94fa44ddcf16256%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a4110910a32e41498a3bb2156abac236.setContent%28html_ad19ca99c3724e2ba94fa44ddcf16256%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f7e157bc635c400b9f3589b21b1577c5.bindPopup%28popup_a4110910a32e41498a3bb2156abac236%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e3239d0df8d848f4914f88d6dfbb7af8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.645335650478316%2C%20-0.8629911318784169%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7598fa8e6d7b4d4aa5096d1050be4fc7%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5bb62584f6634969ba1b8abac3ae3053%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5bb62584f6634969ba1b8abac3ae3053%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7598fa8e6d7b4d4aa5096d1050be4fc7.setContent%28html_5bb62584f6634969ba1b8abac3ae3053%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e3239d0df8d848f4914f88d6dfbb7af8.bindPopup%28popup_7598fa8e6d7b4d4aa5096d1050be4fc7%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f5565d42a60343a9a411fc7e0a57097d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.609992514227066%2C%20-0.8870207060655807%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_235c52551e154205bb9aca4e91ea3a1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_91648c5edd394cfba7d1b573d74d2ef6%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2c13d09c56924c6e98a22b4449b7192f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2c13d09c56924c6e98a22b4449b7192f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_91648c5edd394cfba7d1b573d74d2ef6.setContent%28html_2c13d09c56924c6e98a22b4449b7192f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f5565d42a60343a9a411fc7e0a57097d.bindPopup%28popup_91648c5edd394cfba7d1b573d74d2ef6%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



# Mapa con icono y guardar mapa
En la función `map()` de `folium` hay una propiedad `tiles` que puede tener como valor `Stamen Terrain`. Crea un mapa con las coordenadas de Madrid y sobre ese mapa un marcador con la función `Marker()` de `folium` cuya propiedad `icon` tiene como valor `folium.Icon(color='green')` Finalmente guardamos el mapa con `save('tipo.html')`


```python
coord = [40.535564, -3.6475137]
mapa = folium.Map(location=coord, tiles='Stamen Terrain')
marcador = folium.Marker(coord, icon=folium.Icon(color="green"))
mapa = mapa.add_child(marcador)
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_22629b029498495d99fdd8f2a8027a57%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_22629b029498495d99fdd8f2a8027a57%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_22629b029498495d99fdd8f2a8027a57%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_22629b029498495d99fdd8f2a8027a57%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B40.535564%2C%20-3.6475137%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_bd4e15305e144292adddfc77bb9ca25d%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//stamen-tiles-%7Bs%7D.a.ssl.fastly.net/terrain/%7Bz%7D/%7Bx%7D/%7By%7D.jpg%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Map%20tiles%20by%20%5Cu003ca%20href%3D%5C%22http%3A//stamen.com%5C%22%5Cu003eStamen%20Design%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//creativecommons.org/licenses/by/3.0%5C%22%5Cu003eCC%20BY%203.0%5Cu003c/a%5Cu003e.%20Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//creativecommons.org/licenses/by-sa/3.0%5C%22%5Cu003eCC%20BY%20SA%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_22629b029498495d99fdd8f2a8027a57%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_0ffd9b161fb645c3afec1f6935e94578%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B40.535564%2C%20-3.6475137%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_22629b029498495d99fdd8f2a8027a57%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20icon_8f20c05178a046268eefa4c0ba0ae49c%20%3D%20L.AwesomeMarkers.icon%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22extraClasses%22%3A%20%22fa-rotate-0%22%2C%20%22icon%22%3A%20%22info-sign%22%2C%20%22iconColor%22%3A%20%22white%22%2C%20%22markerColor%22%3A%20%22green%22%2C%20%22prefix%22%3A%20%22glyphicon%22%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20marker_0ffd9b161fb645c3afec1f6935e94578.setIcon%28icon_8f20c05178a046268eefa4c0ba0ae49c%29%3B%0A%20%20%20%20%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>




```python
mapa.save('./tipo.html')
```
