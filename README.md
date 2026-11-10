# Modelo Relacional de Bases de Datos 17

## Descripción

Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para un sistema de gestión veterinaria, enfocado en el control de tutores, mascotas, consultas veterinarias, profesionales, vacunas y el registro de aplicación de vacunas.

---

## Estructura de Tablas y Atributos

### 1. Tutor

* **PK (Clave Primaria):** `id_DNI`
* **Atributos:**
* `nombre`
* `dirección`
* `teléfono`
* `apellido`



### 2. Mascota

* **PK (Clave Primaria):** `id_Hiatoria_clinica`
* **Atributos:**
* `nombre`
* `especie`
* `raza`
* `sexo`
* `fecha_nacimiento`


* **FK (Claves Foráneas):**
* `id_DNI` (asociado a la tabla Tutor)



### 3. Veterinario

* **PK (Clave Primaria):** `id_matricula_profesional`
* **Atributos:**
* `nombre`
* `teléfono`
* `especialidad_clinica`
* `apellido`



### 4. Consulta-Veterinaria

* **PK (Clave Primaria):** `id_Consulta`
* **Atributos:**
* `fecha`
* `motivo_consulta`
* `peso_actual`
* `temperatura`
* `diagnostico`


* **FK (Claves Foráneas):**
* `id_matricula_profesional` (asociado a la tabla Veterinario)
* `id_Historia_clinica` (asociado a la tabla Mascota)



### 5. Vacuna

* **PK (Clave Primaria):** `id_Codigo_vacuna`
* **Atributos:**
* `nombre_comercial`
* `laboratorio`
* `numero_de_lote`
* `descripción`



### 6. Aplicación-de-vacuna

* **PK (Clave Primaria):** `id_aplicación`
* **Atributos:**
* `fecha_de_aplicación`
* `horario`


* **FK (Claves Foráneas):**
* `id_Historia_clinica` (asociado a la tabla Mascota)
* `id_Codigo_vacuna` (asociado a la tabla Vacuna)



---

## Relaciones Principales

* **Tutor y Mascota:** Un tutor puede tener registradas una o varias mascotas vinculadas mediante su documento de identidad (`id_DNI`).
* **Mascota y Consulta-Veterinaria:** Las consultas médicas realizadas a los animales se registran asociando la historia clínica de la mascota (`id_Historia_clinica`).
* **Veterinario y Consulta-Veterinaria:** Cada consulta es atendida por un profesional veterinario identificado mediante su matrícula (`id_matricula_profesional`).
* **Mascota y Vacuna (Aplicación-de-vacuna):** El historial de inmunización o aplicación de vacunas se gestiona a través de la tabla intermedia `Aplicación-de-vacuna`, relacionando al paciente (`id_Historia_clinica`) con el insumo aplicado (`id_Codigo_vacuna`).
