```
package mundo;

/**
 *
 * @author KAREN ERAZO
 */
public class Producto {
    
    private String nombre;
    private double precio;
    private int cantidad;
    private int idProducto;

    public Producto() {
    }

    public Producto(String nombre, double precio, int cantidad, int idProducto) {
        this.nombre = nombre;
        this.precio = precio;
        this.cantidad = cantidad;
        this.idProducto = idProducto;
    }


    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public double getPrecio() {
        return precio;
    }

    public void setPrecio(double precio) {
        this.precio = precio;
    }

    public int getCantidad() {
        return cantidad;
    }

    public void setCantidad(int cantidad) {
        this.cantidad = cantidad;
    }

    public int getIdProducto() {
        return idProducto;
    }

    public void setIdProducto(int idProducto) {
        this.idProducto = idProducto;
    }
    
}
```
