# Image and video processing

## Gama de grises

### Usando Promedio RGB

> :P5 width=350, height=450
>
> let img;
> function preload(){
>   img = loadImage('/vc/docs/sketches/Stormlight.jpg');
>}
> function setup() {
>   createCanvas(350, 450);
>   image(img, 0, 0,width,height);
> }


> :P5 width=350, height=450
>
> let img;
> let img2
> function preload(){
>   img = loadImage('/vc/docs/sketches/Stormlight.jpg');
>}
> function setup() {
>   createCanvas(350, 450);
>   image(img, 0, 0,width,height);
>   let d = pixelDensity();
>   loadPixels();
>   let numPixels = 8 * (width * d) * (height / 2 * d);
>   for (let i = 0; i < numPixels; i += 4) {
>      let r = red(pixels[i]);
>      let g = green(pixels[i]);
>      let b = blue(pixels[i]);
>      let gray = (r+b+g)/3;
>      let grayColor = color(gray, gray, gray);
>      pixels[i] = red(grayColor);
>      pixels[i + 1] = green(grayColor);
>      pixels[i + 2] = blue(grayColor);
>    }
>   updatePixels();
> }

### Usando Luma

> :P5 width=350, height=450
>
> let img3;
> function preload(){
>   img3 = loadImage('/vc/docs/sketches/eye-color.jpg');
>}
> function setup() {
>   createCanvas(350, 450);
>   image(img3, 0, 0,width,height);
> }


> :P5 width=350, height=450
>
> let img4
> function preload(){
>   img4 = loadImage('/vc/docs/sketches/eye-color.jpg');
>}
>
> function setup() {
>   createCanvas(350, 450);
>   image(img4, 0, 0,width,height);
>   let d = pixelDensity();
>   loadPixels();
>
>   let numPixels = 8 * (width * d) * (height / 2 * d);
>   for (let i = 0; i < numPixels; i += 4) {
>      let r = red(pixels[i]);
>      let g = green(pixels[i]);
>      let b = blue(pixels[i]);
>      let colorpixel = color(r,g,b)
>      let r_norm = r/255;
>      let g_norm = g/255;
>      let b_norm = b/255;
>      let r_prim = 255 * (r_norm/255)^(1/2.2)
>      let g_prim = 255 * (g_norm/255)^(1/2.2)
>      let b_prim = 255 * (b_norm/255)^(1/2.2)
>      let y_norm = 0.2126 * r_prim + 0.7152 * g_prim + 0.0722 * b_prim
>      let y = y_norm*255;
>      let grayColor = color(y, y, y);
>      pixels[i] = red(grayColor);
>      pixels[i + 1] = green(grayColor);
>      pixels[i + 2] = blue(grayColor);
>      pixels[i + 3] = alpha(grayColor)
>    }
>   updatePixels();
> }

## Arte ASCII


> :P5 width=350, height=450
>
> let img;
> function preload(){
>   img = loadImage('/vc/docs/sketches/tree.jpg');
>}
> function setup() {
>   createCanvas(350, 450);
>   image(img, 0, 0,width,height);
> }


> :P5 width=350, height=450
>
>let img;
>let total = 0;
>
>
>function preload() {
> img = loadImage('/vc/docs/sketches/tree.jpg');
>}
>function setup() {
>  createCanvas(350,450);
>  background(255);
>  fill(0);
>  textFont("Courier", 6);
>  img.resize(width,height);
>  img.filter(GRAY);
>  img.loadPixels();
>  
>  let i = 0;
>  
>  for (let y = 0; y < height; y += 8) {
>    for (let x = 0; x < width; x += 8) {
>      let pixel = img.pixels[(y * img.width + x)];
>      let r = red(pixel);
>      let g = green(pixel);
>      let b = blue(pixel);
>      total = total + r + g + b;
>      i++;
>    }
>  }
>  
>  total = total / i;
>  for (let y = 0; y < height; y += 2) {
>    for (let x = 0; x < width; x += 2) {
>        let pixel = img.pixels[4*(y * img.width + x)];
>        let r = red(pixel);
>        let g = green(pixel);
>        let b = blue(pixel);
>        let S=r+g+b;
>        S = S/total;
>        if (S<0.15){
>          text("@", x, y);
>        }
>        else if (S<0.30){
>          text("#", x, y);
>        }
>        else if (S<0.45){
>          text("M", x, y);
>        }
>        else if (S<0.60){
>          text("H", x, y);
>        }
>        else if (S<0.75){
>          text("L", x, y);
>        }
>        else if (S<1){
>          text("i", x, y);
>        }
>        else if (S<1.15){
>          text(":", x, y);
>        }
>        else if (S<=1.3){
>          text(".", x, y);
>        }
>    }
>  }
>}








> :ToCPrevNext
