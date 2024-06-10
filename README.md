# DdS-Ejercicios

# QMP2

## PseudoCodigo

    class Prenda
    {

        tipoPrenda tipo;
        trama trama;
        tipoMaterial material;
        color colorPrincipal;
        color colorSecundario;

    }

    class BorradorPrenda
    {

        tipoPrenda tipo;
        trama trama;
        tipoMaterial material;
        color colorPrincipal;
        color colorSecundario;

        contructor BorradorPrenda(tipo){
            validarNoNull(tipo);
            this.tipo = tipo;
            trama = trama.LISA;
        }

        void setTrama(trama){
            validarNoNull(trama);
            this.trama = trama;
        }
        void setMaterial(material){
            validarNoNull(material);
            this.material = material;
        }
        void setColorPrincipal(color){
            validarNoNull(color);
            this.colorPrincipal = tipo;
        }
        void setColorSecundario(color){
            this.colorSecundario = tipo;
        }

        void crearPrenda(){
            validarNoNull(trama);
            validarNoNull(material);
            validarNoNull(color);

            return new Prenda(tipo, material, colorPrincipal, colorSecundario, trama);
        }

    }

## Prosa

Esto es pensado despues de las correciones vistas en la clase. No con las ideas anteriores de MI resolución de la primera iteración.
La primera opcion con el tema de la trama, era crear una clase Material que tenga 2 enums, tipoMaterial y trama, estos 2 son enums para normalizar lo que quiero representar. (Esto se cambio despues de pensar el borrador, iba a ser más comodo).
Se creo una clase BorradorPrenda para tener la posibilidad de guardar una versión intermedia con sus respectivos setters, para poder ir modificandolo y tenerlo guardado. También se le agrega el metodo de crearPrenda a BorradorPrenda, que va a crear una Prenda con sus respectivas validaciones.
Como quiere que se decida primero el tipoPrenda cuando se cree una prenda, Borrador va a pedir primero que se pase en el constructor el tipoPrenda.
Para que se tome como por defecto la trama lisa si es que el usuario no la especifica, la puse por defecto en el constructor, y si el usuario quiere usar el setter para la trama, tiene la validacion que no puede ser null.

---

# QMP1

## PseudoCodigo

    class Atuendo{

        PrendaSuperior prendaSuperior;
        PrendaInferior prendaInferior;
        Calzado calzado;
        Accesorio accesorio = NULL;

    }

    class Usuario{

        Prenda prendasValidas[] = []
        Atuendo atuendos[] = []

        method cargarPrendaSuperior(ParteSuperior){
            prendasValidas.add(ParteSuperior);
        }
        method cargarPrendaInferior(PrendaInferior){
            prendasValidas.add(PrendaInferior);
        }
        method cargarCalzado(Calzado){
            prendasValidas.add(Calzado);
        }
        method cargarAccesorio(Accesorio){
            prendasValidas.add(Accesorio);
        }

        method armarAtuendo(Atuendo){
            atuendos.add(atuendo)
        }

    }

    class Prenda{

        material materialPrenda;
        color colorPrincipal;
        color colorSecundario = no_especifado:

    }

    enum color {
    rojo;
    azul;
    verde;
    no_especificado;
    etc;
    }

    enum material {
    lana;
    algodon;
    etc;
    }

    class ParteSuperior extends Prenda{

        tipoPrensaSuperior tipo;

    }

    enum tipoPrendaSuperior {
    remera;
    musculosa;
    etc;
    }

    class ParteInferior extends Prenda{

        tipoPrendaInferior tipo;

    }

    enum tipoPrendaInferior {
    pantalon;
    bermuda;
    etc;
    }

    class Calzado extends Prenda{

        tipoCalzado tipo;

    }

    enum tipoCalzado {
    gorra;
    piluso;
    etc;
    }

    class Accesorio extends Prenda{

        tipoAccesorio tipo;

    }

    enum tipoAccesorio {
    bufanda;
    anteojos;
    etc;
    }

## Prosa

Para cumplir los requerimientos actuales no segui el orden de los mismos por un tema de empezar con los que a mi parecer eran los que más me iban a marcar el ritmo del diseño.
Por ejemplo, con el requerimiento del material y el color, los marque con un enum ya que no me pide hacer mucho hincapíe en ellos, y en futuras iteraciones quizas tenga que rediseñarlo pero preferi mantener la simplicidad.
El mismo pensamiento se me ocurrio con el requerimiento del tipo de prenda, en un principio no tenia problema con poner un enum para todos los tipos de prenda sin que se vean raros con su criterio(por ejemplo que sea una remera y tenga criterio de parte inferior), pero hay un requerimiento que pide consistencia, asi que decidi hacer una herencia para cada criterio porque ya tengo fijos cuales pueden ser por el momento y que cada clase de su criterio tenga un enum para cada tipo de ese criterio. Con esto ya tengo la consistencia asegurada. Podria haber intentado un strategy con los tipos para cada uno de sus criterios, pero como no me pide nada por ahora, decidí no hacerlo pero ya ir pensando en la posibilidad ya que a como dice el principio del enunciado va a depender de muchas más cosas.
En la lista de requerimientos no me pide hacer un atuendo en si, pero por adelantarme un poco cree un constructor Atuendo. Que va a tener por lo menos una PrendaSuperior, una PrendaInferior y un Calzado minimo para considerarse tal. En el caso de que ese atuendo tenga un Accesorio o no, en el constructor ya esta inicialado como NULL, y si no se inicializa en el momento de crear un atuendo ya va a estar como NULL y no habria problema, para que el usuario decida si el atuendo va a tener un accesorio o no, esto es más para el futuro(extensibiilidad) un poco a contra parte de la simplicidad de los enums.
