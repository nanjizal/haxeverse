Kha Setup
=========

Make sure you have git and node (v6.0+) installed.

Install Kode editor from github.

https://github.com/Kode/KodeStudio/releases

![kode](https://github.com/nanjizal/haxeverse/blob/master/md/Kode.png)

From terminal then clone the Empty git project, it includes it's own version of Kha and Haxe.

```
git clone --recursive https://github.com/KTXSoftware/Empty.git
```
```
git submodule foreach --recursive git pull origin master
```
[(for other Kha workflows see the official documentation)](https://github.com/Kode/Kha/wiki/Getting-Started)

So you should see something like this in the terminal.
```
/projects/haxeverse/examples$ git clone --recursive https://github.com/KTXSoftware/Empty.git
Cloning into 'Empty'...
remote: Counting objects: 65, done.
remote: Total 65 (delta 0), reused 0 (delta 0), pack-reused 65
Unpacking objects: 100% (65/65), done.
Submodule 'Kha' (https://github.com/Kode/Kha.git) registered for path 'Kha'
Cloning into '/projects/haxeverse/examples/Empty/Kha'...
Submodule path 'Kha': checked out '495d0d6e71ff6aae791ce1253e98e161697534d3'
Submodule 'Backends/Kore/khacpp' (https://github.com/Kode/khacpp.git) registered for path 'Kha/Backends/Kore/khacpp'
Submodule 'Kore' (https://github.com/Kode/Kore.git) registered for path 'Kha/Kore'
Submodule 'Tools/haxe' (https://github.com/Kode/haxe_bin.git) registered for path 'Kha/Tools/haxe'
Submodule 'Tools/khamake' (https://github.com/Kode/khamake.git) registered for path 'Kha/Tools/khamake'
Submodule 'Tools/kravur' (https://github.com/Kode/kravur_bin.git) registered for path 'Kha/Tools/kravur'
Submodule 'Tools/oggenc' (https://github.com/Kode/oggenc_bin.git) registered for path 'Kha/Tools/oggenc'
Cloning into '/projects/haxeverse/examples/Empty/Kha/Backends/Kore/khacpp'...
Cloning into '/projects/haxeverse/examples/Empty/Kha/Kore'...
Cloning into '/projects/haxeverse/examples/Empty/Kha/Tools/haxe'...
Cloning into '/projects/haxeverse/examples/Empty/Kha/Tools/khamake'...
Cloning into '/projects/haxeverse/examples/Empty/Kha/Tools/kravur'...
Cloning into '/projects/haxeverse/examples/Empty/Kha/Tools/oggenc'...
Submodule path 'Kha/Backends/Kore/khacpp': checked out '71bc48b53a150d495eb97fd17a6ea85162567c71'
Submodule path 'Kha/Kore': checked out '1da72b29c4768b93527f8aa5368fe45fdf35b71e'
Submodule 'Tools/koremake' (https://github.com/Kode/koremake.git) registered for path 'Kha/Kore/Tools/koremake'
Submodule 'Tools/kraffiti' (https://github.com/Kode/kraffiti_bin.git) registered for path 'Kha/Kore/Tools/kraffiti'
Submodule 'Tools/krafix' (https://github.com/Kode/krafix_bin.git) registered for path 'Kha/Kore/Tools/krafix'
Cloning into '/projects/haxeverse/examples/Empty/Kha/Kore/Tools/koremake'...
Cloning into '/projects/haxeverse/examples/Empty/Kha/Kore/Tools/kraffiti'...
Cloning into '/projects/haxeverse/examples/Empty/Kha/Kore/Tools/krafix'...
Submodule path 'Kha/Kore/Tools/koremake': checked out '55a1f9380330cf04f46a4819ba93d72f2e02a92d'
Submodule path 'Kha/Kore/Tools/kraffiti': checked out '4da769ebb085dfc2494e6402a1329abee3c4e999'
Submodule path 'Kha/Kore/Tools/krafix': checked out '03672b66d53b2b75a3a908e234cb071eca081cef'
Submodule path 'Kha/Tools/haxe': checked out 'c3db4df6a43298e187f72fe3c9c5b99a8dbaf42c'
Submodule path 'Kha/Tools/khamake': checked out 'a1b504586edf53a0c490c5b2b8d7639cb98c9888'
Submodule path 'Kha/Tools/kravur': checked out '224bfe99eebe2fa7d30659ca8f0fc435f312d66d'
Submodule path 'Kha/Tools/oggenc': checked out '07a44da6762fe4b26ac069e1dcee16c2ad23ae78'
```
So if we open 'Kode Studio' and we can drag our Empty project onto it, and clicking on the bug spider icon we can run.

![empthykode](https://github.com/nanjizal/haxeverse/blob/master/md/emptyKode.png)

Not very exciting we get a black window.

Triangle is King
----------------

Kha has several graphics drawing/rendering modes

- Graphics2 ( 2D ) 
- Graphics4 ( 3D )
- others...

For 2D shapes we use Graphics2 and for 3D shapes we would use Graphics4.  To create any complex 2D shapes in Kha we can call the fillTriangle command, it just takes the x and y of each of the triangles corners.

Lets create a new class "TriangleTest.hx" next to our other classes and add a static method for drawing a Red triangle:

```haxe
package;
import kha.graphics2.Graphics;
import kha.Color;
class TriangleTest{
	inline static var red: Color = 0xFFFF0000;
	public static inline function redTriangle( g2: Graphics ){
		g2.begin();
		g2.color =  red;
		g2.fillTriangle( 100, 100, 
                     200, 200,
                     100, 300 );
		g2.end();
	}
}
```
And then in our "Empty.hx" render method which already exists we can add a call the redTriangle static method, passing in the the Graphics2.

```haxe
	function render(framebuffer: Framebuffer): Void {
		TriangleTest.redTriangle( framebuffer.g2 );		
	}
 ```

This just draws a red triangle every time the screen renders.

![red triangle](https://github.com/nanjizal/haxeverse/blob/master/md/redTriangle.png)
 
