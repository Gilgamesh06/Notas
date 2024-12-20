# Tablas

* Las tablas nos permiten tabular datos, las etiquetas para dibujar una tablas son:

    * **table** Define la tabla en si misma.
    * **tr** Define las filas (table row) de la tabla.
    * **td** Define las celdas (table data) dentro de las filas, lo que a su vez formara las columnas.
    * **th** Define las cledas de cabecera (table header) dentro de la primera fila de la tabla, suele ser la fila de titulos de nuestra tabla.
    
```html
<table border="1">
  <tr>
    <th>Ciudad</th>
    <th>País</th>
    <th>Continente</th>
  </tr>
  <tr>
    <td>Ciudad de México</td>
    <td>México</td>
    <td>América</td>
  </tr>
  <tr>
    <td>Tokyo</td>
    <td>Japón</td>
    <td>Asia</td>
  </tr>
  <tr>
    <td>Reikiavik</td>
    <td>Islandia</td>
    <td>Europa</td>
  </tr>
</table>
```