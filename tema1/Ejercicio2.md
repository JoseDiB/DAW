
# Ejercicio 1
Crea un script que añada un puerto de escucha en el fichero de configuración de Apache. 
El puerto se recibirá como parámetro en la llamada y se comprobará que no esté ya presente en el fichero de configuración.

```sh
#!/bin/sh
if [ "$# -ne "1" ]
then
  echo "Error. Falta el número de puerto"
else
  grep "Listen $1" "/etc/apache2/ports.conf"
  if [ "$?" -eq "0" ]
  then
    echo "Listen encontrado en ports.conf"
  else
    echo "No encontrado y agregado"
    echo "Listen $1" >> "/etc/apache2/ports.conf"
  fi
fi
```

# Ejercicio 2
Crea un script que añada un puerto de escucha en el fichero de configuración de Apache. 
El puerto se recibirá como parámetro en la llamada y se comprobará que no esté ya presente en el fichero de configuración.

```sh
#!/bin/bash

read -p "Introduce la direccion IP: " ip
read -p "Introduce el nombre de dominio: " dominio

if grep -q "$dominio" /etc/hosts; then
        echo "El dominio $dominio ya existe en /etc/hosts."
else
        echo "$ip $dominio" | sudo tee -a /etc/hosts > /dev/null
        echo "EL dominio $dominio con IP $ip ha sido agregado a >
fi
```
# Ejercicio 3
Crea un script que nos permita crear una página web con un título, una cabecera y un mensaje
```sh
#!/bin/bash

read -p "Introduce el titulo de la página: " titulo
read -p "Introduce la cabecera de la página: " cabecera
read -p "Introduce el mensaje de la página: " mensaje

cat << EOF > pagina_web.html
<!DOCTYPE html>
<html lang="es">
<head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width-divice, initial-sca>
        <title>$titulo</title>
</head>
<body>
        <h1>$cabecera</h1>
        <p>$mensaje</p>
</body>
</html>
EOF

echo "La página web se ha creado como 'pagina_web.html'."

```

