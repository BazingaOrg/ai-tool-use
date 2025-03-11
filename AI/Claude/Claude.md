# [Claude](https://claude.ai/) 使用

1. ✅[Claude Sonnet 3.7 做了天气卡片效果的生成](https://x.com/vikingmute/status/1894321474582057388)，提示词是：
   ```text
      Create a single HTML file containing CSS and JavaScript to generate an animated weather card. The card should visually represent the following weather conditions with distinct animations: Wind: (e.g., moving clouds, swaying trees, or wind lines) Rain: (e.g., falling raindrops, puddles forming) Sun: (e.g., shining rays, bright background) Snow: (e.g., falling snowflakes, snow accumulating) Show all the weather card side by side The card should have a dark background. Provide all the HTML, CSS, and JavaScript code within this single file. The JavaScript should include a way to switch between the different weather conditions (e.g., a function or a set of buttons) to demonstrate the animations for each.
   ```

体验：试了 claude、deepseek、grok、gemini，效果还是 claude 3.5 效果好。

2. ✅[用 AI 自动生成的代码做了一个三维地球](https://x.com/ymyz1229/status/1895762253703758196)

   ```html
   <!DOCTYPE html>
   <html>
     <head>
       <title>3D Interactive Earth</title>
       <style>
         body {
           margin: 0;
           overflow: hidden;
           background-color: #000000;
         }
         canvas {
           display: block;
         }
         #info {
           position: absolute;
           top: 10px;
           width: 100%;
           text-align: center;
           color: white;
           font-family: Arial, sans-serif;
         }
       </style>
     </head>
     <body>
       <div id="info">
         Interactive 3D Earth - Drag to rotate, scroll to zoom
       </div>
       <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
       <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js"></script>
       <script>
         let scene, camera, renderer, earth, controls;

         init();
         animate();

         function init() {
           // Scene
           scene = new THREE.Scene();

           // Camera
           camera = new THREE.PerspectiveCamera(
             75,
             window.innerWidth / window.innerHeight,
             0.1,
             1000
           );
           camera.position.z = 2;

           // Renderer
           renderer = new THREE.WebGLRenderer({ antialias: true });
           renderer.setSize(window.innerWidth, window.innerHeight);
           renderer.setPixelRatio(window.devicePixelRatio);
           document.body.appendChild(renderer.domElement);

           // Earth
           const geometry = new THREE.SphereGeometry(1, 64, 64);

           // Texture Loader
           const textureLoader = new THREE.TextureLoader();

           // Earth texture
           const earthTexture = textureLoader.load(
             "https://raw.githubusercontent.com/mrdoob/three.js/master/examples/textures/planets/earth_atmos_2048.jpg",
             function (texture) {
               texture.wrapS = texture.wrapT = THREE.RepeatWrapping;
             }
           );

           // Bump mapping
           const bumpMap = textureLoader.load(
             "https://raw.githubusercontent.com/mrdoob/three.js/master/examples/textures/planets/earth_normal_2048.jpg"
           );

           // Specular mapping
           const specularMap = textureLoader.load(
             "https://raw.githubusercontent.com/mrdoob/three.js/master/examples/textures/planets/earth_specular_2048.jpg"
           );

           const material = new THREE.MeshPhongMaterial({
             map: earthTexture,
             bumpMap: bumpMap,
             bumpScale: 0.05,
             specularMap: specularMap,
             specular: new THREE.Color("grey"),
             shininess: 5,
           });

           earth = new THREE.Mesh(geometry, material);
           scene.add(earth);

           // Ambient light
           const ambientLight = new THREE.AmbientLight(0xffffff, 0.2);
           scene.add(ambientLight);

           // Point light (sun-like)
           const pointLight = new THREE.PointLight(0xffffff, 1);
           pointLight.position.set(5, 3, 5);
           scene.add(pointLight);

           // Stars
           const starGeometry = new THREE.SphereGeometry(10, 64, 64);
           const starMaterial = new THREE.MeshBasicMaterial({
             map: textureLoader.load(
               "https://raw.githubusercontent.com/mrdoob/three.js/master/examples/textures/planets/starfield.png"
             ),
             side: THREE.BackSide,
           });
           const starField = new THREE.Mesh(starGeometry, starMaterial);
           scene.add(starField);

           // Controls
           controls = new THREE.OrbitControls(camera, renderer.domElement);
           controls.enableDamping = true;
           controls.dampingFactor = 0.05;
           controls.minDistance = 1.5;
           controls.maxDistance = 4;
           controls.rotateSpeed = 0.5;
           controls.autoRotate = true;
           controls.autoRotateSpeed = 0.5;

           // Initial camera position (facing Asia)
           camera.position.set(-1, 1, 2);
           controls.target.set(0, 0, 0);

           // Handle window resize
           window.addEventListener("resize", onWindowResize, false);
         }

         function onWindowResize() {
           camera.aspect = window.innerWidth / window.innerHeight;
           camera.updateProjectionMatrix();
           renderer.setSize(window.innerWidth, window.innerHeight);
         }

         function animate() {
           requestAnimationFrame(animate);
           controls.update();
           renderer.render(scene, camera);
         }
       </script>
     </body>
   </html>
   ```

   体验：用 claude 3.5 生成。

## 2025.03.12

1. [如何将下面的这种全是字的文档，变成上面这种美观、直观的网页](https://x.com/op7418/status/1899028013850787859)
