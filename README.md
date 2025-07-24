# Analisis de Conglomerados Jerárquico

### Establecer el directorio de trabajo y cargar los datos
```
import os

import pandas as pd

os.chdir('directory')

df = pd.read_csv('comunas.csv')

df.info()
```
### Importar bibliotecas
```
from scipy.cluster.hierarchy import linkage, dendrogram

import matplotlib.pyplot as plt
```
### Definir los datos X (excluir 'comuna')
```
X = df.drop('comuna', axis=1)
```
### Realizar la agrupación jerárquica
```
Z = linkage(X, method='ward')  # Probar con 'average', 'complete', 'single' si es necesario
```
### Graficar un dendrograma horizontal
```
plt.figure(figsize=(8, 5))  # Ajustar el tamaño si es necesario

dendrogram(

    Z,
    
    labels=df['comuna'].values,
    
    orientation='left',  # Situar el dendrograma en posición horizontal
    
    leaf_font_size=6,    # Ajustar el tamaño de la fuente

)

plt.title('Hierarchical Cluster Analysis')

plt.xlabel('Distance')

plt.ylabel('Comuna')

plt.tight_layout()  # Previene la pérdida de la etiqueta

plt.show()
```

![Dendrograma](docs/assets/images/cluster_comunas_RM.png)
