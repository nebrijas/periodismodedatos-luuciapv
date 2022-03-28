# Actividad Dirigida 2

En esta parte de la Actividad Dirigida 2 disponemos el código en bruto para comprender bien la Actividad Dirigida 2

## Librerías
El primer paso es importar la librería requests. Esto nos da la opción de acceder a la página web en la que vamos a realizar el scrapping. La librería BeautifulSoup sirve para analizar los datos que nos hemos descargado.

## Variables
El segundo paso es definir las variables. 

Ante todo, lo primero que se indica es la URL de donde queremos sacar los datos ("https://resultados.elpais.com/deportivos/juegos-olimpicos/medallero/"). Eso sí, , debemos hacer la ordenanza con req = requests.get(URL).

También, hay que indicar la petición de que si el estatus code es distinto: if (req.status_code != 200) no puede hacer web sraping. Si req.status_code == 200, el código se refereirá a él con la expresión "Vamos a por ello".

Para poder leer y comprender el contenido HTML, pasamos la referencia a un objeto BeautifulSoup html = BeautifulSoup(req.text, "html.parser").

### Datos
Nuestras variables, en este caso, son países, oros, platas, bronces y totale. Para poder relacionarse entre ellas, debemos identificar variables nombradas con la función find_all() para que pueda encontrar en la web elegida y las organice.

Para que el código funicone, repetimos las instrucciones 20 veces, ya que son 20 países: for i in range (20), es decir, un bucle. El código realizado establecerá los números, con %d, y el texto con %s. Gracias a el bucle y pulsando a 'run' todo estrá en orden

## Pregunta
Realizamos la pregunta, que este caso es la siguiente: "¿QUIERES CONOCER LOS 20 PAÍSES QUE HAN OBTENIDO MÁS MEDALLAS EN 2020?", a partir de ella se comienza. En el siguiente paso es que el usuario pulse a la tecla 's' del teclado, por lo que se le escribe también esta orden. Esto lo identificará como correcto, el código indica escrito "De acuerdo" y se empieza el bucle y aparecerán las respuestas a la pregunta.

## Bucle para obtener los datos
Y, finalmente, el bucle para obtener los datos es el último paso. Sin él no se, da la posibilidad de 'seguir jugando', que en este caso la hemos nombrado como 'Qué lástima, y...'

## Este es el codigo de la Actividad Diriga 2

```

from bs4 import BeautifulSoup
import requests
#Datos sobre los Juegos Olímpicos en 2020

respuesta=input('¿QUIERES CONOCER LOS 20 PAÍSES QUE HAN OBTENIDO MÁS MEDALLAS EN 2020?\n \n Si tu respuesta es Sí, presiona "s" \n')
if(respuesta == 's'):
  print('\nRESULTADOS DE LOS DATOS DE LOS JUEGOS OLÍMPICOS 2020\n')
  print ('PAÍSES')
  URL = "https://resultados.elpais.com/deportivos/juegos-olimpicos/medallero/"
  # Realizamos la petición a la web
  req = requests.get(URL)
  # Si el estatus code no es 200 no se puede leer la página
  if (req.status_code != 200):
    raise Exception("No se puede hacer Web Scraping en"+ URL)
  # Pasamos el contenido HTML de la web a un objeto BeautifulSoup()
  html = BeautifulSoup(req.text, "html.parser")
  # Obtenemos todos los divs donde están las entradas
  paises = html.find_all("th",{"class":"pais"})
  oros = html.find_all("td",{"class":"m_oro"})
  platas = html.find_all("td",{"class":"m_plata"})
  bronces = html.find_all("td",{"class":"m_bronce"})
  totales = html.find_all("td",{"class":"m_total"})
  for i in range (20):
    # Con el método "getText()" no nos devuelve el HTML
    print("%d. %s \nOro: %s Plata: %s Bronce: %s \n Total: %s \n " % (i+1, paises[i+1].text.strip(),oros[i].text.strip(),platas[i].text.strip(),bronces[i].text.strip(), totales[i].text.strip()))

else:
  print('Qué lástima, y...')
```
