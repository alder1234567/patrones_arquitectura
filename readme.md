 # patrones arquitectonicos
 [ INOTE ]
 
 👍Un  **patron arquitectonico** es una solucion general y 😁reutilisable a un problema comum en la arquitectura de sftware ❤️
 dentro de un contexto dado . los patrones arquitectonicos son las habilidades de organizacion a nivel de carpetas dentro del proyecto de sftware 😎
 
![alt text](image.png)

PATRONES ARQUITECTONICOS MAS CONOCIDOS

 1. Patron de capas
 2. patron cliente-servidor
 3. patron maestro-esclavo 
 4. patron filtro de tuveria
 5. patron igual a igual
 6. patron de intermidiario
 7. patron de bus evento
 8. modelo-vista-controlador
 9. arquitectura limpia
 10. arquitectura hexagonal
 
  ![alt text](image-1.png)  

# PATRON DE filtro DE TUBERIA


 El patrón de filtro de tubería, también conocido como patrón de filtro de tubería y filtro, es un patrón de diseño que se utiliza comúnmente en el desarrollo de software. Este patrón se utiliza para procesar datos secuenciales de manera eficiente y modular, dividiendo el proceso en etapas o filtros que se aplican secuencialmente a los datos.

La idea básica detrás del patrón de filtro de tubería es tener una serie de componentes llamados "filtros", cada uno de los cuales realiza una operación específica en los datos que pasan a través de él. Estos filtros están conectados entre sí formando una tubería, donde la salida de un filtro se convierte en la entrada del siguiente.

Los principales beneficios de este patrón incluyen:

Modularidad: Cada filtro es independiente y puede ser reutilizado o modificado sin afectar a otros componentes de la tubería.

Facilidad de mantenimiento: Los cambios en el proceso de filtrado se pueden realizar fácilmente añadiendo, eliminando o modificando filtros individuales.

Escalabilidad: Se pueden agregar nuevos filtros para ampliar la funcionalidad sin necesidad de reescribir el código existente.

Por ejemplo, en el procesamiento de imágenes, se podría implementar una tubería de filtro para realizar operaciones como ajuste de contraste, filtrado de ruido y detección de bordes, donde cada filtro realizaría una de estas tareas en la imagen.

La implementación del patrón de filtro de tubería puede variar según el lenguaje de programación y el contexto específico del problema a resolver, pero en general, implica la creación de clases o funciones para cada filtro y una forma de conectarlos entre sí para formar la tubería.



class FiltroBase:
    def _init_(self):
        pass
    
    def aplicar(self, datos):
        raise NotImplementedError()

class FiltroEliminarCaracteresEspeciales(FiltroBase):
    def aplicar(self, datos):
        return ''.join(c for c in datos if c.isalnum() or c.isspace())

class FiltroConvertirMinusculas(FiltroBase):
    def aplicar(self, datos):
        return datos.lower()

class FiltroEliminarPalabrasVacias(FiltroBase):
    def _init_(self, palabras_vacias):
        self.palabras_vacias = palabras_vacias
    
    def aplicar(self, datos):
        return ' '.join(word for word in datos.split() if word.lower() not in self.palabras_vacias)

def aplicar_filtro_tuberia(datos, filtros):
    resultado = datos
    for filtro in filtros:
        resultado = filtro.aplicar(resultado)
    return resultado

texto = "¡Hola, mundo! Este es un ejemplo de texto. Contiene palabras vacías como 'es' y 'un'."
filtros = [
    FiltroEliminarCaracteresEspeciales(),
    FiltroConvertirMinusculas(),
    FiltroEliminarPalabrasVacias(['es', 'un'])
]
resultado = aplicar_filtro_tuberia(texto, filtros)
print(resultado)




El patrón de filtro de tubería es un concepto de diseño de software más que una herramienta o tecnología específica, por lo que es utilizado por empresas en una variedad de sectores y contextos de desarrollo de software. Aquí hay algunas empresas y organizaciones que podrían estar utilizando este patrón:

1. Empresas tecnológicas: Gigantes como Google, Facebook y Amazon lo emplean para procesar grandes volúmenes de datos en tiempo real, como la personalización de contenido, análisis de datos de usuarios y procesamiento de transacciones.

2. Empresas financieras: Instituciones bancarias, empresas de gestión de inversiones y firmas de trading utilizan este patrón para analizar datos del mercado financiero, ejecutar algoritmos de trading y detectar fraudes en tiempo real.

3. Empresas de salud: Compañías farmacéuticas, hospitales y proveedores de atención médica emplean este patrón para procesar datos de pacientes, analizar resultados de pruebas médicas y monitorear la eficiencia operativa.

4. Empresas de comercio electrónico: Plataformas como eBay, Alibaba y Shopify lo utilizan para analizar datos de ventas, recomendar productos a los usuarios y optimizar la experiencia de compra en línea.

5. Empresas de logística y transporte: Compañías de transporte, como UPS y FedEx, utilizan este patrón para rastrear envíos, optimizar rutas de entrega y gestionar inventarios de manera eficiente.