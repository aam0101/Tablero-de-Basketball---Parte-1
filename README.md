## 📌 Objetivo del Proyecto

Crear una aplicación Android funcional para gestionar el marcador de un partido de baloncesto, aplicando:

- Views y Layouts (ConstraintLayout recomendado)
- Navegación con **Explicit Intents**
- **Data Binding** para evitar `findViewById`
- Gestión avanzada de recursos (`strings.xml`)
- Buenas prácticas de desarrollo Android
  

## 🏀 Funcionalidad de la App

La aplicación está compuesta por **dos pantallas principales**, tal como requiere la actividad:

### **1️⃣ MainActivity — Marcador en tiempo real**
Permite:
- Sumar **+1** o **+2** puntos a cada equipo  
- Restar **–1** (sin permitir valores negativos)  
- Restablecer marcador a **0–0**  
- Navegar a la pantalla de resultados  

### **2️⃣ ScoreActivity — Resultado final**
Muestra:
- Marcador final en formato **X – Y**
- Mensaje contextual:
  - 🟦 Gana el equipo local  
  - 🟥 Gana el equipo visitante  
  - 🟨 Empate  

Incluye la lógica de comparación y construcción del mensaje final.

---

## 🧩 Arquitectura General

La estructura del proyecto sigue un patrón simple y claro:

```
BasketballScoreApp/
 ├── app/
 │   ├── java/.../MainActivity.java
 │   ├── java/.../ScoreActivity.java
 │   ├── res/layout/activity_main.xml
 │   ├── res/layout/activity_score.xml
 │   ├── res/values/strings.xml
 │   └── AndroidManifest.xml
 └── README.md
```

---

## 🔗 Paso de Datos entre Activities

Para cumplir la actividad, los datos se envían con **Intent.putExtra()** utilizando **constantes**, como exige la rúbrica:

```java
public static final String EXTRA_LOCAL_SCORE = "LOCAL_SCORE";
public static final String EXTRA_VISITOR_SCORE = "VISITOR_SCORE";
```

Envió de datos:

```java
Intent intent = new Intent(MainActivity.this, ScoreActivity.class);
intent.putExtra(EXTRA_LOCAL_SCORE, localScore);
intent.putExtra(EXTRA_VISITOR_SCORE, visitorScore);
startActivity(intent);
```

Recepción en ScoreActivity:

```java
int local = getIntent().getIntExtra(MainActivity.EXTRA_LOCAL_SCORE, 0);
int visitor = getIntent().getIntExtra(MainActivity.EXTRA_VISITOR_SCORE, 0);
```

---

## 🧷 Data Binding — Implementación

El proyecto utiliza **Data Binding** para:

- Acceder a las vistas sin usar `findViewById`
- Hacer el código más limpio y seguro

Ejemplo:

```java
private ActivityMainBinding binding;

binding = ActivityMainBinding.inflate(getLayoutInflater());
setContentView(binding.getRoot());

binding.btnAddLocal1.setOnClickListener(v -> addPointsLocal(1));
```

---

## ✨ Diseño de Interfaces

- Se ha utilizado **ConstraintLayout**
- Todos los textos están en `strings.xml`
- Se han aplicado estilos coherentes para claridad y usabilidad

---

## 🔥 Lógica del Marcador

Implementación correcta de:

- Suma: +1 / +2  
- Resta: –1 (validación: nunca baja de **0**)  
- Reset del partido  
- Actualización en tiempo real  

---

## 🚀 Instrucciones de Ejecución

1. Clonar el repositorio:
```bash
git clone <https://github.com/aam0101/Tablero-de-Basketball---Parte-1>
```

2. Abrir en **Android Studio**

3. Sincronizar Gradle

4. Ejecutar en un emulador o dispositivo físico

---

## 📷 Capturas de Pantalla

MainActivity — Marcador en tiempo real
![Main Activity](resources/main_activity.png)



## 📚 Buenas Prácticas Aplicadas

✔ Nomenclatura clara  
✔ Código limpio y comentado  
✔ Recursos en strings.xml  
✔ Uso de constantes  
✔ Separación correcta de lógica y vista  

---

## 🧑‍💻 Autor

Proyecto desarrollado por Alberto Alcalde Montero 

