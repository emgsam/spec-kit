# Especificación: Menú PDF v1

## 1. Objetivo y contexto de negocio

Muchos restaurantes necesitan su menú en PDF para imprimir, compartir por WhatsApp o redes, o poner detrás de un QR. Hoy dependen de un diseñador cada vez que cambia un precio o un plato. Esta web permite que cualquier restaurante arme su menú, lo guarde, lo actualice cuando quiera y descargue un PDF prolijo con su identidad.

## 2. Usuarios

- **Encargado del restaurante:** conoce sus platos, precios y datos del local. No sabe de diseño ni de herramientas técnicas.
- **Cliente del restaurante:** recibe el PDF (impreso, por WhatsApp o QR) sin usar la app. Necesita leerlo fácil y poder contactar al local.

## 3. Escenarios de usuario (historias)

- HU1 — Como encargado, quiero crear mi cuenta, para que mi menú quede guardado y solo yo lo edite.
- HU2 — Como encargado, quiero cargar nombre, logo, dirección y WhatsApp del restaurante, para que el cliente sepa quiénes somos y cómo contactarnos.
- HU3 — Como encargado, quiero crear y ordenar categorías, para que el menú sea fácil de recorrer.
- HU4 — Como encargado, quiero cargar platos con nombre, descripción, precio y foto, para que el cliente sepa qué pide.
- HU5 — Como encargado, quiero ajustar el diseño (colores, tipografía, mostrar u ocultar fotos), para que el menú refleje el estilo del local.
- HU6 — Como encargado, quiero ver una vista previa y descargar el PDF, para imprimirlo o compartirlo.
- HU7 — Como encargado, quiero volver otro día y editar mi menú, para actualizar precios sin empezar de cero.
- HU8 — Como encargado, quiero marcar alérgenos y etiquetas (vegano, sin TACC, etc.) en cada plato, para que el cliente elija con seguridad.
- HU9 — Como encargado, quiero cargar varios precios por plato según el tamaño (ej: chica / grande), para no duplicar platos.

## 4. Requisitos funcionales

- RF1. El sistema debe permitir que cualquier persona cree una cuenta e ingrese a ella.
- RF2. El sistema debe guardar el menú de cada cuenta y mostrarlo al volver a ingresar.
- RF3. El sistema debe permitir cargar y editar nombre, logo, dirección y WhatsApp del restaurante.
- RF4. El sistema debe permitir crear, editar, borrar y reordenar categorías.
- RF5. El sistema debe permitir crear, editar, borrar y reordenar platos dentro de una categoría, con nombre, descripción, precio y foto opcional.
- RF6. El sistema debe ofrecer un único diseño con opciones configurables: colores, tipografía y mostrar u ocultar fotos.
- RF7. El sistema debe mostrar una vista previa del menú igual al PDF final.
- RF8. El sistema debe generar un PDF descargable, de una o varias páginas.
- RF9. El sistema debe permitir asignar a cada plato alérgenos de una lista fija: gluten, lácteos, huevo, maní, frutos secos, soja, pescado y mariscos.
- RF10. El sistema debe permitir asignar a cada plato etiquetas de una lista fija: vegano, vegetariano, sin TACC y picante.
- RF11. El sistema debe permitir que un plato tenga un precio único o varios precios con nombre de tamaño.
- RF12. El PDF debe mostrar los alérgenos y etiquetas de cada plato, y una leyenda que explique los íconos o abreviaturas.

## 5. Reglas de negocio (con ejemplos)

- RN1. Un menú pertenece a una sola cuenta. Ej: el usuario A no puede ver ni editar el menú del usuario B.
- RN2. Todo plato pertenece a una categoría. Ej: no se puede crear "Flan" sin elegir categoría.
- RN3. Nombre y precio del plato son obligatorios, y el precio debe ser mayor que 0. Ej: un plato con precio vacío o "$0" no se guarda.
- RN4. El precio se muestra como moneda local. Ej: 4500 se ve "$4.500".
- RN5. El nombre del restaurante es obligatorio para generar el PDF. Logo, dirección, WhatsApp y fotos son opcionales.
- RN6. No se puede generar el PDF si el menú no tiene ningún plato. Ej: con 0 platos, el botón avisa "Agregá al menos un plato".
- RN7. Una categoría sin platos no aparece en el PDF. Ej: "Postres" vacía no se muestra.
- RN8. El WhatsApp debe tener formato de teléfono válido. Ej: "hola123" se rechaza.
- RN9. Un plato tiene precio único **o** precios por tamaño, nunca las dos cosas. Ej: "Pizza muzza" con Chica $8.000 y Grande $12.000 no muestra además un precio suelto.
- RN10. Con precios por tamaño, cada tamaño necesita nombre y precio mayor que 0, y los nombres no se repiten en el mismo plato. Ej: dos tamaños "Grande" en el mismo plato se rechazan.
- RN11. "Vegano" y "contiene lácteos o huevo" no pueden ir juntos. Ej: un plato vegano con lácteos se rechaza con un aviso.
- RN12. La leyenda del PDF muestra solo los alérgenos y etiquetas que se usan en el menú. Ej: si ningún plato tiene "soja", la leyenda no la incluye.
- RN13. La descripción larga se muestra completa en el PDF, en las líneas que haga falta. Ej: una descripción de 300 caracteres no se corta.

## 6. Criterios de aceptación (verificables sin código)

- CA1. Creo una cuenta, cargo un menú, cierro sesión, vuelvo a entrar y mi menú sigue igual.
- CA2. Con 2 categorías de 3 platos cada una, el PDF muestra los 6 platos en su categoría y en el orden elegido.
- CA3. El PDF muestra nombre, logo, dirección y WhatsApp del restaurante.
- CA4. Si cambio el color principal, la vista previa y el PDF muestran el nuevo color.
- CA5. Un plato sin precio no se guarda y aparece un mensaje que dice por qué.
- CA6. Con 0 platos no puedo descargar el PDF y veo un aviso.
- CA7. Una categoría vacía no aparece en el PDF.
- CA8. Un menú con 40 platos genera un PDF de varias páginas, sin platos cortados entre una página y otra.
- CA9. Desde la cuenta B no puedo ver el menú de la cuenta A.
- CA10. Marco "sin TACC" y "gluten" en platos distintos, y el PDF los muestra en cada plato junto con la leyenda.
- CA11. Una pizza con dos tamaños muestra ambos precios en el PDF.
- CA12. Un plato con descripción de 300 caracteres se ve completo en el PDF.

## 7. Casos límite

- CL1. ¿Qué pasa si el menú no tiene platos? No se genera el PDF (RN6).
- CL2. ¿Qué pasa si una categoría está vacía? Se oculta en el PDF (RN7).
- CL3. ¿Qué pasa si el menú es largo? Pasa a varias páginas, y un plato o un título de categoría nunca queda cortado al final de una página.
- CL4. ¿Qué pasa si no cargo logo ni fotos? El PDF se genera igual, sin huecos vacíos.
- CL5. ¿Qué pasa si subo una imagen enorme o un archivo que no es imagen? Se rechaza con un mensaje.
- CL6. ¿Qué pasa si la descripción de un plato es muy larga? Se muestra completa, en las líneas que haga falta (RN13).
- CL7. ¿Qué pasa si borro una categoría con platos? Pide confirmación antes de borrar la categoría y sus platos.
- CL8. ¿Qué pasa si ningún plato tiene alérgenos ni etiquetas? El PDF no muestra leyenda.
- CL9. ¿Qué pasa si paso un plato de varios tamaños a precio único? Pide confirmación, porque se pierden los tamaños.

## 8. Fuera de alcance

Esta versión **no** incluye:

- Más de un menú por cuenta.
- Varios diseños o plantillas para elegir.
- Menú en varios idiomas.
- Pedidos, reservas o pagos.
- Menú web público o generación de QR (el PDF se puede compartir, pero la app no genera el QR).
- Varios usuarios editando el mismo restaurante.
