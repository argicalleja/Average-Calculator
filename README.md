# Average-Calculator
Practical Python experiments to learn programming, test ideas, and understand how code works.
def ingresar_calificaciones():
    materias = []
    calificaciones = []

    while True:
        materia = input("Introduce el nombre de la materia: ")

        while True:
            try:
                calificacion = float(input("Introduce la calificación (0-10): "))

                if 0 <= calificacion <= 10:
                    break
                else:
                    print("La calificación debe estar entre 0 y 10.")

            except ValueError:
                print("Debes introducir un número válido.")

        materias.append(materia)
        calificaciones.append(calificacion)

        continuar = input("¿Quieres añadir otra materia? (s/n): ").lower()

        if continuar != "s":
            break

    return materias, calificaciones


def calcular_promedio(calificaciones):
    return sum(calificaciones) / len(calificaciones)


def determinar_estado(calificaciones, umbral=5.0):
    aprobadas = []
    reprobadas = []

    for indice in range(len(calificaciones)):
        if calificaciones[indice] >= umbral:
            aprobadas.append(indice)
        else:
            reprobadas.append(indice)

    return aprobadas, reprobadas


def encontrar_extremos(calificaciones):
    indice_maximo = calificaciones.index(max(calificaciones))
    indice_minimo = calificaciones.index(min(calificaciones))

    return indice_maximo, indice_minimo


def main():
    materias, calificaciones = ingresar_calificaciones()

    if len(materias) == 0:
        print("No se ha introducido ninguna materia.")
        print("Programa finalizado.")
        return

    promedio = calcular_promedio(calificaciones)

    aprobadas, reprobadas = determinar_estado(calificaciones)

    indice_maximo, indice_minimo = encontrar_extremos(calificaciones)

    print("\n--- RESUMEN FINAL ---")

    print("\nMaterias y calificaciones:")

    for indice in range(len(materias)):
        print(f"{materias[indice]}: {calificaciones[indice]}")

    print(f"\nPromedio general: {promedio:.2f}")

    print("\nMaterias aprobadas:")
    for indice in aprobadas:
        print(f"- {materias[indice]}: {calificaciones[indice]}")

    print("\nMaterias reprobadas:")
    for indice in reprobadas:
        print(f"- {materias[indice]}: {calificaciones[indice]}")

    print(
        f"\nMejor calificación: "
        f"{materias[indice_maximo]} - {calificaciones[indice_maximo]}"
    )

    print(
        f"Peor calificación: "
        f"{materias[indice_minimo]} - {calificaciones[indice_minimo]}"
    )

    print("\nGracias por utilizar la calculadora de promedios.")


if __name__ == "__main__":
    main()
