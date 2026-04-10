# Lancha Robot V1 — Wiring Schedule

**Este documento lista CADA cable, hose y conexion fisica del robot.**  
Cada fila = un cable o manguera real. Sin flechas, sin diagramas cruzados.  
Leer fila por fila para cablear el robot completo.

---

## Como leer esta tabla

- **DE** = donde empieza el cable (componente + terminal)
- **A** = donde termina el cable (componente + terminal)
- **Tipo** = que tipo de cable o manguera es
- **Sale de la caja?** = indica si el cable pasa por un cable gland (sello impermeable en la pared de la caja)
- Todos los componentes electronicos viven DENTRO de la caja sellada, excepto: motores, cilindros, camara, y antenas

---

## CIRCUITO 1: Cadena de energia (12V)

Estos cables forman la cadena principal de energia. La corriente fluye en este orden exacto:
Bateria --> Switch --> Fusible --> Bus 12V --> todos los dispositivos de 12V.

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 1 | Bateria LiFePO4 (+) | Switch principal de encendido | Cable rojo, 14 AWG | No | El switch esta montado en la tapa de la caja, pero no sale de ella |
| 2 | Switch principal de encendido | Fusible 25A (entrada) | Cable rojo, 14 AWG | No | El switch corta toda la energia del robot |
| 3 | Fusible 25A (salida) | Bus 12V (terminal strip, riel positivo) | Cable rojo, 14 AWG | No | Si el fusible se quema, nada recibe energia |
| 4 | Bateria LiFePO4 (-) | Bus 12V (terminal strip, riel negativo / tierra) | Cable negro, 14 AWG | No | Tierra comun para todo el sistema |

---

## CIRCUITO 2: Bus 12V a dispositivos de 12V

Estos cables van del bus 12V (terminal strip) a cada dispositivo que necesita 12V.
Todos estos cables son INTERNOS a la caja sellada.

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 5 | Bus 12V (+) | ESC Izquierdo (cable rojo de entrada) | Cable rojo, 16 AWG | No | ESC convierte 12V DC a 3 fases para el motor |
| 6 | Bus 12V (-) | ESC Izquierdo (cable negro de entrada) | Cable negro, 16 AWG | No | |
| 7 | Bus 12V (+) | ESC Derecho (cable rojo de entrada) | Cable rojo, 16 AWG | No | ESC convierte 12V DC a 3 fases para el motor |
| 8 | Bus 12V (-) | ESC Derecho (cable negro de entrada) | Cable negro, 16 AWG | No | |
| 9 | Bus 12V (+) | Bomba hidraulica (+) | Cable rojo, 16 AWG | No | La bomba solo corre cuando se usa el brazo (~20% del tiempo) |
| 10 | Bus 12V (-) | Bomba hidraulica (-) | Cable negro, 16 AWG | No | |
| 11 | Bus 12V (+) | Solenoide V1 - Lift (+) | Cable rojo, 18 AWG | No | Valvula de brazo subir/bajar |
| 12 | Bus 12V (-) | Solenoide V1 - Lift (-) | Cable negro, 18 AWG | No | |
| 13 | Bus 12V (+) | Solenoide V2 - Rotate (+) | Cable rojo, 18 AWG | No | Valvula de brazo rotar izq/der |
| 14 | Bus 12V (-) | Solenoide V2 - Rotate (-) | Cable negro, 18 AWG | No | |
| 15 | Bus 12V (+) | Solenoide V3 - Gripper (+) | Cable rojo, 18 AWG | No | Valvula de pinza abrir/cerrar |
| 16 | Bus 12V (-) | Solenoide V3 - Gripper (-) | Cable negro, 18 AWG | No | |

---

## CIRCUITO 3: Convertidor 5V y dispositivos de 5V

El convertidor buck toma 12V del bus y lo baja a 5V para dispositivos que no soportan 12V.

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 17 | Bus 12V (+) | Buck converter (entrada +) | Cable rojo, 18 AWG | No | Entrada: 12V |
| 18 | Bus 12V (-) | Buck converter (entrada -) | Cable negro, 18 AWG | No | |
| 19 | Buck converter (salida 5V +) | Receptor RC (pin VCC / 5V) | Cable rojo, 22 AWG | No | Salida: 5V regulado |
| 20 | Buck converter (salida GND) | Receptor RC (pin GND) | Cable negro, 22 AWG | No | |
| 21 | Buck converter (salida 5V +) | Video TX VTX (pin VCC / 5V) | Cable rojo, 22 AWG | No | |
| 22 | Buck converter (salida GND) | Video TX VTX (pin GND) | Cable negro, 22 AWG | No | |

---

## CIRCUITO 4: Buzzer de voltaje bajo

El buzzer se conecta DIRECTO a la bateria (no pasa por el switch ni el fusible).
Siempre esta monitoreando. Suena fuerte cuando el voltaje baja demasiado.

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 23 | Bateria LiFePO4 (+) | Buzzer de voltaje (cable +) | Cable rojo, 22 AWG | No | Conectar ANTES del switch para que siempre monitoree |
| 24 | Bateria LiFePO4 (-) | Buzzer de voltaje (cable -) | Cable negro, 22 AWG | No | |

---

## CIRCUITO 5: Senales PWM (receptor RC a dispositivos)

Estos son cables DELGADOS de senal. Llevan pulsos PWM que le dicen a cada dispositivo que hacer.
PWM = Pulse Width Modulation (una senal simple de control, NO es energia).

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 25 | Receptor RC, salida CH1 | ESC Izquierdo (cable de senal, usualmente blanco) | Cable servo 3-pin (senal) | No | Controla velocidad y direccion del motor izquierdo |
| 26 | Receptor RC, salida CH2 | ESC Derecho (cable de senal, usualmente blanco) | Cable servo 3-pin (senal) | No | Controla velocidad y direccion del motor derecho |
| 27 | Receptor RC, salida CH3 | Relay/driver de Solenoide V1 (Lift) | Cable servo 3-pin (senal) | No | El relay amplifica la senal debil del receptor para activar la valvula solenoide |
| 28 | Receptor RC, salida CH4 | Relay/driver de Solenoide V2 (Rotate) | Cable servo 3-pin (senal) | No | Misma logica: receptor --> relay --> solenoide |
| 29 | Receptor RC, salida CH5 | Relay/driver de Solenoide V3 (Gripper) | Cable servo 3-pin (senal) | No | SWA toggle: una posicion = abrir, otra = cerrar |

---

## CIRCUITO 6: ESCs a motores de propulsion (SALEN DE LA CAJA)

Estos cables SALEN de la caja sellada a traves de cable glands impermeables.
Son cables de alta corriente (3 fases) que van a los motores en las pontones.

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 30 | ESC Izquierdo (cable fase A) | Motor Izquierdo (fase A) | Cable motor, 16 AWG | Si - Cable gland PG9 #1 | Los 3 cables de fase pasan por UN cable gland |
| 31 | ESC Izquierdo (cable fase B) | Motor Izquierdo (fase B) | Cable motor, 16 AWG | Si - Cable gland PG9 #1 | Rutear cables por dentro de los tubos del frame |
| 32 | ESC Izquierdo (cable fase C) | Motor Izquierdo (fase C) | Cable motor, 16 AWG | Si - Cable gland PG9 #1 | |
| 33 | ESC Derecho (cable fase A) | Motor Derecho (fase A) | Cable motor, 16 AWG | Si - Cable gland PG9 #2 | Los 3 cables de fase pasan por UN cable gland |
| 34 | ESC Derecho (cable fase B) | Motor Derecho (fase B) | Cable motor, 16 AWG | Si - Cable gland PG9 #2 | Rutear cables por dentro de los tubos del frame |
| 35 | ESC Derecho (cable fase C) | Motor Derecho (fase C) | Cable motor, 16 AWG | Si - Cable gland PG9 #2 | |

---

## CIRCUITO 7: Camara FPV (SALE DE LA CAJA)

La camara esta montada en el maste exterior. Necesita 5V de energia,
y envia su senal de video de regreso al VTX dentro de la caja.
Todo pasa por UN cable gland (cable con 3 conductores: 5V, GND, video).

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 36 | Buck converter (salida 5V +) | Camara FPV (pin VCC) | Cable rojo, 22 AWG | Si - Cable gland PG7 #3 | Los 3 hilos van juntos por un cable gland |
| 37 | Buck converter (salida GND) | Camara FPV (pin GND) | Cable negro, 22 AWG | Si - Cable gland PG7 #3 | |
| 38 | Camara FPV (pin VIDEO OUT) | Video TX VTX (pin VIDEO IN) | Cable amarillo, 22 AWG | Si - Cable gland PG7 #3 | Senal de video analogica de regreso al VTX |

---

## CIRCUITO 8: Antenas (SALEN DE LA CAJA)

Las antenas estan en el maste exterior para mejor alcance.
Cables coaxiales conectan cada antena a su dispositivo dentro de la caja.

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 39 | Receptor RC (conector de antena) | Antena RC 2.4GHz (en maste) | Cable coaxial delgado / cable de antena | Si - Cable gland PG7 #4 | Montar antena lo mas alto posible en el maste |
| 40 | Video TX VTX (conector SMA) | Antena VTX 5.8GHz Pagoda (en maste) | Cable coaxial SMA | Si - Cable gland PG7 #5 | Antena Pagoda o Cloverleaf para cobertura omnidireccional |

---

## CIRCUITO 9: Mangueras hidraulicas (SALEN DE LA CAJA)

Cada valvula solenoide tiene 2 mangueras que van a su cilindro en el brazo:
una para EXTENDER el cilindro, otra para RETRAER.
3 valvulas x 2 mangueras = 6 mangueras que salen de la caja.

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 41 | Valvula V1, puerto A (extender) | Cilindro 1 Lift, puerto extender | Manguera nylon 6mm | Si - Cable gland PG9 #6 | Manguera para SUBIR el brazo |
| 42 | Valvula V1, puerto B (retraer) | Cilindro 1 Lift, puerto retraer | Manguera nylon 6mm | Si - Cable gland PG9 #6 | Manguera para BAJAR el brazo |
| 43 | Valvula V2, puerto A (extender) | Cilindro 2 Rotate, puerto extender | Manguera nylon 6mm | Si - Cable gland PG9 #7 | Manguera para GIRAR brazo a un lado |
| 44 | Valvula V2, puerto B (retraer) | Cilindro 2 Rotate, puerto retraer | Manguera nylon 6mm | Si - Cable gland PG9 #7 | Manguera para GIRAR brazo al otro lado |
| 45 | Valvula V3, puerto A (extender) | Cilindro 3 Gripper, puerto extender | Manguera nylon 6mm | Si - Cable gland PG9 #8 | Manguera para CERRAR la pinza |
| 46 | Valvula V3, puerto B (retraer) | Cilindro 3 Gripper, puerto retraer | Manguera nylon 6mm | Si - Cable gland PG9 #8 | Manguera para ABRIR la pinza |

---

## CIRCUITO 10: Circuito hidraulico interno (dentro de la caja)

La bomba, el deposito, y las valvulas estan todos DENTRO de la caja.
Fluido hidraulico circula entre ellos por mangueras cortas internas.

| # | DE | A | Tipo | Sale de la caja? | Notas |
|---|-----|-----|------|:---:|-------|
| 47 | Deposito hidraulico (salida) | Bomba hidraulica (entrada / succion) | Manguera nylon 6mm, corta | No | La bomba succiona fluido del deposito |
| 48 | Bomba hidraulica (salida / presion) | Valvula V1 (puerto de presion P) | Manguera nylon 6mm, corta | No | Fluido presurizado a la valvula de lift |
| 49 | Bomba hidraulica (salida / presion) | Valvula V2 (puerto de presion P) | Manguera nylon 6mm, corta | No | Fluido presurizado a la valvula de rotacion |
| 50 | Bomba hidraulica (salida / presion) | Valvula V3 (puerto de presion P) | Manguera nylon 6mm, corta | No | Fluido presurizado a la valvula de gripper |
| 51 | Valvula V1 (puerto de retorno T) | Deposito hidraulico (retorno) | Manguera nylon 6mm, corta | No | Fluido regresa al deposito |
| 52 | Valvula V2 (puerto de retorno T) | Deposito hidraulico (retorno) | Manguera nylon 6mm, corta | No | |
| 53 | Valvula V3 (puerto de retorno T) | Deposito hidraulico (retorno) | Manguera nylon 6mm, corta | No | |

---

## ENLACES INALAMBRICOS (sin cables)

Estas no son conexiones fisicas — son senales de radio entre el operador y el robot.

| # | DE | A | Frecuencia | Alcance | Funcion |
|---|-----|-----|-----------|---------|---------|
| W1 | Transmisor RC FlySky FS-i6X (operador) | Antena RC 2.4GHz (en maste del robot) | 2.4 GHz | 1.5 - 2 km | Operador envia comandos de control al robot |
| W2 | Antena VTX 5.8GHz (en maste del robot) | Monitor/Goggles FPV (operador) | 5.8 GHz | 2+ km a 1W | Robot transmite video en vivo al operador |

---

## RESUMEN DE CABLE GLANDS

Inventario de todos los sellos impermeables en la pared de la caja:

| Gland # | Tamano | Que pasa por el | Destino |
|---------|--------|----------------|---------|
| 1 | PG9 | 3 cables de fase del motor izquierdo | Motor izquierdo (popa, ponton izq) |
| 2 | PG9 | 3 cables de fase del motor derecho | Motor derecho (popa, ponton der) |
| 3 | PG7 | 3 hilos de camara (5V, GND, video) | Camara FPV (en maste) |
| 4 | PG7 | Cable de antena RC | Antena RC 2.4GHz (en maste) |
| 5 | PG7 | Cable coaxial SMA de VTX | Antena VTX 5.8GHz (en maste) |
| 6 | PG9 | 2 mangueras hidraulicas (lift) | Cilindro 1 en brazo (subir/bajar) |
| 7 | PG9 | 2 mangueras hidraulicas (rotate) | Cilindro 2 en brazo (rotar) |
| 8 | PG9 | 2 mangueras hidraulicas (gripper) | Cilindro 3 en brazo (pinza) |
| **Total** | | **8 cable glands** | |

---

## LISTA DE COMPONENTES (referencia rapida)

### Dentro de la caja sellada
| Componente | Voltaje | Funcion |
|-----------|---------|---------|
| Bateria LiFePO4 12V 20-30Ah | 12V | Fuente de toda la energia |
| Switch de encendido (waterproof) | 12V | Apaga/enciende todo el robot |
| Fusible 25A | 12V | Proteccion contra corto circuito |
| Terminal strip (bus 12V) | 12V | Punto de distribucion para todos los 12V |
| Buck converter | 12V in, 5V out | Baja voltaje para receptor y VTX |
| Buzzer de voltaje | 12V | Alarma de bateria baja |
| Receptor RC FlySky FS-iA10B | 5V | Recibe comandos del operador |
| ESC Izquierdo 30A | 12V | Controla motor izquierdo |
| ESC Derecho 30A | 12V | Controla motor derecho |
| Video TX (VTX) 5.8GHz 1W | 5V | Transmite video al operador |
| Bomba hidraulica 12V DC | 12V | Presuriza fluido hidraulico |
| Deposito hidraulico 1-2L | N/A | Almacena fluido biodegradable |
| Solenoide V1 (Lift) | 12V | Controla cilindro de subir/bajar |
| Solenoide V2 (Rotate) | 12V | Controla cilindro de rotacion |
| Solenoide V3 (Gripper) | 12V | Controla cilindro de pinza |
| Relay board (si necesario) | 5V/12V | Amplifica senal RC para activar solenoides |

### Fuera de la caja (en el robot)
| Componente | Ubicacion | Funcion |
|-----------|-----------|---------|
| Motor Izquierdo 775 | Popa, ponton izquierdo (en pod sumergido) | Propulsion lado izquierdo |
| Motor Derecho 775 | Popa, ponton derecho (en pod sumergido) | Propulsion lado derecho |
| Cilindro 1 (Lift) | Brazo, articulacion del hombro | Sube y baja el brazo |
| Cilindro 2 (Rotate) | Brazo, base con palanca | Gira el brazo izq/der |
| Cilindro 3 (Gripper) | Brazo, mecanismo de pinza | Abre y cierra la pinza |
| Camara FPV 1200TVL | Maste frontal, apuntando al agua | Video en vivo para el operador |
| Antena RC 2.4GHz | Maste frontal, arriba | Recibe comandos del transmisor |
| Antena VTX 5.8GHz Pagoda | Maste frontal, arriba | Transmite video al monitor |

### Con el operador (en la orilla)
| Componente | Funcion |
|-----------|---------|
| Transmisor RC FlySky FS-i6X | Envia comandos al robot via 2.4GHz |
| Monitor FPV 7" o Goggles EV800D | Recibe video del robot via 5.8GHz |
