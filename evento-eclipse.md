# 🌑 Evento Especial: ECLIPSE

> *Sistema Copa de Hogwarts · Módulo de evento narrativo*

---

## Texto de presentación

> El cielo sobre el campo empieza a cambiar antes de que nadie lo note. Un
> borde oscuro muerde el sol, despacio, como si algo muy antiguo hubiera
> decidido que hoy no habrá luz de sobra para nadie. Las gradas murmuran,
> los profesores miran hacia arriba con más curiosidad que preocupación, y
> las antorchas del estadio empiezan a encenderse una a una, aunque todavía
> sea mediodía.
>
> Los magos más viejos lo llaman por su nombre desde hace siglos: **Eclipse**.
> Durante los minutos en que el disco solar desaparece, la magia ambiental
> del campo se vuelve inestable. La Quaffle es más difícil de seguir, las
> Bludgers reaccionan distinto, y hasta la Snitch Dorada parece disfrutar
> del caos, ocultándose en las sombras que el sol ya no puede deshacer.
>
> Ningún equipo elige jugar un partido de Eclipse. Simplemente les toca.
> Y cada vez que alguien lanza el dado, no importa cuán bueno sea el plan
> trazado en el vestuario: el cielo también tiene voto — y nadie sabe qué
> forma va a tomar hasta que ya es tarde.

---

## 1. Qué es el Eclipse

El **Eclipse** es un evento especial que puede estar activo durante todo
el partido, o durante las rondas que el organizador determine (por
clima, calendario mágico, evento de trama, etc.). Mientras está activo,
**cada jugador que tira su propio dado** corre, en esa misma tirada, el
riesgo de que el Eclipse le juegue en contra.

Lo importante: **el Eclipse no reemplaza al dado ni agrega una tirada
extra**. El resultado del d20 sigue decidiendo el éxito o fracaso de la
acción como siempre — y ese mismo número es el que determina, además, si
el Eclipse se activa sobre esa jugada en particular.

---

## 2. Mecánica de activación (aleatoria, no exacta)

Se definen de antemano **6 números "Eclipse"** dentro del rango del d20
(6/20 = 30%), elegidos sin un patrón evidente para que la tirada no se
sienta predecible:

> **Números Eclipse: 3, 7, 10, 13, 16, 19**

Cada vez que un jugador tira su dado durante el Eclipse:

1. Resuelve su acción con el resultado obtenido, exactamente como
   siempre (éxito o fracaso según la dificultad correspondiente).
2. Si ese resultado **es uno de los números Eclipse**, se dispara un
   efecto de Eclipse: el código del dado hace un segundo sorteo interno
   y elige **uno al azar entre los cinco de la lista** (tabla abajo) —
   no importa quién tiró ni qué estaba haciendo, es puro azar sobre
   azar, resuelto en el mismo momento de la tirada.
3. Si el resultado **no** es uno de esos números (el 70% restante), no
   pasa nada más — la jugada se resuelve con total normalidad.

No hace falta llevar la cuenta de cuántas veces salió ni forzar que se
cumpla el porcentaje en cada partido: al ser 6 números fijos sobre 20,
el ~30% surge solo, tirada tras tirada, de forma orgánica y sin cálculos
en el momento.

> 💡 *Cómo elegir el efecto al azar:* se resuelve directamente en el
> código del dado del sitio. Cuando el resultado del d20 cae en uno de
> los números Eclipse, el propio script hace un segundo `randomize`
> (por ejemplo `Math.floor(Math.random()*5)`) para determinar cuál de
> los 5 efectos de la tabla se muestra. No requiere ningún dado físico
> aparte ni que nadie elija nada a mano — todo sale de la misma tirada
> en pantalla.

---

## 3. Tabla de efectos de Eclipse

Cuando se dispara el Eclipse, el efecto que toca es uno cualquiera de
estos cinco, sorteado al azar (no se filtra por contexto ni se elige el
que "tenga más sentido" en ese momento):

| # | Nombre narrativo | Efecto mecánico |
|---|---|---|
| 1 | **Oscuridad total** | **Su equipo no puede arriesgar la ubicación** de la Snitch en esta ronda (no se resuelve intento de captura, solo se acerca/aleja). |
| 2 | **Ráfagas heladas** | Si la tirada corresponde a un **turno impar** de la ronda (turno 1 o turno 3): el jugador **pierde el turno**, pese al resultado, por perder el equilibrio sobre la escoba. |
| 3 | **Bludger Encantada** | Si la tirada era una **acción defensiva** (Golpeador defendiendo, Guardián atajando): el jugador **pierde el turno**, el objeto encantado reacciona de forma imprevisible y anula la jugada. |
| 4 | **Visibilidad reducida** | Si la tirada era una **acción ofensiva** (anotar con la Quaffle, avanzar en ataque): el jugador **pierde el turno**, no logra reaccionar a tiempo pese al resultado del dado. |
| 5 | **Criatura mágica enloquece** | **No hay pista de Snitch esta ronda**, para ninguno de los dos equipos, sin importar quién haya tirado. |

### Qué pasa si el efecto sorteado "no aplica"

Como el efecto sale al azar y no se elige según lo que el jugador
estaba haciendo, puede pasar que toque, por ejemplo, el efecto **#2**
(turno impar) en una tirada que en realidad correspondía a un turno
par, o el efecto **#1** (Buscador) cuando quien tiró no es Buscador.
Cuando eso ocurra:

- **Si la condición del efecto no se cumple, ese efecto simplemente no
  tiene consecuencia esa vez** — el Eclipse "intentó" algo pero no
  encontró dónde morder. La jugada queda resuelta con normalidad, más
  allá del resultado del dado.
- Los efectos **#1** (sin arriesgar ubicación de la Snitch) y **#5**
  (sin pista de Snitch esta ronda) **siempre** tienen consecuencia, sin
  importar el contexto de la tirada.

Esto es intencional: el Eclipse es errático por naturaleza, así que a
veces "falla" sobre la jugada equivocada — y eso también forma parte de
la sensación de caos que se busca transmitir.

---

## 4. Resumen rápido

```
¿Eclipse activo? → Sí
  ↓
Jugador tira su d20 → resuelve su acción con total normalidad
  ↓
¿El número que salió es 3, 7, 10, 13, 16 o 19?
  ↓
  No (70%) → nada más ocurre, la jugada queda resuelta como siempre
  Sí (30%) → se sortea al azar 1 de los 5 efectos de la tabla
              ↓
              ¿La condición del efecto sorteado coincide con la jugada?
              ↓
              Sí → se aplica el efecto
              No → no pasa nada extra esta vez (excepto los efectos #1
                   y #5, que siempre se aplican)
```

---

## 5. Guía visual: cómo debería modificarse la luna por el Eclipse de Sangre

Si el evento narrativo escala a un **Eclipse de Sangre** (una variante
más intensa y de mayor peso dramático — por ejemplo, para una final o un
partido de trama), la ambientación visual del sitio/estadio debería
acompañar ese cambio. Guía de dirección de arte:

### Paleta de color
Usar y extender los tonos que ya existen en el sistema visual del
torneo, virando hacia rojos más profundos:

| Uso | Color base existente | Ajuste para Eclipse de Sangre |
|---|---|---|
| Fondo del cielo | `--ink` (`#0a0b0f`) | Oscurecer levemente y agregar un tinte rojo muy sutil de fondo (no saturado) |
| Luna / halo | — (nuevo elemento) | Disco en tonos `--scarlet-bright` (`#a3232f`) a `--bronze` (`#7c5a2e`) en el borde, con centro casi negro |
| Corona / resplandor | `--gold-light` (`#f0d488`) | Sustituir por un resplandor rojo-ámbar tenue, mucho más apagado que el dorado habitual — el oro debe sentirse "ausente" durante el evento |
| Antorchas / velas | `.candle` existente | Mantener el fuego dorado como único punto de luz cálida "normal" — el contraste con el cielo rojizo refuerza la sensación de anomalía |

### Fases sugeridas (progresión narrativa/visual)
1. **Penumbra inicial** — el cielo se oscurece gradualmente, apenas
   perceptible; el dorado del sitio sigue dominante.
2. **Totalidad** — el disco queda completamente oculto; el fondo pasa a
   negro casi total, se encienden más antorchas/velas de las habituales.
3. **Luna de Sangre** — en el momento de mayor oscuridad, el borde lunar
   se enciende en un rojo apagado (no un rojo vivo/saturado — debe leerse
   "ominoso", no "alarma"). Este es el pico visual del evento.
4. **Retorno** — la luz dorada habitual vuelve a filtrarse desde los
   bordes, el rojo se retira primero del centro hacia afuera.

### Recomendaciones de forma
- La luna/eclipse **no debería tener un contorno perfecto ni brillo
  uniforme**: conviene un borde ligeramente irregular o con textura
  (como un grabado antiguo), coherente con la estética de pergamino y
  grabados del resto del sitio.
- Evitar rojos saturados tipo "alerta" (`#ff0000` o similares) — se
  rompe el tono medieval/mágico del torneo. El rojo debe sentirse
  cercano a `--scarlet` / `--scarlet-bright`, ya usados en el sitio para
  Gryffindor y acentos dramáticos.
- Si se anima, un parpadeo lento y sutil (similar al `flicker` de las
  velas, pero mucho más lento, en el orden de 6–10s por ciclo) ayuda a
  que la luna se sienta "viva" sin resultar una distracción del
  contenido del reglamento.
- Mantener la Snitch dorada visualmente intacta durante el evento — su
  brillo dorado, en contraste con el cielo rojo, refuerza narrativamente
  por qué es tan difícil de encontrar durante el Eclipse.

### Sonido/ambientación (si aplica en otros formatos, ej. narración en vivo)
- Silencio de multitud momentáneo al iniciar la totalidad.
- Sonido de viento más presente cuando sale sorteado "Ráfagas heladas"
  (efecto #2), reforzando por qué se pierde el equilibrio en esos
  turnos.

---

*Documento de referencia. No requiere cambios en el reglamento base del
torneo — el Eclipse es un módulo opcional que se activa por ronda o por
partido, y se resuelve tirada por tirada.*
