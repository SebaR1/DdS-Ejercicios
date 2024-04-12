# DdS-Ejercicios

# QMP1

# PseudoCodigo

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

class ParteInferior extends Prenda{

    tipoPrendaInferior tipo;

}

class Calzado extends Prenda{

    tipoCalzado tipo;

}

class Accesorio extends Prenda{

    tipoAccesorio tipo;

}

# Prosa

Primero perdón por la desprolijidad de la entrega.
Para cumplir los requerimientos actuales no segui el orden de los mismos por un tema de empezar con los que a mi parecer eran los que más me iban a marcar el ritmo del diseño.
Por ejemplo, con el requerimiento del material y el color, los marque con un enum ya que no me pide hacer mucho hincapíe en ellos, y en futuras iteraciones quizas tenga que rediseñarlo pero preferi mantener la simplicidad.
El mismo pensamiento se me ocurrio con el requerimiento del tipo de prenda, en un principio no tenia problema con poner un enum para todos los tipos de prenda sin que se vean raros con su criterio(por ejemplo que sea una remera y tenga criterio de parte inferior), pero hay un requerimiento que pide consistencia, asi que decidi hacer una herencia para cada criterio porque ya tengo fijos cuales pueden ser por el momento y que cada clase de su criterio tenga un enum para cada tipo de ese criterio. Con esto ya tengo la consistencia asegurada. Podria haber intentado un strategy con los tipos para cada uno de sus criterios, pero como no me pide nada por ahora, decidí no hacerlo pero ya ir pensando en la posibilidad ya que a como dice el principio del enunciado va a depender de muchas más cosas.
En la lista de requerimientos no me pide hacer un atuendo en si, pero por adelantarme un poco cree un constructor Atuendo. Que va a tener por lo menos una PrendaSuperior, una PrendaInferior y un Calzado minimo para considerarse tal. En el caso de que ese atuendo tenga un Accesorio o no, en el constructor ya esta inicialado como NULL, y si no se inicializa en el momento de crear un atuendo ya va a estar como NULL y no habria problema, para que el usuario decida si el atuendo va a tener un accesorio o no, esto es más para el futuro(extensibiilidad) un poco a contra parte de la simplicidad de los enums.
