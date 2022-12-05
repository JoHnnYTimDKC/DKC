# DKC
Coding-one-Final project

<html>

<head>
 <script src = "https://mimicproject.com/libs/maximilian.v.0.1.js"></script>
 
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r126/three.min.js" integrity="sha512-n8IpKWzDnBOcBhRlHirMZOUvEq2bLRMuJGjuVqbzUJwtTsgwOgK5aS0c1JA647XWYfqvXve8k3PtZdzpipFjgg==" crossorigin="anonymous"></script>
<script src="https://unpkg.com/three@0.126.0/examples/js/loaders/GLTFLoader.js"></script>
 
 <script src = "https://mimicproject.com/libs/maximilian.js"></script>
  
  <script src = "orbitControls.js"></script>
  
  
	<meta charset="utf-8">
  
  
	<style>
		body {
          
			margin: 0px;
		    background-color: #000000;
			overflow: hidden;
		}
      
      
      
	</style>
</head>

<body>
  
  <object height="100" width="100" data="music.mp3"></object>
 
  
	<script type="module">
      


      
   const axesHelper = new THREE.AxesHelper(6);
    
	var camera = new THREE.PerspectiveCamera(100, window.innerWidth / window.innerHeight, 1, 1000); 
      
	var scene = new THREE.Scene();  
    var spheres = [];
    var timer = [];
      
   
  
	var geometry4 = new THREE.TorusGeometry( 10, 0.2, 10, 100 );
   
    var geometry2 = new THREE.PlaneGeometry( 450,250 );
  
    var geometry3 = new THREE.SphereGeometry( 10, 50, 50 );
      
      
	var myTextureLoader = new THREE.TextureLoader();
    var myTextureLoader2 = new THREE.TextureLoader(); 
    var myTextureLoader3 = new THREE.TextureLoader(); 
    var myTextureLoader4 = new THREE.TextureLoader(); 

      
	var myTexture = myTextureLoader.load('00.jpg'); 
    var myTexture2 = myTextureLoader2.load('123.jpg');  
    var myTexture3 = myTextureLoader3.load('555.jpg'); 
    var myTexture4 = myTextureLoader4.load('1.jpeg'); 
  
      
	var material = new THREE.MeshBasicMaterial({map: myTexture}); 
    var material2 = new THREE.MeshBasicMaterial({map:myTexture2,side:THREE.DoubleSide} )
    var material3 = new THREE.MeshBasicMaterial( {map: myTexture3});
    var material4 = new THREE.MeshBasicMaterial( {map: myTexture4});
   
      

     
    var torus = new THREE.Mesh( geometry4, material4 );
    var plane = new THREE.Mesh( geometry2, material2 ); 
    var sphere = new THREE.Mesh( geometry3, material3 );
      
	var light = new THREE.DirectionalLight("rgb(155,520,385)");    
	var renderer = new THREE.WebGLRenderer();

    var light2 = new THREE.AmbientLight( 0x404040,6); light
    scene.add( light );
      
    var light3 = new THREE.PointLight( 0xff0000, 1100, 100 );
    light.position.set( 150,150, 150 );
  
    
    camera.position.set(50,50,602 );

	light.position.set(0,0,12);
    light2.position.set(10,0,12);
    light3.position.set(0,0,0);
    plane.position.z = -9; 

	scene.add(light);
    scene.add(light2);
    scene.add(light3);
    scene.add(plane);
    scene.add(torus);
    scene.add(axesHelper);
    scene.add(sphere);
    

     
       var loader = new THREE.GLTFLoader();
      loader.load (
      	'punk.glb',
        function (gltf) {
          let model = gltf.scene.children[0];
          let geometry = model.geometry;
          model.material = material;
          model.position.set(20, -280, -200);
          model.scale.x = model.scale.y = model.scale.z = 0.61;
          
          scene.add(model);
          
          
          
        } 
      )

      
      
  
  torus.rotation.Y =Math.PI/2
  
      
	renderer.setPixelRatio(window.devicePixelRatio);
	renderer.setSize(window.innerWidth, window.innerHeight);
	document.body.appendChild(renderer.domElement);
	window.addEventListener('resize', onWindowResize, false); 
    var controls = new THREE.OrbitControls (camera, renderer.domElement);

     
      
 	for ( let i = 0; i < 200; i ++ ) {

					const mesh = new THREE.Mesh( geometry3, material3 );

					mesh.position.x = Math.random() * 60 - 50;
					mesh.position.y = Math.random() * 60 - 50;
					mesh.position.z = Math.random() * 60 - 50;

					mesh.scale.x = mesh.scale.y = mesh.scale.z = Math.random() * 1 + 1;

					scene.add( mesh );

					spheres.push( mesh );

				}

 
  
function draw() {
   const timer = 0.0001 * Date.now();
    torus.position.set = (300,2000,200);
    torus.rotation.y+= 0.01;
    controls.update();
  
  for ( let i = 0, il = spheres.length; i < il; i ++ ) {

					const sphere = spheres[ i ];

					sphere.position.x = 560 * Math.tan( timer + i );
					sphere.position.y = 990 * Math.sin( timer + i * 2.2 );

				}
  
	renderer.render(scene, camera);
	requestAnimationFrame(draw);
}
      
      
    
function onWindowResize() {
	camera.aspect = window.innerWidth / window.innerHeight;
	camera.updateProjectionMatrix();
	renderer.setSize(window.innerWidth, window.innerHeight);
}    
      
draw();
      
      
      
	</script>
</body>

</html>
