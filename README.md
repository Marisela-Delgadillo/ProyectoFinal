**Integrantes:**
+ Aguilar Romo Danna Paulina
+ Amaya Quintero César Heberto
+ Marisela Delgadillo Bojórquez
+ Padilla Aispuro Idalia Guadalupe
+ Peña Hernández Azalia

# *Proyecto Final*

## Abstract

El objetivo de este proyecto fue crear una escena en Unity sobre vegetación con agua utilizando los distintos shaders aprendidos a lo largo del semestre, se pusieron a prueba todos nuestros conocimientos de Shader Graph, utilizando distintos tipos de modelos de luz, combinaciones, vertex shading y al igual se usaron los vértices como animación.

En la siguiente parte de la documentación se presentará la forma en la que se realizó el antes ya mencionado proyecto, se hablará un poco sobre la investigación de distintas fuentes, conceptos y temas en general de distintos modelos de luz para que nos fueran útiles como herramientas para la creación de nuestra escena en Unity.

## Introducción

Las bases de investigación sobre Shader Graph en Unity, nos dio la facilidad de desarrollar de manera visual y manejar al instante los posibles errores, también se puedieron crear y conectar nodos en redes de gráficos como lo hicimos casi en su totalidad. Shader Graph al utilizarse con el canal de renderizado de alta definición y el canal de renderizado universal, nos permitió realizar distintos tipos de modelos de luz, combinaciones y muchas mas cosas de una manera sumamente fácil.

Nuestra escena es tomada desde cero, junto con sus shaders y modelos. Para todo esto, se estudiaron los tipos de modelos de luz que realizamos y los modelos que podíamos ocupar para la creación de la escena, la personalización y las herramientas visuales nos permitieron crear efectos del agua y de la vegetación,nuestro escenario está conformado por rocas, flores y animales como patos, topos, ovejas y plantas carnívoras que le dieron un toque divertido. Los Shaders fueron creados desde cero en universal render pipeline en el cual nos encargamos de crear y conectar los nodos ya mencionados anteriormente. Cabe resaltar que existen diferentes tipos de shaders que utilizamos, el cual vertex shader,es uno de ellos y se utiliza para calcular la posición de los vértices en la imagen.

## Antecedentes

Antes de hablar acerca de lo que hoy conocemos como Shader Graphs, primero tenemos que conocer un poco acerca de Unity. Unity es uno de los motores de creación de videojuegos más importantes de la actualidad, que tuvo sus inicios en 2005 hasta la actualidad y más allá. Unity es uno de los grandes responsables de la democratización de la creación de videojuegos, al ofrecer a desarrolladores amateurs una forma sencilla y barata de aprender y desarrollar sus propias ideas, facilitando el proceso de creación y distribución de sus obras, y creando sin querer una nueva forma de crear videojuegos, la del desarrollador-autor.

El éxito de Unity se debe a su enfoque en cubrir las necesidades de los desarrolladores independientes, los cuales normalmente no pueden permitirse crear su propio motor de juegos, ni pagar el acceso a las herramientas necesarias. La compañía busca &quot;democratizar&quot; el desarrollo de videojuegos y hacer que el desarrollo de contenido interactivo 2D y 3D sea lo más accesible a tantas personas en todo el mundo como sea posible.

Anteriormente, no existían maneras de realizar lo que hoy conocemos como “shaders” si no era programando, así que las personas que podían realizar “shaders” son los que contaban con cierto conocimiento de programación y lo llevaban a cabo en Unity. A lo que nos referimos hoy en día como Shader Graph es lo que nos deja empezar a crear a las personas, que no estamos tan familiarizadas en el tema de la programación, básicamente se podría decir que es más didáctica y practica a comparación de la programación. Y es por lo que nos permite crear shaders muy fácilmente. Anteriormente los shaders eran un conjunto de instrucciones que eran ejecutadas todas al mismo tiempo por cada píxel de la pantalla, donde le daba el significado el código que escribías y que tenía que comportarse de manera diferente dependiendo de su posición en la pantalla. Ahora con Shader Graph solo tienes que conectar los nodos en una red de gráficos y puedes ver los gráficos y cambios que estas creando al instante.

Unity creo Shader Graph para trabajar con el canal de renderizado codificable. Los nodos maestros que funcionan con el canal de renderizado universal y el canal de renderizado de alta definición (HDRP) están incluidos en la versión básica. También logro que se pudiera extender para trabajar con cualquier canal de renderizado personalizado. (1)

## Desarrollo

+ ***Capítulo 1. Creación del proyecto en Unity.*** 

  + Lo primero que realizamos fue nuestro proyecto en Unity en su versión 2020. Después generamos una nueva escena, donde también agregamos nuestra carpeta de Shaders. Como ya se mencionó anteriormente, shader graph nos deja crear shaders fácilmente desarrollándolos de manera visual en tiempo real. Para comenzar con lo visual, se fueron creando los shaders para posteriormente unirlos mediante nuestro escenario.

+ ***Capítulo 2. Creación de Shader para el agua***

  + Para realizar el shader del agua. Primero generamos un grafo de universal render pipeline tipo lit shader graph, decidimos usar este ya que nuestro proyecto no requiere que usemos Sprites. Creamos este shader con un tipo de superficie transparente para que se desvanezca en función con profundidad, usamos la profundidad de la cámara para crear un nodo de la cámara, se le resto el valor de la posición del espacio a la profundidad para crear un gradiente en el agua. Para tener más control en los bordes realizamos un vector de fuerza, posteriormente usamos los brillos del degradado para mezclar entre los dos valores diferentes, así que creamos dos valores de color para poder separar el color del agua profunda y la de la superficie, los conectamos a un nodo y usamos el degradado creado como una máscara para el nodo. Para darle un aspecto más realista al agua usamos dos mapas de normales que se mueven en diferentes direcciones los cuales fueron conectados a sus nodos correspondientes y conectados para poder controlar su fuerza, para que el agua fuera reflejante se utilizó un Smoothness. Y por último para darle movimiento al agua utilizamos la posición de nuestro objeto para poder ser conectado a vertex. 
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen1.png)

+ ***Capítulo 3. Creación del Shader modelo de luz custom*** 

  + Este modelo de luz esta basado en Lambert y en el modelo Specular, crearemos un grafo de universal render pipeline tipo lit shader graph. Primero que nada, creamos nuestro albedo, el cual será el color principal, una vez hecho esto creamos un archivo de tipo hlsl para obtener la dirección de la luz por medio del siguiente código.
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen2.png)

  + Ahora creamos un subgrafo para nuestro mainLight, donde pondremos nuestra función creada anteriormente y le conectaremos un nodo de posición:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen3.png)

  + Acto seguido creamos otro subgrafo en el cual realizaremos la operación producto punto, para esto es necesario el MainLight que acabamos de hacer y el normal vector, lo saturamos para que nos quede en valores de 0 y 1:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen4.png)

  + Para crear el efecto de falloff haremos un subgrafo donde estará el Lambert, para esto multiplicamos nuestro producto punto con el color de la atenuación de la luz:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen5.png)

  + De igual manera que con el MainLight crearemos un archivo hlsl para el DirectSpecular, este funciona para que se refleje la dirección de la luz dependiendo de la dirección de donde sea observado, para esto utilizaremos el siguiente código:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen6.png)

  + Posteriormente creamos un subgrafo para el DirectSpecular donde le pasaremos sus propiedades correspondientes:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen7.png)

  + Crearemos otro subgrafo para la atenuación de la luz, donde utilizaremos el MainLight y realizaremos sus respectivas operaciones para calcular el color y las sombras:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen8.png)
  
  + Para el efecto de Toon Shading crearemos un subgrafo con el efecto de Ramp Texture, en el cual ocuparemos dos gradientes entre el negro y blanco, uno intenso y el otro con un pequeño suavizado. Quedando de la siguiente manera:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen9.png)

  + Lo pasamos a nuestro shader principal conectando el producto punto con la intensidad de la luz, también crearemos una propiedad de tipo Boolean para saber si el efecto será intenso o suavizado.

  + Para el reflejo de la luz cartoon, en vez de utilizar una textura creada por nosotros en cualquier editor de imágenes, utilizamos la herramienta voronoi para simular dicho efecto, entonces creamos otro subgrafo llamado Dabs, en donde modificaremos las propiedades del voronoi utilizando el rotate y el tiling and offset. Dando como resultado lo siguiente:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen10.png)

  + Lo pasamos a nuestro shader principal multiplicándolo con el DirectSpecular.

  + Crearemos otro subgrafo para el SideLight, el cual es la silueta de luz que se forma en nuestro modelo, dependiendo de la dirección de la luz. Aquí haremos uso nuevamente del MainLight, del Lambert. Substraeremos pocas unidades a nuestro lamber para que el falloff quede en la parte superior y realizaremos un producto punto entre el MainLight y el ViewDirection, para después unir ambos resultados e invertirlo y agregar el filtro deseado utilizando el efecto Fresnel y lo redondeamos utilizando Step. Viéndose así:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen11.png)

  + Para agregarlo al shader principal solo lo tenemos que sumar con el efecto que ya teníamos. Finalmente, nuestro shader se vería de este modo:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen12.png)
  + Agregándolo a un modelo:
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen13.png)

+ ***Capítulo 4. Creación del Shader grass vertex***

  + Para el movimiento de las plantas y las hojas de los árboles, se necesita modificar la velocidad de desplazamiento del vértice. Para ello, se agrega una propiedad de tipo vector2, en la cual se introduce la velocidad con la que se desea que se muevan las plantas y se multiplica por el tiempo. Esto se conecta con un Tiling and Offset junto con la posición. Después, para poder cambiar la variación de la posición del ruido del vértice, agregamos un nodo de Gradient Noise, al cual le conectamos lo que calculamos anteriormente y una propiedad de tipo float con el valor de la densidad del ruido. Todo esto se conecta a un Substract para limpiar el ruido del viento, y después multiplicarlo por la intensidad del viento. Luego, lo aplicamos este ruido al eje de las X y creamos la interpolación lineal en la posición del eje de las Y. Para terminar, sólo hay que convertirlo de posición mundial a objeto relativo y conectarlo al vertex position.
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen14.png)

+ ***Capítulo 5. Creación de escenario con shaders***

  + Después haber hecho los shaders, se comenzó a crear el escenario, cambiamos el material de skybox por otro material que descargamos desde assets para el cielo para poder tener un cielo de acuerdo con nuestro proyecto. Luego creamos un objeto 3D tierra y le fuimos dando forma a nuestro terreno con ayuda de las herramientas que este plano nos proporciona.
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen15.png)

  + Después de terminar de crear nuestro plano de terreno, se buscaron assets que contaron con los requisitos necesarios para elaborar nuestro proyecto, por lo cual colocamos un asset de vegetación verde para el relieve creando una zona montañosa verde en el plano de tierra. Posteriormente se le agregó un plano al cual se le coloco el material del agua.
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen16.png)

  + A partir de esto, se empezó a decorar con vegetación de assets de árboles y plantas los cuales los importamos a Unity y eliminamos los árboles que no necesitamos, así que nos dimos a la tarea de buscar cada assets que nos gustara, donde concluimos a 3 diferentes. A los cuales se le agrego el shader grass vertex.
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen17.png)

  + Y finalmente para utilizar otro de nuestros shaders colocamos plantas con su animación vertex, rocas y animales cuyos utilizan el modelo de luz custom toon-shading. Este shader ya antes definido se utilizó para darle un poco más de vida animal a nuestro escenario.
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen18.png)
  + ![](https://github.com/Marisela-Delgadillo/ProyectoFinal/blob/main/Assets/Preview/Imagen19.png)

## Conclusiones

Al final obtuvimos un proyecto que nos retó a poner en práctica nuestros conocimientos en base a la materia, se realizó muy buen proyecto, nos gustó la manera en la que se deslindó cada aparte de él y fue muy divertido colaborar y crear algo que realmente nos gustara. Se obtuvo un paisaje digno de cada punto con el que se estableció el proyecto y por eso podemos decir que el terminarlo y concluir con un escenario creado por nosotros fue muy bueno tanto para nosotros como para reforzar nuestros conocimientos. Hubo algunos detalles en cuestión de encontrar algunos modelos o como empezar a crearlo, pero de ahí en fuera todo se hizo en su tiempo y forma.

## Resultado

***Link del video:*** https://www.youtube.com/watch?v=6_DInOgbl3M

## Referencias

1. Anónimo. (s.f.). Unity SRP Doc. Gradient Noise Node. Recuperado de: [https://bitinn.github.io/ScriptableRenderPipeline/ShaderGraph/Gradient-Noise-Node/](https://bitinn.github.io/ScriptableRenderPipeline/ShaderGraph/Gradient-Noise-Node/)
2. Anónimo. (2018). RoyStan. Toon Shader. Recuperado de: [https://roystan.net/articles/toon-shader.html](https://roystan.net/articles/toon-shader.html)
3. Anónimo. (2018). RoyStan. Grass Shader. Recuperado de: [https://roystan.net/articles/grass-shader.html](https://roystan.net/articles/grass-shader.html)
4. Anónimo. (2021). Game Dev. Water Shader. Recuperado de: [https://gamedev.stackexchange.com/questions/183143/need-to-generate-seamless-gradient-noise-texture-for-water-shader?noredirect=1&amp;lq=1](https://gamedev.stackexchange.com/questions/183143/need-to-generate-seamless-gradient-noise-texture-for-water-shader?noredirect=1&amp;lq=1)
5. Caurin, J. (2019). Geekno. Shader. Recuperado de: [https://www.geekno.com/glosario/shader](https://www.geekno.com/glosario/shader)
6. Cooper, T. (2018). Unity. Introduction to Shader Graph: Build your shaders with a visual editor. Recuperado de: [https://blog.unity.com/technology/introduction-to-shader-graph-build-your-shaders-with-a-visual-editor](https://blog.unity.com/technology/introduction-to-shader-graph-build-your-shaders-with-a-visual-editor)
7. Gonzalez, P. (2015). Thebookofshaders. ¿Qué es un fragment shader? Recuperado de: [https://thebookofshaders.com/01/?lan=es](https://thebookofshaders.com/01/?lan=es)
8. Hocking, J. (2020). Raywenderlich. Introduction to Shaders in Unity. Recuperado de: [https://www.raywenderlich.com/5671826-introduction-to-shaders-in-unity](https://www.raywenderlich.com/5671826-introduction-to-shaders-in-unity)
9. Isidoro, J. (s.f.). Developer. Animated Grass with Pixel and Vertex Shaders. Recuperado de: [http://developer.amd.com/wordpress/media/2012/10/ShaderX\_AnimatedGrass.pdf](http://developer.amd.com/wordpress/media/2012/10/ShaderX_AnimatedGrass.pdf)
10. Kalupahana, D. (2019, 20 junio). Shaders in Unity — Lambert and Ambient - Deshan Kalupahana. Medium. Recuperado de: [https://medium.com/@deshankalupahana/shaders-in-unity-lambert-and-ambient-ceba9fab6cfa](https://medium.com/@deshankalupahana/shaders-in-unity-lambert-and-ambient-ceba9fab6cfa)
11. Lindman, A. (2019, 31 julio). Custom Lighting in Shader Graph: Expanding your graphs in 2019. Unity Blog. Recuperado de: [https://blog.unity.com/technology/custom-lighting-in-shader-graph-expanding-your-graphs-in-2019](https://blog.unity.com/technology/custom-lighting-in-shader-graph-expanding-your-graphs-in-2019)
12. Lin, W. (2019). Raywenderlich. Shader Graph in Unity for Beginners. Recuperado de: [https://www.raywenderlich.com/3744978-shader-graph-in-unity-for-beginners](https://www.raywenderlich.com/3744978-shader-graph-in-unity-for-beginners)
13. Miciuleviciute, P. (2021). Paulinami. Water Shader [URP, Amplify]. Recuperado de: [https://www.paulinami.com/water-shader-urp-amplify](https://www.paulinami.com/water-shader-urp-amplify)
14. P. (s. f.). 5.1. Definición, características y objetivo del método experimental. Psikipedia. Recuperado de: [https://psikipedia.com/libro/analisis-de-datos/2458-la-distribucion-t-de-student#:%7E:text=Una%20distribuci%C3%B3n%20%E2%80%9Ct%E2%80%9D%20es%20el,sim%C3%A9trica%2C%20con%20%CE%BC%20%3D%200](https://psikipedia.com/libro/analisis-de-datos/2458-la-distribucion-t-de-student#:%7E:text=Una%20distribuci%C3%B3n%20%E2%80%9Ct%E2%80%9D%20es%20el,sim%C3%A9trica%2C%20con%20%CE%BC%20%3D%200).
15. School, A. C. T. D. (2019, 12 junio). Cel Shading ó Toon Shading. THE CUBE. [https://www.thecube3danimation.com/blog-1/2018/1/29/cel-shading-toon-shading](https://www.thecube3danimation.com/blog-1/2018/1/29/cel-shading-toon-shading)
16. Strix, S. (2016). Stix Games. DirectX 11 Grass Shader. Recuperado de: [https://stixgames.com/publicfiles/StixGames%20-%20DirectX%2011%20Grass%20Shader%20Manual.pdf](https://stixgames.com/publicfiles/StixGames%20-%20DirectX%2011%20Grass%20Shader%20Manual.pdf)
17. Technologies, U. (s. f.-b). Unity - Manual: Smoothness. Unity:Manual. Recuperado 25 de mayo de 2021, de [https://docs.unity3d.com/Manual/StandardShaderMaterialParameterSmoothness.html](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterSmoothness.html)
18. Technologics, U. (s. f.). Get Main Light Position. Unity Forum. Recuperado 25 de mayo de 2021, de [https://forum.unity.com/threads/get-main-light-position.811071/](https://forum.unity.com/threads/get-main-light-position.811071/)
19. Technologies, U. (s. f.). Unity - Manual: Surface Shader lighting examples. Unity. Recuperado de: [https://docs.unity3d.com/Manual/SL-SurfaceShaderLightingExamples.html](https://docs.unity3d.com/Manual/SL-SurfaceShaderLightingExamples.html)
20. Turnes, Y. (2021). GamerDic. Shader. Recuperado de: [https://www.gamerdic.es/termino/shader/](https://www.gamerdic.es/termino/shader/)
21. Technologies, U. (2021). Unity. Gradient Noise Node. Recuperado de: [https://docs.unity3d.com/Packages/com.unity.shadergraph@6.9/manual/Gradient-Noise-Node.html](https://docs.unity3d.com/Packages/com.unity.shadergraph@6.9/manual/Gradient-Noise-Node.html)
22. Technologies, U. (2021). Unity. Shader Graph: Tiling and Offset. Recuperado de: [https://learn.unity.com/tutorial/shader-graph-tiling-and-offset-2019-3#](https://learn.unity.com/tutorial/shader-graph-tiling-and-offset-2019-3)
23. Technologies, U. (2021). Unity. Subtract Node. Recuperado de: [https://docs.unity.cn/Packages/com.unity.shadergraph@6.9/manual/Subtract-Node.html](https://docs.unity.cn/Packages/com.unity.shadergraph@6.9/manual/Subtract-Node.html)
24. Technologies, U. (2021). Unity. Tiling And Offset Node. Recuperado de: [https://docs.unity3d.com/Packages/com.unity.shadergraph@6.9/manual/Tiling-And-Offset-Node.html](https://docs.unity3d.com/Packages/com.unity.shadergraph@6.9/manual/Tiling-And-Offset-Node.html)
25. Unity Technologies. (2016). Unity. Assets Shader. Recuperado de: [https://docs.unity3d.com/es/530/Manual/class-Shader.html](https://docs.unity3d.com/es/530/Manual/class-Shader.html)
26. Unity Technologies. (2016). Unity. Crear y Editar Terrenos. Recuperado de:[https://docs.unity3d.com/es/530/Manual/terrain-UsingTerrains.html](https://docs.unity3d.com/es/530/Manual/terrain-UsingTerrains.html)
27. Unity Technologies. (2019). Unity. Agua en Unity. Recuperado de: [https://docs.unity3d.com/es/2018.4/Manual/HOWTO-Water.html](https://docs.unity3d.com/es/2018.4/Manual/HOWTO-Water.html)
28. Unity Technologies. (2021). Unity. Shader Graph. Recuperado de: [https://unity.com/es/shader-graph](https://unity.com/es/shader-graph)
29. UNIAT. (2021). Uniat. Evolución de Unity en sus 10 años de historia!. Recuperado de: [https://www.uniat.edu.mx/unity-10-anos/](https://www.uniat.edu.mx/unity-10-anos/)
30. Unity Technologies. (2021). Unity. Water Shader. Recuperado de: [https://forum.unity.com/threads/water-shader.995380/](https://forum.unity.com/threads/water-shader.995380/)

Ciudad Obregón, Sonora; 25 de mayo de 2020
