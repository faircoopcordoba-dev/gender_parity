#Algoritmo simple para comprobar la paridad de género en un grupo, asegurando que haya igual cantidad de hombres y mujeres.

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
