# Plan de Ataque - Test Strategy

### **Objetivo**
El objetivo de esta prueba es verificar que el juego de "Adivina tu número" cumpla con los requisitos funcionales establecidos por el cliente, asegurando que los errores del código sean corregidos y que la aplicación funcione correctamente en todos los casos de prueba definidos.

### **Errores encontrados y soluciones**

1. **Error: Generación de número aleatorio incorrecta**  
   - **Descripción** El código original generaba un número aleatorio en el rango de 0 a 10, lo que generaba decimales en lugar de enteros entre 1 y 100.  
   - **Solución** Se corrigió utilizando `Math.floor(Math.random() * 100) + 1` para garantizar que el número aleatorio generado fuera un número entero entre 1 y 100.  
   - **Línea corregida**
     ```javascript
     let randomNumber = Math.floor(Math.random() * 100) + 1;
     ```

2. **Intentos Definidos Incorrectamente**
   - **Descripción** La variable `ATTEMPS` estaba definida con un valor de 5 en lugar de 10.
   - **Solución** Se corrigió la constante para reflejar correctamente los 10 intentos permitidos.
   - **Línea corregida**
     ```javascript
     const ATTEMPTS = 10;
     ```
3. **Error: Selección incorrecta del elemento `lowOrHi`**  
   - **Descripción** El código intentaba seleccionar un elemento con el nombre `lowOrHi` sin el prefijo `.` para una clase.  
   - **Solución** Se agregó el selector de clase (`.lowOrHi`) para seleccionar correctamente el elemento en el DOM.  
   - **Línea corregida**
     ```javascript
     const lowOrHi = document.querySelector('.lowOrHi');
     ```
4. **Comparación Incorrecta de Datos**
   - **Descripción** `userGuess` era un string, mientras que `randomNumber` era un número entero, lo que causaba fallos en la comparación estricta (`===`).
   - **Solución** Se convirtió `userGuess` a un número entero con `parseInt()`.
   - **Línea corregida**
     ```javascript
     if (parseInt(userGuess) === randomNumber) {
     ```

5. **Error: Uso incorrecto de `addEventListener`**  
   - **Descripción** La sintaxis de `addEventListener` contenía un error tipográfico en el nombre del método (`addeventListener` en lugar de `addEventListener`).  
   - **Solución** Se corrigió la sintaxis y se usó correctamente `addEventListener` con la letra `E` en mayúscula.  
   - **Línea corregida**
     ```javascript
     guessSubmit.addEventListener('click', checkGuess);
     ```

6. **Error: Mensajes incorrectos de victoria y derrota**  
   - **Descripción** Los mensajes de victoria y derrota estaban incorrectos, y se intercambiaban al ganar o perder.  
   - **Solución** Se corrigieron los mensajes para que al ganar se muestre "¡Felicitaciones!" y al perder "¡Perdiste!", con los colores correspondientes.  
   - **Líneas corregidas**
     ```javascript
     if(userGuess === randomNumber) {
       lastResult.textContent = '¡Felicitaciones! Adivinaste el número!';
     } else if(guessCount === ATTEMPTS) {
       lastResult.textContent = '¡Perdiste!';
     }
     ```

7. **Error: Generación del número aleatorio al reiniciar el juego**  
   - **Descripción** El número aleatorio generado al reiniciar el juego siempre era 1 debido a un error con `Math.random()`.  
   - **Solución**: Se corrigió para generar correctamente un número entre 1 y 100 utilizando `Math.floor(Math.random() * 100) + 1`.  
   - **Línea corregida**
     ```javascript
     randomNumber = Math.floor(Math.random() * 100) + 1;
     ```

8. **Error: El botón de reinicio no aparecía**  
   - **Descripción**: El botón de reinicio se creaba, pero no aparecía en la interfaz de usuario.  
   - **Solución** Se verificó que `setGameOver()` se ejecutara correctamente y que el botón de reinicio fuera añadido al DOM con `appendChild`.  
   - **Línea corregida**
     ```javascript
     document.body.appendChild(resetButton);
     ```

9. **Error: Validación de entrada del usuario (números enteros)**  
   - **Descripción** La entrada de usuario no validaba correctamente que se ingresaran solo números enteros, lo que podría permitir valores no deseados.  
   - **Solución**: Se agregó una validación para asegurarse de que el valor ingresado sea un número entero y mostrar una alerta si el valor es incorrecto.  
   - **Línea corregida**
     ```javascript
     if (isNaN(userGuess) || !Number.isInteger(userGuess)) {
       alert('Por favor, ingrese un número entero.');
       guessField.value = '';
       guessField.focus();
       return;
     }
     ```

10. **Error en setGameOver**
   - **Descripción**: Se usó incorrectamente `addeventListener` en lugar de `addEventListener`.
   - **Solución**: Se corrigió la sintaxis del evento.
   - **Línea corregida**:
     ```javascript
     resetButton.addEventListener('click', resetGame);
     ```

11. **Error en la Generación del Nuevo Número al Reiniciar el Juego**
   - **Descripción**: La generación del número no estaba correcta, ya que `Math.random()` por sí solo no genera valores en el rango adecuado.
   - **Solución** Se corrigió la generación del número aleatorio.
   - **Línea corregida**
     ```javascript
     randomNumber = Math.floor(Math.random() * 100) + 1;
     ```


### **Pruebas realizadas**
1. **Prueba de generación de números aleatorios**  
   - Verificación de que el número generado esté en el rango de 1 a 100 y que sea un número entero.

2. **Prueba de validación de entrada**  
   - Verificación de que solo se acepten números enteros. Si el valor es incorrecto, se muestra una alerta.

3. **Prueba de mensajes de victoria y derrota**  
   - Verificación de que los mensajes de victoria y derrota sean correctos y se muestren con el color correspondiente.

4. **Prueba de funcionalidad del botón de reinicio**  
   - Verificación de que el botón de reinicio aparezca al finalizar el juego y que el juego se reinicie correctamente.

### **Conclusiones**
- El juego ha sido corregido según los requisitos iniciales y las pruebas realizadas.
- Se han corregido todos los errores encontrados, y la funcionalidad ahora cumple con los requisitos especificados.
