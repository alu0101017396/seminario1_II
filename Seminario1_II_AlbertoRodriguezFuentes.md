## Mundos virtuales. Introducción a la programación de gráficos 3D.
Alberto Rodríguez Fuentes
1.  Qué funciones se pueden usar en los scripts de Unity para llevar a cabo traslaciones, rotaciones y escalados.
	Para las translaciones se puede usar: ``transform.Translate(float x, float y, float z); ``
Para las rotaciones: 
``Transform.Rotate(Vector3 axis, float angle, Space relativeTo = Space.Self); ``
Y para los escalados: 
``transform.localScale()``
2.  ¿Cómo duplicarías el tamaño de un objeto en en un script?.
	Lo duplicaria poniendo ``transform.localScale = new vector_(2, 2, 2);``
3.  Cómo situarías un objeto en la posición (3,5,1.)
	Lo situaría utilizando la linea de código ``transform.position = new  Vector3 (3, 5, 1);``
4.  Como trasladarías 3 metros en cada uno de los ejes y luego lo rotas 30º alrededor del eje Y?
	Primero usaría la línea ``transform.position += new  Vector3(3, 3, 3); ``para mover el objeto y luego usaría ``transform.Rotate(0.0f, 30.0f, 0.0f, Space.Self);`` para que rotara sobre si mismo.
5.  Como rotarías un objeto sobre el eje (1,1,1).
	Lo rotaría ``
transform.Rotate(0, yAmount, 0, Space.Self);
``
6.  Rota un objeto alrededor del eje Y 30ª y desplázalo 3 metros en cada uno de los ejes. ¿Obtendrías el mismo resultado que en 4?
	No porque se desplazaria en los ejes dados por la rotación.
7.  Como puedes obtener la distancia al plano cerca del volumen de vista desde la cámara.
	Lo puedes ver en el inspector de la cámara,  en el apartado de Clipping  Planes.
8.  Como puedes aumentar el ángulo de la cámara
	Aumentando el Field of View de esta en el inspector.
9.  Qué efecto tiene disminuir el ángulo de la cámara.
	Tiene el efecto de hacer zoom al centro del plano.
10.  Configura un volumen de vista que recorte objetos de la escena.
![Gif](https://github.com/alu0101017396/seminario1_II_gif/blob/main/9.gif)
11.  Como puedes realizar la proyección al espacio 2D.
	Cambiando la proyección de Perspectiva a Ortografica.
12.  Especifica la rotación de los apartados 4 y 6 con la utilidad quaternion.  
	Si usaramas quaternion primero tendríaos que crear un objeto de esta clase al cual le igualariamos la rotación deseada utilizando ``Quaternion rotation = Quaternion.Euler(rotationVector);``. En rotationVector especificariamos el angulo de rotación y el eje sobre un objeto Vector3. Acto seguido utilizariamos ``transform.rotation = rotation;`` para rotar el objeto
    
13.  ¿Como puedes averiguar la matriz de proyección en perspectiva que se ha usado para proyectar la escena al último frame renderizado?.
	Lo puedes averiguar usando la función ``cam.projectionMatrix;`` ,siendo cam ``Camera cam = GetComponent<Camera>();``, dentro de la función ``OnPostRender()`` 
14.  ¿Como puedes averiguar la matriz de proyección en perspectiva ortográfica que se ha usado para proyectar la escena al último frame renderizado?.  
	La pueds averiguar igual que en la respuesta anterior, pero poniendo la cámara en proyección ortográfica.
    
15.  ¿Cómo puedes obtener la matriz de transformación entre el sistema de coordenadas local y el mundial?.
	La puedes obtener haciendo uso de la funcion ``tranform.localToWorldMatrix``.
16.  Cómo puedes obtener la matriz para cambiar al sistema de referencia de vista.
	Puedes obtenerla haciendo uso de la funcion ``Camera.worldToCameraMatrix``
17.  Especifica la matriz de la proyección usado en un instante de la ejecución del ejercicio 1 de la práctica 1.
	Esto lo hice añadiendo una función OnRenderObject a la cámara y luego un código similar al del ejercicio 13.
	![](https://github.com/alu0101017396/seminario1_II_gif/blob/main/17.PNG)
18.  Especifica la matriz de modelo y vista de la escena del ejercicio 1 de la práctica 1.
	Esta la específique en una función ``OnRenderObject()`` utilizando ``GL.modelview()``.
	![](https://github.com/alu0101017396/seminario1_II_gif/blob/main/18.PNG)
20.  Aplica una rotación en el start de uno de los objetos de la escena y muestra la matriz de cambio al sistema de referencias mundial.  
    Esto lo podemos sacar igualando un objeto Matrix4x4 a ``transform.localToWorldMatrix;``
    ![](https://github.com/alu0101017396/seminario1_II_gif/blob/main/19.PNG)
21.  ¿Como puedes calcular las coordenadas del sistema de referencia de un objeto con las siguientes propiedades del Transform:?:
    Position (3, 1, 1), Rotation (45, 0, 45)
    
    Se calcularia multiplicando las matrices 
    (1, 0, 0, 3) (1      , 0      , 0       , 0) (cos(45), -sin(45), 0, 0)
    (0, 1, 0, 1) (0      , cos(45), -sin(45), 0) (sin(45), cos(45) , 0, 0)
    (0, 0, 1, 1) (sin(45), cos(45), 0       , 0) (0      , 0       , 1, 0)
    (0, 0, 0, 1) (0      , 0      , 0       , 1) (0      , 0       , 0, 1)
						    



