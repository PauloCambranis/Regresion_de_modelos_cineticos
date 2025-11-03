# Ajuste de parámetros cinéticos con R
La regresión no lineal tiene varias ventajas sobre métodos gráficos como Lineweaver-Burk. Es más exacta, tiene menos distorciones y es muy fácil de hacer con herramientas tan poderosas como **R**, el lenguaje de programación pensado para estadística.
En este repositorio puedes encontrar el script de R para ajustar tu cinética. Sigue estos pasos:
1. Si no tienes instalado R, puedes ir a una consola en línea como https://rdrr.io/snippets/
2. Copia y pega en la consola el contenido del archivo Script R de este repositorio.
3. Reemplaza los valores de muestra con tus propios datos. Si los pegas de excel, asegúrate de respetar la sintaxis de R:
```R
datos <- c(0.1, # la lista se declara con c()
           0.2, # Cuidado con las comas
           0.3)
```

Hay varios scripts en este repositorio para diversos modelos, incluyendo:
- Cinética enzimática clásica de Michaelis-Menten
- Cinética enzimática con inhibición por sustrato
- Cinética de crecimiento microbiano de Monod
- Cinética de crecimiento de Monod y Tessier (comparación)
- Regresión Lineal

Más modelos pronto!

---
## Solución de problemas
### Problemas causados por las comas y los datos de entrada
Si obtienes alguno de estos errores, verifica que copiaste bien los datos, que les pusiste comas a todos excepto al último, y que son el mismo número de datos,

Falta una coma:
```R
Error: unexpected numeric constant in:
"
```
El ultimo elemento tiene una coma:
```R
Error in c(0.05, 0.1, 0.3, 0.5, 1, 2.5, 5, 8, 12, 16, 20, 25, 30, 40,  : 
  argument 16 is empty
```
No son el mismo numero de datos
```R
arguments imply differing number of rows: 15, 16
```

### Problemas relacionados al fallo del metodo iterativo
En el caso del modelo con inhibicion por sustrato, el modelo es muy sensible a los valores de inicializacion y a los datos de entrada. Si los datos no son de unexperimento con inhibicion, es probable que falle con un error que menciona que hay un problema con el calculo de la gradiente, como este:
```R
In prof$getProfile() : singular gradient
```
