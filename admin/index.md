# Política de privacidad — «RapidAnd Admin al lado»

Última actualización: 19 de noviembre de 2026 (versión 0.7.1)

«RapidAnd Admin al lado» es una extensión interna de RapidAnd para su equipo. Solo
la pueden instalar usuarios del dominio rapidand.com y solo funciona con una
sesión del admin de RapidAnd (admin.rapidand.com / admin.rapidsur.com).

## Qué datos trata y dónde
- **Sesión del admin:** el token de la sesión que el usuario ya tiene abierta en el
  admin. Se guarda solo en la memoria de sesión del navegador (`chrome.storage.session`),
  nunca en disco, y se borra al cerrar el navegador o al cerrar sesión en el admin (en el
  panel o en una pestaña normal del admin). El token solo se envía a la API de RapidAnd
  (api.rapidand.com / api.rapidsur.com, o la del admin configurado); cualquier otra
  dirección que anuncie una página se ignora.
- **Webs que visita con la sesión abierta:** mientras haya sesión del admin, la extensión
  consulta al backend de RapidAnd (con el token del usuario) **el dominio de la pestaña
  activa y de las webs https que se ven en pantalla** para saber si es una plataforma
  de compra con cuentas. Por tanto el servidor de RapidAnd puede conocer esos dominios, no
  las direcciones completas ni el contenido. Hay un tope global de 10 búsquedas de dominio nuevo
  por minuto. No se consulta nada sin sesión ni en pestañas en segundo plano.
- **Caché local por dominio:** el resultado («este dominio es la plataforma X» o «no es
  ninguna») se guarda en `chrome.storage.local` hasta 24 h (6 h si no es ninguna), hasta
  1000 dominios, ligado a la sesión; **se borra al cerrar sesión** y la ignora otro usuario.
  La lista de cuentas de cada plataforma se guarda 5 min en la memoria de sesión.
- **Cuentas de proveedores:** nombres de usuario de las cuentas de compra de RapidAnd en
  tiendas online, y, solo cuando el usuario pulsa «Rellenar» o «Copiar contraseña» (o se usa una
  passkey), la contraseña o la firma de la passkey de esa cuenta. Se obtienen del admin, se
  escriben en el formulario de la tienda o en el portapapeles, y no se guardan. La contraseña
  copiada se **borra del portapapeles a los 60 segundos** (también si se copió otra cosa después).
- **Registro de diagnóstico local:** las últimas 300 acciones de la extensión (qué se hizo, con qué
  resultado y a qué hora) en `chrome.storage.local`. Solo apunta dominios de plataformas conocidas
  (nunca otras webs), y nunca contraseñas, tokens, firmas ni challenges. No sale del ordenador salvo
  que el usuario pulse «Diagnóstico» para copiarlo y enviarlo a mano.
- **Preferencias locales:** zoom del panel y de las webs, pestañas del panel y si la barra de cuentas
  está oculta en cada web.

## Con quién se comparten
Con nadie salvo los servidores de RapidAnd (api.rapidand.com / api.rapidsur.com), que registran
cada uso de una contraseña o passkey con el usuario que lo hizo y reciben las consultas de dominio
descritas arriba. No se venden ni se ceden datos a terceros, no se usan para publicidad y no se
guarda un historial de navegación en la extensión más allá de la caché y el registro descritos.

## Contacto
hector@rapidand.com
