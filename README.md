Facultad de Ciencias Exactas, Ingeniera y Agrimensura
Instituto Politecnico Superior
Técnico en Informática
Algoritmos y Estructuras de Datos Avanzadas
Práctica TAD - Inducción

1. Las listas finitas pueden especificarse como un TAD con los constructores:
• nil : Construye una lista vacı́a.
• cons: Agrega un elemento a la lista.
y las siguientes operaciones:
• head : Devuelve el primer elemento de la lista.
• tail : Devuelve todos los elementos de la lista menos el primero.
a) Dar una especificación algebraica del TAD listas finitas.
b) Dar una especificación tomando como modelo las secuencias.
c) Asumiendo que A es un tipo con igualdad, especificar una función inL : List A → A → Bool
tal que inL ls x = true si y sólo si x es un elemento de ls.
d) Especificar una función que elimina todas las ocurrencias de un elemento dado.

2. Dado el TAD pilas, con las siguientes operaciones:
• empty: Construye una pila inicialmente vacı́a.
• push: Agrega un elemento al tope de la pila.
• isEmpty: Devuelve verdadero si su argumento es una pila vacı́a, falso en caso contrario.
• top: Devuelve el elemento que se encuentra al tope de la pila.
• pop: Saca el elemento que se encuentra al tope de la pila.
Dar una especificación algebraica del TAD pilas y una especificación tomando como modelo las
secuencias.

3. Asumiendo que A es un tipo con igualdad, completar la siguiente definición del TAD conjunto.

a) Nombre de tipo: Conjunto
Usa: Bool

b) Operaciones:
tad Conjunto (A : Set)
vacio
: Conjunto A
insertar
: A → Conjunto A → Conjunto A
borrar
: A → Conjunto A → Conjunto A
esVacio
: Conjunto A → Bool
union
: Conjunto A → Conjunto A → Conjunto A
interseccion : Conjunto A → Conjunto A → Conjunto A
resta
: Conjunto A → Conjunto A → Conjunto A

c) Especificación algebraica.
insertar x (insertar x c) = insertar x c
insertar x (insertar y c) = insertar y (insertar x c)
...
¿Que pasarı́a si se agregase una función choose : Conjunto A → A, tal que choose (insertar x c) =
x ?

4.
El TAD priority queue es una cola en la cual cada elemento tiene asociado un valor que es su
prioridad (a dos elementos distintos le corresponden prioridades distintas). Los valores que definen
la prioridad de los elementos pertenecen a un conjunto ordenado. Las siguientes son las operaciones
soportadas por este TAD:
• vacia: Construye una priority queue vacı́a.
• poner : Agrega un elemento a una priority queue con una prioridad dada.
• primero: Devuelve el elemento con mayor prioridad de una priority queue.
• sacar : Elimina de una priority queue el elemento con mayor prioridad.
• esVacia: Determina si una priority queue es vacı́a.
• union: Une dos priority queues.
Dar una especificación algebraica del TAD priority queue y una especificación tomando como
modelo los conjuntos.

5. Demostrar que (uncurry zip) ◦ unzip = id , siendo:
zip
:: [a ] → [b ] → [(a, b)]
zip [ ] ys
= []
zip (x : xs) [ ]
= []
zip (x : xs) (y : ys) = (x , y) : zip xs ys
unzip
:: [(a, b, )] → ([a ], [b ])
unzip [ ]
= ([ ], [ ])
unzip ((x , y) : ps) = (x : xs, y : ys)
where (xs, ys) = unzip ps

6. Demostrar que sum xs 6 length xs ∗maxl xs, sabiendo que xs es una lista de números naturales
y que maxl y sum se definen
maxl [ ]
=0
maxl (x : xs) = x ‘max ‘ maxl xs
sum [ ]
=0
sum (x : xs) = x + sum xs

7. Dado el siguiente tipo de datos
data Arbol a = Hoja a | Nodo a (Arbol a) (Arbol a)
a) Dar el tipo y definir la función size que calcula la cantidad de elementos que contiene un
(Arbol a).
b) Demostrar la validez de la siguiente propiedad: ∀t ∈ (Arbol a).∃k ∈ N.size t = 2 k + 1
c) Dar el tipo y definir la función mirror que dado un árbol devuelve su árbol espejo.
d) Demostrar la validez de la siguiente propiedad: mirror ◦ mirror = id
e) Considerando las siguientes funciones:
hojas
:: Arbol a → Int
hojas (Hoja x )
=1
hojas (Nodo x t 1 t 2 ) = hojas t 1 + hojas t 2
altura
:: Arbol a → Int
altura (Hoja x )
=1
altura (Nodo x t 1 t 2 ) = 1 + (altura t 1 ‘max ‘ altura t 2 )
Demostrar que para todo árbol finito t se cumple que hojas t < 2 (altura t)

8. Dadas las siguientes definiciones:
data AGTree a = Node a [AGTree a ]
ponerProfs n (Node x xs) = Node n (map (ponerProfs (n + 1)) xs)
a) Definir una función alturaAGT que calcule la altura de un AGTree.
b) Definir una función maxAGT que dado un AGTree de enteros devuelva su mayor elemento.
c) Demostrar que alturaAGT = maxAGT ◦ ponerProfs 1

9. Dadas las siguientes definiciones
data Tree a = Leaf a | Node a (Tree a) (Tree a)
flatten (Leaf x )
= [x ]
flatten (Node x lt rt)
= flatten lt ++ [x ] ++ flatten rt
mapTree f (Leaf x )
= Leaf (f x )
mapTree f (Node x lt rt) = Node (f x ) (mapTree f lt) (mapTree f rt)
demostrar que map f ◦ flatten = flatten ◦ mapTree f

10. Dada la siguiente definición
join [ ]
= []
join (xs : xss) = xs +
+ join xss
demostrar

a) join = concat ◦ map id

b) join ◦ join = join ◦ map join

11. Dadas las funciones insert :: Ord a ⇒ a → Bin a → Bin a, que agrega un elemento a un
BST dado, y inorder :: Ord a ⇒ Bin a → [a ], que realiza un recorrido inorder sobre un BST,
dadas en clase de teorı́a, probar las siguientes propiedades sobre las funciones:

a) Si t es un BST, entonces insert x t es un BST.

b) Si t es un BST entonces inorder t es una lista ordenada.

12. Dar el principio de inducción estructural para el siguiente tipo de datos.
data F = Nil | One F | Two (Bool → F )
