# FDV_07_Tilemaps

1. Obtener assets que incorpores a tu proyecto para la generación del mapa: planos e isométricos.
    Assets escogidos :
    
    <https://assetstore.unity.com/packages/2d/environments/nature-pixel-art-base-assets-free-151370>
    <https://assetstore.unity.com/packages/2d/environments/isometric-medieval-pack-209879>

2. Generar al menos 2 paletas para crear un mapa rectangular.

    Una paleta para el terreno del juego.

    [Tilemaps - Paletas](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile2.png)

    Otra para el ciel

    ![Tilemaps - Paletas](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile2_1.png)

3. Crear un mapa isométrico.
4. En el mapa isométrico generar zonas elevadas y obstáculos.
    Resultado:

    ![Tilemaps - Mapa Isometrico](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile3_5.png)

5. En el mapa convencional, incluir obstáculos y paredes.

    ![Tilemaps - Mapa Rectangular](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile4_6.gif)

6. Seleccionar sprites para usar como decoración y sprites animados para usar como personaje y como enemigos e incorporarlos al juego.
7. Controlar mediante scripts al menos dos transiciones de animación en el personaje y una de un enemigo.
    Se utilizó un [Cloud Sprite](https://toppng.com/photo/222272) como Sprite decorativo, se reutilizaron las animaciones de zombis y duendes y los Sprites de ejercicios anteriores.

   ![Tilemaps - Ejercicio 6-7](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile6_7.gif)

8. Incorpora elementos físicos en tu escena que respondan a las siguientes restricciones:

    1. Objeto estático que ejerce de barrera infranqueable
        Agregamos un _Sprite_ de una piedra y agregamos un _BoxCollider2D_, haciendo imposible que el personaje avance.
        ![Tilemaps - Ejercicio 8.1](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile8_1.gif)

    2. Zona en la que los objetos que caen en ella son impulsados hacia adelante
        Creamos un GameObject vacío y agregamos un **Rigidbody2D** y un **BoxCollider2D** para que _haya colisión_ y activamos la opción _IsTrigger_ y agregamos una etiqueta llamada "PushForce" y en el script asociado al jugador verificamos si estamos colisionando con el objeto y si estamos sumando una fuerza continua mientras se produce la colisión.

                ```C#
                private void OnTriggerStay2D(Collider2D other)
                   {
                      if (other.gameObject.CompareTag("PushFront"))
                      {
                            Zombie_Rigidbody.AddForce(Vector2.right * Impulse / 80);
                      }
                   }
                ```

    3. Objeto que es arrastrado por otro a una distancia fija
        Al triángulo le agregamos un componente _Rigidbody2D_ de tipo estático y un componente _DistanceJoint2D_ y conectamos el GameObject cuadrado amarillo que también tiene un componente _Rigidbody2D_ y activamos la colisión.

    4. Objeto que al colisionar con otros sigue un comportamiento totalmente físico.
        Agregamos un Sprite cuadrado y agregamos un Rigidbody2D de tipo Dynamic y BoxCollider2D con IsTrigger desactivado.

        Resultado 8.2 - 8.4:

        ![Tilemaps - Ejercicio 8.2 - 8.4](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile8_2_3_4.gif)

    5. Incluye dos capas que asignes a diferentes tipos de objetos y que permita evitar colisiones entre ellos.
        creamos una capa llamada "FallObj" y agregamos GameObjects a la capa usando el inspector.
        ![Tilemaps - Ejercicio 8.5 layer Colision](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile8_5_1.png)

    En Edit > Project Settings > 2D Physics configuramos las colisiones entre capas
    ![Tilemaps - Ejercicio 8.5 layer Colision](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile8_5.png)

    duplicando los cuadrados y agregándolos a diferentes capas.

   ![Tilemaps - Ejercicio 8.5](https://github.com/almadacv/FDV_07_Tilemaps/blob/main/Gif/Tile8_5.gif)
