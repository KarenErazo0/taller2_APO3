```
package umariana.taller2;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.Scanner;
import mundo.Producto;


//se crea la clase con dos variables privadas

public class Taller2 {
    private  ArrayList<Producto> misProductos;
    private  Scanner lector;

    public Taller2() {

//nuevo contenedor vacio

        misProductos = new ArrayList<>();
        lector = new Scanner(System.in);
    }


//metodo para mostrar el menu de opciones
    public void mostrarMenu() {
        boolean activo = true;

//crear un ciclo para mantener el menu activo hasta finalizar

        do {
            System.out.println("----BIENVENIDO----");
            System.out.println("1. Agregar Producto\n2. Mostrar Inventario\n3. Mostrar Inventario Organizado\n4. Eliminar Producto\n5. Salir");
            int opcion = lector.nextInt();
            switch (opcion) {
                                case 1:

//llamar metodo para agregar un producto

                    agregarProducto();
                    break;

                case 2:
//Condicional para verificar si hay o no productos agregados
                    if (misProductos.size() == 0) {
                        System.out.println("No hay productos agregados.");
                    } else {
//llamar metodo para mostrar los productos
                        mostrarProductos();
                    }
                    break;
                case 3:
//Condicional para verificar si hay o no productos agregados
                    if (misProductos.size() == 0) {
                        System.out.println("No hay productos agregados.");
                    } else {
//llamar metodo para enlistar productos
                        listarProductos();
                    }
                    break;

                case 4:
//Condicional para verificar si hay o no productos agregados
                    if(misProductos.size()==0){
                        System.out.println("No hay productos agregados");
                    } else {
//llamar metodo para eliminar un producto
                    eliminarProducto();
                    }
                    break;
                case 5:
//establecer variable para terminar el ciclo
                    activo = false;
                    System.out.println("Programa terminado");
                    break;
                default:
// mensaje de error si se ingresa una opcion incorrecta
                    System.out.println("opcion no valida");
            }
        } while (activo);
    }

    public void agregarProducto() {
        
//metodo que permite agregar un nuevo producto
System.out.println("====AGREGAR PRODUCTO====");
        lector.nextLine();

//solicitar el ingreso sobre datos del producto
        System.out.println("Ingrese el nombre del producto");
        String nombre = lector.nextLine();

        System.out.println("Ingrese el precio del producto");
        double precio = lector.nextDouble();

        System.out.println("Ingrese la cantidad del producto");
        int cantidad = lector.nextInt();

        System.out.println("Ingrese el Id del producto");
        int idProducto = lector.nextInt();

        System.out.println("Producto agregado correctamente");
        //Cumplimiento de los parametros de la prioridad
        // Creacion del objeto y llenar la informacion
        Producto nuevoProducto = new Producto(nombre, precio, cantidad, idProducto);

        misProductos.add(nuevoProducto);
    }


//metodo para mostrar los productos agregados
    public void mostrarProductos() {
        System.out.println("====PRODUCTOS REGISTRADOS====");
//ciclo para mostrar los detalles del producto utilizando getters
        for(Producto p: misProductos){
            System.out.println("Nombre: "+p.getNombre());
            System.out.println("Precio: "+p.getPrecio());
            System.out.println("Cantidad: "+p.getCantidad());
            System.out.println("ID:" +p.getIdProducto());
            System.out.println("==================");
        }
    }


//metodo para ordenar los prductos de manera ascendente segun su cantidad
    public void listarProductos() {

//bucles aninados para comparar la cantidad de cada par de productos
        for (int i=0; i<misProductos.size()-1;i++){
            for(int j=i+1; j<misProductos.size();j++){
                Producto producto1 = misProductos.get(i);
                Producto producto2 = misProductos.get(j);
                if(producto1.getCantidad()>producto2.getCantidad()){
                    misProductos.set(i, producto2);
                    misProductos.set(j, producto1);
                }
            }
        }

//bucle para imprimir los detalles del producto utilizando los getters
        for (Producto p : misProductos) {
            System.out.println(" Nombre: "+p.getNombre()+ " \n Cantidad: " +p.getCantidad()+ " \n Precio: " + p.getPrecio()+"\nID:"+p.getIdProducto());
            System.out.println("======================================");
        }
    }

//metodo para eliminar un producto proporcionando su id
    public void eliminarProducto() {
        System.out.println("Digite el Id del producto que quiere eliminar");
        int id = lector.nextInt();
//recorrer la lista de misProductos para verificar el id del producto
        Iterator<Producto> it = misProductos.iterator();
        while (it.hasNext()){
            Producto p = it.next();
//si el ID coincide se elimina el producto usando remove()
            if(p.getIdProducto() == id){
                it.remove();
                System.out.println("Producto con id "+id+" ha sido eliminado");
            }else{

//mostrar error si no se encuentra ningun producto con el ID
                System.out.println("No se encontro ningun producto con el ID "+ id);
            }
        }
    }

    public static void main(String[] args) {
        Taller2 organizador = new Taller2();
        organizador.mostrarMenu();
    }
}
```
