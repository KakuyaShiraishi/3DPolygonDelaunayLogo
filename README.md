# 3DPolygonDelaunayLogo
3D polygon was created by Delaunay triangulation.  
link [Click Here](https://shiraishikakuya.github.io/3DPolygonDelaunayLogo/)

---
I used the shader to write this program.  
・VertexShader  

```
	uniform float amplitude;
	
	attribute vec3 customColor;
	attribute vec3 displacement;
	
	varying vec3 vNormal;
	varying vec3 vColor;
			
	void main() {
		vNormal = normal;
		vColor = customColor;
		vec3 newPosition = position + normal * amplitude * displacement;
		gl_Position = projectionMatrix * modelViewMatrix * vec4( newPosition, 1.0 );
		}
```  
・FragmentShader  

```
	varying vec3 vNormal;
	varying vec3 vColor;
	
	void main() {
		const float ambient = 0.4;
		vec3 light = vec3( 1.0 );
		light = normalize( light );
		float directional = max( dot( vNormal, light ), 0.0 );
		gl_FragColor = vec4( ( directional + ambient ) * vColor, 1.0 );
		}
```


---
__3D Polygon__
![](https://raw.githubusercontent.com/ShiraishiKakuya/3DPolygonDelaunayLogo/master/img/01.png)

  
3D polygons were meshed and randomly colored using Delaunay triangulation.
![](https://raw.githubusercontent.com/ShiraishiKakuya/3DPolygonDelaunayLogo/master/img/02.png)

  
  
  
The triangle of that 3D polygon can be moved by amplitude.
Can leave afterimages in moving triangles.
For that purpose, I created GUI to control amplitude and afterimage.
![](https://raw.githubusercontent.com/ShiraishiKakuya/3DPolygonDelaunayLogo/master/img/gui.png)
![](https://raw.githubusercontent.com/ShiraishiKakuya/3DPolygonDelaunayLogo/master/img/03.png)
![](https://raw.githubusercontent.com/ShiraishiKakuya/3DPolygonDelaunayLogo/master/img/05.png)


By the way, the amplitude parameter can be diffused so far.
![](https://raw.githubusercontent.com/ShiraishiKakuya/3DPolygonDelaunayLogo/master/img/04.png)
