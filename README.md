# 🔮 SPELLSCRIMS – Documento Maestro del Producto (v1.0)
**Plataforma Social Competitiva + Torneos Simples para League of Legends**

---

## 1. VISIÓN DEL PRODUCTO

**SPELLSCRIMS** es la plataforma donde los jugadores de League of Legends pueden encontrar duo, reclutar personas para su equipo de Flex y organizar scrims rápidamente.

El objetivo es resolver los tres dolores más grandes del jugador amateur en LATAM:

- ❌ "No tengo duo."
- ❌ "No encuentro equipo serio para Flex."
- ❌ "No tengo con quién hacer scrims."

SPELLSCRIMS crea un espacio donde los jugadores pueden:

- ✔ Conectarse entre sí de forma rápida y eficiente
- ✔ Armar equipos de 5 sin complicaciones
- ✔ Coordinar scrims con otros equipos
- ✔ Crear torneos simples completamente gratis

Todo desde una plataforma ligera, clara, directa y optimizada para que el jugador encuentre personas en **menos de 2 minutos**.

---

## 2. OBJETIVO DEL MVP

El MVP inicial de SPELLSCRIMS debe permitir:

### 1) Crear un perfil competitivo simple
- Nickname
- Rol principal
- Rol secundario
- División actual
- Horarios de juego
- Campeones más usados
- Servidor (LAN / LAS)
- Modalidades disponibles:
  - DuoQ
  - Flex
  - Scrims

### 2) Buscar jugadores
**Filtros:**
- Rol
- División
- Horario
- Modalidad
- Servidor

### 3) Crear y gestionar equipos simples
- Crear equipo
- Añadir miembros por invitación
- Publicar roles faltantes
- Recibir postulaciones

### 4) Crear torneos simples (solo gratuitos)
- Crear torneo con formulario básico
- Inscripciones abiertas
- Registro de equipos
- Bracket generado automáticamente
- Actualización manual de resultados

Este MVP está diseñado para lanzar la plataforma en producción en **menos de 4 meses** de desarrollo individual.

---

## 3. ALCANCE DEL MVP

### ✔ INCLUIDO

**Perfiles simples**
- 6–8 campos
- Enfocado en rol, elo y horario
- Link a Discord para contacto

**Buscador de jugadores**
- DuoQ
- Equipos para Flex
- Scrims de 5v5
- Filtros mínimos y efectivos

**Equipos básicos**
- Nombre
- Roles ocupados
- Roles faltantes
- Server
- Lista de miembros
- Botón "postularse"

**Torneos gratis (simples)**
- Registro de equipos
- Bracket simple
- Gestión manual del avance

**Autenticación**
- Registro / Login
- Validación de email

### ❌ NO INCLUIDO (ahora)
- Chat interno
- IA de emparejamiento
- Torneos de pago
- Integración con Riot API
- Estadísticas automáticas
- Scrims automáticas con código de lobby
- App móvil
- Premium

---

## 4. ROLES DE USUARIO

### Jugador
- Crear perfil
- Buscar duo / equipo / scrims
- Unirse a un equipo
- Registrarse en torneos

### Líder de equipo
- Crear equipo
- Publicar roles faltantes
- Gestionar roster

### Organizador
- Crear torneo
- Gestionar bracket

---

## 5. FLUJOS PRINCIPALES DE USUARIO

### 1. Crear perfil
1. Registro → Login
2. Completar:
   - Nick
   - Elo
   - Roles
   - Servidor
   - Horarios
   - Campeones
   - Modalidades
3. Perfil visible en búsquedas

### 2. Buscar duo
1. Ingresar a "Buscar Duo"
2. Filtrar por:
   - Rol
   - Elo
   - Horario
   - Servidor
3. Ver tarjeta de jugador
4. Clic en "Ver Discord"
5. Contacto directo

### 3. Buscar equipo para Flex
1. "Buscar Equipo"
2. Ver equipos
3. Filtrar roles faltantes
4. Postularse

### 4. Crear equipo
1. Crear equipo
2. Definir roles ocupados
3. Publicar roles faltantes
4. Recibir postulaciones

### 5. Crear torneo
1. Formulario simple
2. Abrir inscripciones
3. Generar bracket
4. Actualizar resultados manualmente

---

## 6. LISTA COMPLETA DE FEATURES DEL MVP

### ✔ Perfiles
- Rol Main
- Rol Secondary
- División
- Horarios
- Campeones
- Servidor
- Modalidad (Duo, Flex, Scrim)
- Link a Discord

### ✔ Búsqueda
**Filtros esenciales:**
- Rol
- Elo
- Modalidad
- Servidor
- Resultados por tarjeta

### ✔ Equipos
- Crear equipo
- Registrar miembros
- Editar roles
- Roles faltantes
- Publicación automática en "Busco Jugador"

### ✔ Torneos simples
- Crear torneo
- Registro de equipos
- Bracket automático
- Estado del torneo
- Gestión manual de avance

### ✔ Autenticación
- Registro
- Login
- Logout
- Recuperación de contraseña

---

## 7. MODELOS DE DATOS (DEFINITIVOS)

### User
```
userId
email
passwordHash
username
discordLink
createdAt
```

### PlayerProfile
```
profileId
userId
roleMain
roleSecondary
rank
server
champions[]
availability
modes[] // Duo, Flex, Scrim
createdAt
```

### Team
```
teamId
ownerId
name
server
members[] // userIds
rolesNeeded[] // ["TOP", "ADC"]
createdAt
```

### Tournament
```
tournamentId
name
description
maxTeams
teamsRegistered[]
bracket[]
status
createdAt
```

---

## 8. ARQUITECTURA RECOMENDADA

### Frontend – Angular
- Componentes ligeros
- Diseño limpio y rápido
- S3 + CloudFront para despliegue

### Backend – Java + Quarkus (Lambdas)
**Microservicios independientes:**
- Auth
- Profiles
- Teams
- Players
- Tournaments

### Base de Datos – DynamoDB
**Tablas:**
- Users
- Profiles
- Teams
- Tournaments

### Infraestructura – AWS
- Lambda
- API Gateway
- DynamoDB
- S3
- CloudFront
- SES (emails)
- Cognito (opcional para login simplificado)

---

## 9. ROADMAP DE LANZAMIENTO (12–14 semanas)

### FASE 1 – Perfiles + Auth (3 semanas)
- Login
- Register
- Completar perfil
- Mostrar perfiles

### FASE 2 – Búsqueda de jugadores (3 semanas)
- Listado
- Filtros
- Tarjetas

### FASE 3 – Equipos básicos (2–3 semanas)
- Crear equipo
- Roles faltantes
- Postulaciones

### FASE 4 – Torneos simples (4 semanas)
- Crear torneo
- Registrar equipos
- Bracket automático

### FASE 5 – Optimización final (1–2 semanas)
- Corrección de bugs
- UI Cleanup
- Mejoras de usabilidad

---

## 10. OBJETIVO FINAL

Lanzar **SPELLSCRIMS** como la plataforma más simple y efectiva para conectar jugadores competitivos de LoL en LATAM.

El MVP permite escalar a futuro hacia:
- Scrims automáticas
- IA de emparejamiento
- Torneos premium
- Equipos persistentes con estadísticas
- App móvil
- Notificaciones y chat interno
