# Informe de proyecto: NortePass

## Infraestructura global de ticketing descentralizado sobre Solana

**Estado del proyecto:** Etapa de conceptualización y diseño de MVP.

**Alcance:** Internacional.

**Sector:** Ticketing, entretenimiento, eventos deportivos, blockchain y Web3.

**Tecnología principal:** Solana.

---

## 1. Resumen ejecutivo

NortePass propone una plataforma global para comprar, transferir, revender y verificar entradas de eventos de alta demanda. El organizador define cómo se distribuyen las entradas, cuántas puede adquirir cada asistente y en qué condiciones se pueden revender. Si una persona ya no puede asistir, podría ofrecer su entrada en el mercado autorizado. El comprador podría verificar su titularidad y vigencia antes de presentarse en el recinto.

El proyecto combina cuatro objetivos: reducir las esperas durante la venta, distribuir el cupo de manera equitativa, dar al asistente una titularidad digital verificable y ofrecer una reventa con precios y condiciones transparentes. Solana serviría como registro compartido de emisión, transferencias y uso. Las mejoras en tiempos de compra y prevención del acaparamiento deberán medirse en el piloto.

NortePass podría operar con su propia plataforma o integrarse bajo la marca de una ticketera existente. Jujuy es un posible entorno piloto para evaluar la propuesta con organizadores y asistentes antes de expandirse a otros mercados.

[Leer el resumen corto de NortePass](resumen-nortepass.md)

## 2. Problemática identificada

### 2.1. Saturación durante ventas masivas

Durante la comercialización de entradas para eventos de gran popularidad, las plataformas tradicionales pueden experimentar:

- Colas virtuales prolongadas.
- Saturación de servidores.
- Interrupciones del servicio.
- Errores durante el procesamiento de pagos.
- Pérdida de reservas durante la compra.
- Incertidumbre sobre la disponibilidad real de entradas.

Se busca aprovechar el procesamiento paralelo de Solana, complementado con una infraestructura distribuida, para reducir los cuellos de botella tecnológicos y mejorar la experiencia de adquisición.

Se reconoce que ninguna tecnología puede eliminar la escasez de entradas cuando la demanda supera la oferta. El objetivo es reducir las esperas innecesarias y garantizar una distribución más eficiente y equitativa.

### 2.2. Acaparamiento de entradas

Los revendedores pueden utilizar bots, múltiples cuentas y sistemas automatizados para adquirir grandes cantidades de entradas durante los primeros minutos de una venta.

Posteriormente, estas entradas se comercializan a precios considerablemente superiores a los originales.

Esta situación perjudica a los consumidores legítimos, quienes deben competir contra mecanismos automatizados de adquisición.

### 2.3. Reventa abusiva y clandestina

El mercado secundario de entradas presenta problemas como:

- Especulación sobre los precios.
- Comercialización fuera de canales oficiales.
- Ausencia de garantías para compradores y vendedores.
- Entradas inexistentes o falsificadas.
- Venta simultánea de una misma entrada a diferentes personas.
- Falta de mecanismos seguros de intercambio.

NortePass no busca prohibir la reventa legítima, sino proporcionar un ecosistema en el cual pueda realizarse de manera controlada y segura.

### 2.4. Ausencia de propiedad digital verificable

En muchos sistemas tradicionales, las entradas son registros administrados exclusivamente por la empresa emisora.

NortePass propone representar cada entrada como un activo digital verificable en blockchain, cuya titularidad esté asociada al usuario y cuyo funcionamiento se encuentre gobernado por reglas programables.

## 3. Solución propuesta

Desarrollar una infraestructura híbrida Web2-Web3 que permita gestionar integralmente el ciclo de vida de una entrada:

1. Creación del evento.
2. Configuración del inventario y reglas comerciales.
3. Distribución de entradas.
4. Adquisición por parte de usuarios.
5. Asignación de titularidad digital.
6. Transferencia o publicación para reventa.
7. Comercialización secundaria segura.
8. Verificación de autenticidad.
9. Validación de acceso al evento.
10. Invalidación de la entrada después de su utilización.

Las operaciones que requieran garantías de autenticidad, propiedad y cumplimiento de reglas comerciales se realizarán mediante programas desplegados en Solana.

Los servicios que no requieran descentralización se implementarán mediante tecnologías convencionales.

## 4. Objetivos del proyecto

### Objetivo general

Transformar el ecosistema global de comercialización de entradas mediante una infraestructura tecnológica rápida, equitativa, verificable y resistente al fraude.

### Objetivos específicos

- Reducir los tiempos de procesamiento durante ventas masivas.
- Prevenir compras que superen los límites establecidos por evento.
- Reducir las ventajas de bots y revendedores especulativos.
- Garantizar la autenticidad de las entradas digitales.
- Proporcionar titularidad digital verificable.
- Implementar un mercado secundario seguro.
- Establecer límites programables sobre los precios de reventa.
- Evitar la utilización múltiple de una misma entrada.
- Permitir la integración con plataformas de ticketing existentes.
- Facilitar la adopción de blockchain sin exigir conocimientos técnicos a los usuarios.

## 5. Mercado objetivo

La plataforma está orientada a eventos y organizaciones internacionales, incluyendo:

- Partidos de fútbol.
- Mundiales y competencias deportivas internacionales.
- Conciertos de artistas reconocidos.
- Giras musicales internacionales.
- Festivales multitudinarios.
- Fórmula 1.
- Eventos de esports.
- Convenciones y congresos.
- Espectáculos culturales.
- Estadios y centros de entretenimiento.

Ejemplos conceptuales de aplicación incluyen eventos como la Copa Mundial de la FIFA, la UEFA Champions League, Tomorrowland, Coachella o conciertos de artistas con demanda internacional.

Estos ejemplos representan mercados potenciales y no asociaciones comerciales confirmadas.

El mercado regional de Jujuy, Argentina, podría utilizarse como entorno piloto para realizar pruebas con organizadores reales antes de buscar una expansión internacional.

## 6. Propuesta de valor

### Para los consumidores

- Mayor eficiencia durante el proceso de compra.
- Acceso más equitativo a las entradas.
- Titularidad digital verificable.
- Protección contra falsificaciones.
- Posibilidad de transferir o revender entradas legítimamente.
- Menor exposición a estafas.
- Transparencia sobre precios y condiciones comerciales.

### Para los organizadores

- Infraestructura escalable.
- Configuración de límites de compra.
- Control sobre las condiciones de reventa.
- Reducción de entradas falsificadas.
- Trazabilidad de operaciones.
- Gestión del inventario y aforo.
- Herramientas de análisis y prevención de fraude.
- Posibilidad de obtener ingresos del mercado secundario.

### Para plataformas de ticketing existentes

- Integración mediante API y SDK.
- Incorporación de funcionalidades blockchain.
- Infraestructura de propiedad digital.
- Mercado secundario verificable.
- Herramientas antiacaparamiento.
- Implementación bajo modalidad white label.

## 7. Implementación de ventas masivas mediante Solana

Solana constituye una de las tecnologías centrales de la propuesta debido a su arquitectura de ejecución paralela de transacciones.

El proyecto pretende aprovechar esta característica mediante el diseño de cuentas independientes y la distribución adecuada del inventario.

Por ejemplo, un evento con 80.000 entradas y un millón de compradores potenciales requeriría una infraestructura capaz de manejar solicitudes concurrentes sin depender de un único recurso compartido.

La arquitectura propuesta contempla:

- Inventario distribuido por sectores, lotes o entradas individuales.
- Procesamiento concurrente.
- Reservas temporales.
- Emisión anticipada de activos digitales.
- Infraestructura RPC redundante.
- Balanceadores de carga.
- CDN.
- Sistemas de mensajería asíncrona.
- Caché distribuida.
- Control de concurrencia.
- Protección contra ataques y solicitudes automatizadas.

Un riesgo técnico importante es la contención de cuentas compartidas en Solana. Si todas las compras requieren modificar una misma cuenta de inventario, tesorería o evento, el paralelismo podría verse limitado.

Por ello, el diseño deberá evitar puntos innecesarios de escritura compartida.

La mejora de rendimiento constituye una hipótesis que deberá verificarse experimentalmente mediante pruebas de carga y comparaciones con arquitecturas convencionales.

## 8. Sistema antiacaparamiento

Los organizadores podrán establecer reglas programables de adquisición.

Por ejemplo:

- Máximo de cuatro entradas por persona.
- Máximo de dos entradas por operación.
- Límite acumulado de adquisición por evento.
- Restricciones sobre transferencias recibidas.
- Reglas especiales para preventas.
- Límites sobre la cantidad de entradas disponibles para reventa.

El programa blockchain verificará el cumplimiento de las reglas antes de autorizar las operaciones.

Si una persona intenta adquirir una cantidad superior a la permitida, la transacción será rechazada.

El objetivo es evitar tanto una compra masiva individual como la acumulación mediante operaciones sucesivas.

### Problema de las múltiples wallets

Una dirección blockchain no representa necesariamente una persona.

Un revendedor podría crear numerosas wallets para intentar evadir los límites establecidos.

Por lo tanto, el proyecto requiere mecanismos complementarios:

- Verificación de identidad.
- Credenciales digitales verificables.
- Identificadores seudónimos específicos por evento.
- Prevención de cuentas duplicadas.
- Protección antibots.
- Limitación de solicitudes.
- Análisis de comportamiento.
- Control de dispositivos y sesiones, sujeto a restricciones de privacidad.

Los datos personales no deberán almacenarse directamente en blockchain.

La solución de identidad deberá demostrar que una misma persona no puede obtener múltiples cupos fácilmente, sin exponer públicamente su identidad.

Se reconoce que no será posible eliminar completamente los ataques mediante identidades prestadas, cuentas comercializadas o compradores coordinados.

## 9. Distribución equitativa

La velocidad tecnológica no garantiza por sí misma una distribución justa.

Una plataforma más rápida también podría favorecer a bots si no se establecen mecanismos de asignación adecuados.

Por este motivo, se evaluarán diferentes modelos:

- Orden de llegada.
- Salas de espera virtuales.
- Sorteos verificables.
- Ventanas temporales de adquisición.
- Preventas para socios.
- Cupos distribuidos por grupos.
- Asignación aleatoria durante eventos de demanda extrema.

El sistema deberá analizar qué mecanismo ofrece mejores condiciones de equidad sin perjudicar la experiencia del usuario.

## 10. Propiedad digital descentralizada

Cada entrada estará representada por un activo digital único en Solana.

La entrada podría contener:

- Identificador único.
- Identificador del evento.
- Dirección del propietario.
- Sector, fila y asiento.
- Precio original.
- Último precio de venta.
- Estado actual.
- Cantidad de transferencias.
- Restricciones comerciales.
- Fecha de expiración.

Se evaluarán diferentes implementaciones:

- Cuentas PDA administradas por un programa propio.
- NFTs.
- Tokens mediante Token-2022.
- Transfer Hook para incorporar reglas personalizadas.

La representación definitiva deberá seleccionarse considerando:

- Costos de emisión.
- Escalabilidad.
- Seguridad.
- Compatibilidad con wallets.
- Capacidad de restringir transferencias.
- Facilidad de integración.
- Posibilidad de recuperación de acceso.

La propiedad digital estará sujeta a las condiciones legítimas de utilización del evento.

No se presupone que la entrada sea un activo de libre transferencia sin restricciones.

Existe una tensión entre la descentralización de la propiedad y la necesidad de imponer reglas comerciales. El proyecto deberá definir explícitamente qué autoridad conserva el organizador y qué derechos adquiere el consumidor.

## 11. Ecosistema de reventa legítima

NortePass incorporará un marketplace integrado para que los usuarios puedan revender entradas cuando no puedan asistir a un evento.

El funcionamiento propuesto será:

1. El usuario adquiere una entrada.
2. La titularidad digital queda asignada a su wallet.
3. El usuario decide publicar la entrada para reventa.
4. El sistema verifica que sea su propietario.
5. El programa verifica que la entrada no haya sido utilizada.
6. Se comprueba que el precio respete las reglas del evento.
7. Otro usuario adquiere la entrada.
8. Se ejecuta el intercambio del pago y la titularidad.
9. El comprador pasa a ser el nuevo propietario.
10. El vendedor recibe el importe correspondiente.

Cuando el pago se realice mediante activos compatibles con Solana, como USDC, podrá implementarse un intercambio atómico dentro de una misma transacción.

Si el pago o la transferencia no pueden completarse, la operación deberá fallar sin producir un intercambio parcial.

Los pagos mediante moneda fiduciaria requerirán mecanismos externos de confirmación, conciliación y gestión de contracargos.

## 12. Control de precios de reventa

Los organizadores podrán configurar un precio máximo de reventa, calculado en función del precio original de adquisición.

Ejemplo:

- Precio original: USD 100.
- Incremento máximo autorizado: 10 %.
- Precio máximo de reventa: USD 110.

Si un usuario intenta publicar la entrada por USD 500, el programa rechazará la operación.

El límite deberá calcularse considerando el precio original y no el último precio de reventa, para evitar aumentos acumulativos mediante transferencias sucesivas.

También podrían configurarse:

- Comisiones máximas.
- Reventas únicamente al precio original.
- Períodos habilitados de comercialización.
- Cantidad máxima de reventas.
- Transferencias gratuitas autorizadas.
- Restricciones particulares por evento.

El objetivo es reducir la especulación y preservar la posibilidad de reventa legítima.

No obstante, la plataforma no puede impedir completamente acuerdos económicos realizados fuera de ella, pagos clandestinos o ventas de cuentas y wallets.

## 13. Validación de acceso

Los usuarios podrán presentar una credencial digital para ingresar al evento.

Se propone utilizar códigos QR dinámicos o desafíos criptográficos de corta duración.

El sistema verificará:

- Autenticidad de la entrada.
- Titularidad o autorización de uso.
- Correspondencia con el evento.
- Estado de la entrada.
- Vigencia de la credencial.
- Ausencia de utilización previa.

Una vez autorizado el ingreso, la entrada cambiará a estado utilizada.

Los intentos posteriores de utilizar la misma entrada deberán ser rechazados.

La implementación deberá contemplar escenarios de conectividad limitada, latencia, congestión de la red y escaneo simultáneo desde diferentes accesos.

## 14. Arquitectura tecnológica propuesta

### Frontend

- React o Next.js.
- TypeScript.
- Solana Wallet Adapter.
- Aplicación web adaptable a dispositivos móviles.
- Panel de organizadores.
- Marketplace.
- Interfaz de validación de acceso.

### Backend

- Spring Boot o FastAPI.
- Arquitectura modular.
- API REST.
- Autenticación y autorización.
- Gestión de usuarios.
- Gestión de identidad.
- Gestión de eventos.
- Procesamiento de pagos.
- Coordinación de operaciones blockchain.
- Prevención de fraude.
- Notificaciones.

### Infraestructura off-chain

- PostgreSQL.
- Redis.
- Sistemas de mensajería.
- Docker.
- CDN.
- Balanceadores de carga.
- Monitoreo y observabilidad.
- Proveedores de identidad.
- Proveedores de pagos.

### Infraestructura on-chain

- Solana.
- Rust.
- Anchor.
- Program Derived Addresses.
- Programas de emisión y adquisición.
- Registro de titularidad.
- Reglas de transferencia.
- Marketplace descentralizado.
- Registro de utilización de entradas.

El stack tecnológico es provisional y deberá evaluarse durante la etapa de diseño.

## 15. Separación entre blockchain e infraestructura tradicional

### Información on-chain

- Identificador de entrada.
- Titularidad digital.
- Estado de utilización.
- Reglas comerciales.
- Límites de adquisición.
- Historial de transferencias.
- Precio original.
- Operaciones de reventa.

### Información off-chain

- Datos personales.
- Documentos de identidad.
- Contraseñas.
- Imágenes de eventos.
- Información comercial.
- Información bancaria.
- Historial de navegación.
- Análisis de comportamiento.
- Notificaciones.
- Información operativa de los organizadores.

La arquitectura híbrida pretende utilizar blockchain únicamente cuando aporte garantías que justifiquen sus costos y complejidad.

## 16. Inteligencia artificial y prevención de fraude

Como funcionalidad complementaria, se contempla incorporar modelos de análisis de comportamiento para:

- Detectar compras automatizadas.
- Identificar patrones sospechosos.
- Detectar cuentas coordinadas.
- Analizar concentraciones anómalas de entradas.
- Identificar posibles intentos de fraude.
- Predecir la demanda.
- Optimizar la planificación de eventos.

La inteligencia artificial no constituye un requisito indispensable para el MVP.

Inicialmente podrían utilizarse reglas deterministas y mecanismos convencionales de seguridad, incorporando modelos de aprendizaje automático cuando exista suficiente información para entrenarlos y evaluarlos.

## 17. Experiencia de usuario y adopción

Uno de los requisitos fundamentales consiste en que los consumidores puedan utilizar NortePass sin conocimientos sobre blockchain.

Se evaluará la incorporación de:

- Registro mediante correo electrónico.
- Wallets integradas.
- Autenticación mediante passkeys.
- Recuperación segura de cuentas.
- Pagos mediante tarjetas y moneda fiduciaria.
- Patrocinio de comisiones de red.
- Abstracción de operaciones blockchain.
- Compatibilidad con wallets externas.

El consumidor no debería estar obligado a comprender conceptos como SOL, RPC, contratos inteligentes, claves privadas o comisiones de red para adquirir una entrada.

La implementación deberá equilibrar facilidad de uso, custodia, recuperación de acceso y propiedad descentralizada.

## 18. Modelo de negocio

El proyecto contempla diferentes mecanismos de monetización.

### B2C

Venta directa de entradas a consumidores mediante una aplicación propia.

### B2B

Provisión de infraestructura tecnológica para organizadores, clubes deportivos, artistas y empresas de entretenimiento.

### B2B2C

Integración con organizaciones que utilicen NortePass para comercializar entradas a sus propios consumidores.

### Marketplace

Comisión sobre operaciones legítimas de reventa.

### White label

Licenciamiento de la plataforma para que terceros puedan ofrecerla bajo su propia marca.

### API y SDK

Integración de funcionalidades blockchain, propiedad digital y prevención de fraude en plataformas existentes.

### SaaS

Suscripciones para acceder a herramientas de gestión, análisis de demanda, control de acceso y prevención de fraude.

## 19. Ejemplo económico hipotético

Considerando un evento internacional con:

- 80.000 entradas.
- Precio promedio de USD 100.
- Comisión de plataforma del 3 %.

El volumen total comercializado sería de USD 8.000.000.

Los ingresos brutos potenciales de NortePass serían de USD 240.000.

Estos valores son exclusivamente ilustrativos.

No representan una proyección financiera validada y no contemplan impuestos, costos de infraestructura, procesamiento de pagos, marketing, adquisición de clientes, devoluciones, seguridad ni gastos operativos.

La viabilidad económica deberá determinarse mediante investigación de mercado y análisis de costos reales.

## 20. Producto mínimo viable para una hackathon

El MVP deberá demostrar las características que diferencian al proyecto de una plataforma convencional.

Las funcionalidades propuestas son:

1. Creación de un evento.
2. Configuración de inventario limitado.
3. Configuración de límites de adquisición.
4. Conexión de wallets.
5. Adquisición de entradas digitales.
6. Asignación de titularidad on-chain.
7. Rechazo de compras que superen los límites.
8. Visualización de entradas adquiridas.
9. Publicación de entradas para reventa.
10. Rechazo de precios de reventa abusivos.
11. Compra legítima de una entrada mediante un intercambio atómico.
12. Transferencia de titularidad.
13. Validación de acceso.
14. Prevención del doble uso.
15. Pruebas de concurrencia.
16. Despliegue en Solana Devnet.

Para el MVP, la verificación real de identidad podría sustituirse por credenciales de prueba emitidas por una autoridad simulada.

Esta simplificación deberá declararse explícitamente, ya que limitar compras por wallet no equivale a limitar compras por persona.

## 21. Escenarios de demostración

### Escenario A: Venta concurrente

Múltiples compradores intentan adquirir entradas simultáneamente.

Se mide rendimiento, latencia, operaciones exitosas, errores y posibles cuellos de botella.

### Escenario B: Acaparamiento

Un revendedor intenta adquirir 100 entradas cuando el máximo autorizado es de cuatro.

Resultado esperado: rechazo de las operaciones que superen el límite.

### Escenario C: Evasión mediante múltiples wallets

Un usuario intenta utilizar diferentes wallets asociadas a una misma credencial.

Resultado esperado: aplicación del límite acumulado por identidad verificada.

### Escenario D: Reventa abusiva

Una entrada adquirida por USD 100 se intenta revender por USD 500.

Resultado esperado: rechazo por incumplimiento de las reglas comerciales.

### Escenario E: Reventa legítima

Una persona vende su entrada a otra por un importe autorizado.

Resultado esperado: intercambio seguro del pago y la titularidad.

### Escenario F: Fraude de acceso

Dos personas intentan utilizar la misma entrada.

Resultado esperado: únicamente se autoriza una utilización válida.

## 22. Indicadores de evaluación

Para determinar si la propuesta aporta valor tecnológico deberán medirse, como mínimo:

- Transacciones de compra exitosas por segundo.
- Latencia promedio y percentiles P95 y P99.
- Tasa de transacciones fallidas.
- Costos por emisión de entrada.
- Costos por transferencia y reventa.
- Rendimiento bajo concurrencia.
- Incidencia de contención de cuentas.
- Cantidad de ventas duplicadas.
- Capacidad de prevención del acaparamiento.
- Resistencia ante múltiples wallets.
- Tiempo de validación de acceso.
- Disponibilidad del sistema.
- Facilidad de utilización.
- Costo operativo por evento.

Las pruebas deberán compararse con una implementación equivalente basada en infraestructura convencional.

No se considera suficiente utilizar blockchain como argumento de superioridad sin evidencia experimental.

## 23. Competencia y diferenciación

NortePass competiría directa o indirectamente con plataformas como:

- Ticketmaster.
- StubHub.
- Eventbrite.
- SeatGeek.
- AXS.
- DICE.
- Plataformas de ticketing basadas en blockchain.
- Protocolos descentralizados de emisión de entradas.

La diferenciación propuesta consiste en integrar dentro de una misma infraestructura:

- Procesamiento concurrente.
- Distribución equitativa.
- Propiedad digital verificable.
- Prevención del acaparamiento.
- Reventa programable.
- Intercambios seguros.
- Validación de acceso.
- Experiencia de usuario accesible.

No se afirma que estas funcionalidades sean individualmente inéditas. La originalidad y diferenciación comercial deberán verificarse mediante un análisis actualizado de competidores.

## 24. Riesgos y desafíos

### Tecnológicos

- Contención de cuentas compartidas.
- Congestión de la red.
- Dependencia de proveedores RPC.
- Vulnerabilidades en programas blockchain.
- Recuperación de wallets.
- Integración entre pagos tradicionales y blockchain.
- Validación en entornos con conectividad limitada.
- Escalabilidad de mecanismos de identidad.

### Comerciales

- Dificultad para conseguir acuerdos con grandes organizadores.
- Competidores con posiciones consolidadas.
- Contratos de exclusividad.
- Costos de adquisición de clientes.
- Resistencia de consumidores a nuevas plataformas.
- Incentivos insuficientes para abandonar sistemas existentes.

### Legales

- Protección de datos personales.
- Regulación de activos digitales.
- Legislación sobre reventa de entradas.
- Derechos de consumidores.
- Regulación de pagos.
- Obligaciones fiscales.
- Políticas de devolución.
- Diferencias regulatorias entre países.

### Conceptuales

- Posibilidad de resolver determinadas problemáticas sin blockchain.
- Tensión entre propiedad descentralizada y restricciones comerciales.
- Imposibilidad de eliminar completamente los acuerdos clandestinos.
- Dificultad de garantizar una identidad única por persona.
- Ausencia de evidencia experimental sobre ventajas de rendimiento.
- Riesgo de que la solución agregue complejidad sin generar beneficios suficientes.

## 25. Visión a largo plazo

NortePass pretende posicionarse como una infraestructura global de ticketing que permita a organizadores y plataformas existentes incorporar mecanismos verificables de emisión, propiedad y comercialización de entradas.

La visión no depende necesariamente de convertirse en una aplicación que sustituya directamente a Ticketmaster.

También contempla convertirse en una capa de infraestructura especializada que pueda ser utilizada por múltiples plataformas, organizadores y mercados internacionales.

La misión consiste en facilitar un acceso más eficiente, equitativo y seguro a los eventos, reduciendo las oportunidades de especulación y fraude.
