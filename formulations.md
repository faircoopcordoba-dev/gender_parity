# Algoritmo simple para comprobar la paridad de género en un grupo, asegurando que haya igual cantidad de hombres y mujeres.

```python
def comprobar_paridad_genero(grupo):
    """
    grupo: lista de strings donde cada elemento es 'H' para hombre o 'M' para mujer
    Retorna True si hay igual cantidad de hombres y mujeres, False en caso contrario
    """
    conteo_hombres = grupo.count('H')
    conteo_mujeres = grupo.count('M')

    return conteo_hombres == conteo_mujeres

# Ejemplo de uso
grupo = ['H', 'M', 'M', 'H', 'H', 'M']
print(comprobar_paridad_genero(grupo))  # Esto imprime False porque hay 3 hombres y 3 mujeres
```

---

# Con Google Sheets

Para crear una fórmula en Google Sheets que compruebe paridad de género en un grupo, donde haya igual cantidad de hombres que de mujeres, puedes usar la función CONTAR.SI para contar cada grupo y luego compararlos. Suponiendo que los géneros estén en el rango A2:A100 con "H" para hombres y "M" para mujeres, la fórmula sería:

```
=CONTAR.SI(A2:A100,"H")=CONTAR.SI(A2:A100,"M")
```

Esta fórmula devuelve VERDADERO si la cantidad de "H" es igual a la de "M", es decir, paridad de género, o FALSO si no lo es.

Además, para mostrar la cantidad de cada género por separado en celdas diferentes, puedes usar:

    Para hombres: =CONTAR.SI(A2:A100,"H")

    Para mujeres: =CONTAR.SI(A2:A100,"M")

Esta solución es fácil de aplicar y permite controlar rápidamente si un grupo es equilibrado en términos de género, directamente desde Google Sheets, sin necesidad de código adicional ni complementos.

https://youtu.be/TGAycGZNY0I?si=PFOJJ5wfN0dzVE0j



USE:
https://docs.google.com/spreadsheets/d/1tbcHGJtyQNUlK-Zj6qdp7Txw_MVN_13uQUKCNtyar7c/edit?usp=sharing


# Para control de areas y departamentos en partes iguales

Para contabilizar por grupos de especialidades en Google Sheets y asegurarte de que haya partes iguales de integrantes, como ingenieros de software, programadores, recursos humanos, y marketing, se puede hacer lo siguiente:

1. Organiza en columnas la información: una columna con el nombre o ID del integrante, otra con el género (por ejemplo, "H" o "M"), y otra con la especialidad o departamento (por ejemplo, "Ingeniería", "Marketing").

2. Para contar el número de integrantes por género y especialidad usa la función CONTAR.SI.CONJUNTO. Por ejemplo, para contar hombres en Ingeniería:
   
   ``` 
   =CONTAR.SI.CONJUNTO(B2:B100, "H", C2:C100, "Ingeniería") 
   ```
   
   y para mujeres en Ingeniería:
   
   ```
   =CONTAR.SI.CONJUNTO(B2:B100, "M", C2:C100, "Ingeniería")
   ```

3. Repite para cada departamento o especialidad.

4. Para controlar que la cantidad sea igual entre géneros en cada área, usa una fórmula que compare ambas cantidades, por ejemplo:

   ```
   =CONTAR.SI.CONJUNTO(B2:B100,"H", C2:C100,"Ingeniería") = CONTAR.SI.CONJUNTO(B2:B100,"M", C2:C100,"Ingeniería")
   ```

5. Para decidir qué integrante agregar y mantener la paridad por área, deberás revisar estos conteos y añadir solo de la categoría de género que esté en menor cantidad dentro de la especialidad.

Esta estructura te permite administrar el crecimiento equitativo por género y área dentro de la empresa, y verificarlo automáticamente con fórmulas en Google Sheets.

Esta es la forma básica para contabilizar y comparar.


# Algoritmo Python

Algoritmo en Python para gestionar la paridad de género dentro de grupos o especialidades, asegurando que haya igualdad de hombres y mujeres en cada área:

```python
from collections import defaultdict

def verificar_paridad_por_grupo(personas):
    """
    personas: lista de diccionarios con 'nombre', 'genero' y 'especialidad'
    genero: 'H' o 'M'
    Retorna True si en todas las especialidades hay igual cantidad de hombres y mujeres;
    False y detalle si no.
    """
    conteo = defaultdict(lambda: {'H': 0, 'M': 0})

    for p in personas:
        genero = p['genero']
        especialidad = p['especialidad']
        conteo[especialidad][genero] += 1

    desequilibrios = {}
    for esp, counts in conteo.items():
        if counts['H'] != counts['M']:
            desequilibrios[esp] = counts

    if desequilibrios:
        return False, desequilibrios
    return True, {}

# Ejemplo de uso:
grupo_personas = [
    {'nombre': 'Ana', 'genero': 'M', 'especialidad': 'Ingeniería'},
    {'nombre': 'Juan', 'genero': 'H', 'especialidad': 'Ingeniería'},
    {'nombre': 'Lucía', 'genero': 'M', 'especialidad': 'Marketing'},
    {'nombre': 'Carlos', 'genero': 'H', 'especialidad': 'Marketing'},
    {'nombre': 'Pedro', 'genero': 'H', 'especialidad': 'Marketing'},
]

paridad, detalles = verificar_paridad_por_grupo(grupo_personas)
if paridad:
    print("Hay paridad de género en todos los grupos.")
else:
    print("Desequilibrios detectados por especialidad:")
    for esp, counts in detalles.items():
        print(f"{esp}: Hombres={counts['H']}, Mujeres={counts['M']}")
```

Con este algoritmo puedes agregar integrantes y verificar si la paridad de género se mantiene en cada especialidad. En caso de desequilibrio, muestra en qué áreas hay más hombres o más mujeres, lo que te ayuda a decidir qué perfil añadir para mantener la igualdad.

Este algoritmo es básica y puede extenderse para sugerir automáticamente qué tipo de integrante agregar para equilibrar, pero ya te da una herramienta para control manual del balance en el crecimiento de la empresa.


