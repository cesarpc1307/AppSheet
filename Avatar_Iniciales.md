
# 🧩 Iniciales en AppSheet usando ui-avatars.com

Este fragmento de código permite generar dinámicamente una imagen de avatar en **AppSheet**  
basado en las iniciales del campo del nombre del usuario (o de quien se desee), utilizando el servicio gratuito de https://ui-avatars.com.

Ideal para apps que requieren mostrar una imagen de usuario sin necesidad de subir fotos reales.

---

📌 Configuración en AppSheet

- Tipo de campo: Virtual Column  
- Tipo de dato: Image

### 🧪 Fórmula en AppSheet

```appsheet
CONCATENATE(
  "https://ui-avatars.com/api/?name=",
  ENCODEURL(LEFT([Nombre_Completo], 1)),
  ENCODEURL(LEFT(INDEX(SPLIT([Nombre_Completo], " "), 2), 1)),
  "&background=CCCCCC&color=000000&size=128"
)
```

---

🔍 Explicación del código

1. "https://ui-avatars.com/api/?name=" → Base del servicio que genera el avatar.  
2. ENCODEURL(LEFT([Nombre_Completo], 1)) → Extrae la primera letra del nombre completo.  
3. ENCODEURL(LEFT(INDEX(SPLIT([Nombre_Completo], " "), 2), 1)) → Extrae la primera letra del segundo nombre o apellido.  
4. "&background=CCCCCC&color=000000&size=128" → Personalización del avatar:
   - Fondo: Gris claro (CCCCCC)
   - Texto: Negro (000000)
   - Tamaño: 128px

---

🎯 Ejemplo

Si el campo [Nombre_Completo] es:

César Pineda

La fórmula generará un enlace como:

https://ui-avatars.com/api/?name=C+P&background=CCCCCC&color=000000&size=128

Mostrará una imagen con las iniciales "C P".

---

📝 Notas adicionales

- Puedes cambiar los colores con los parámetros background y color.  
- Si el nombre tiene más de dos palabras, puedes ajustar la fórmula para mostrar otros elementos (como primer nombre + primer apellido).  
- La imagen se genera desde la nube, por lo que no ocupa espacio en tu app.  
- Esta URL puede usarse directamente en otros campos tipo imagen.  

---
Espero les sirva.
