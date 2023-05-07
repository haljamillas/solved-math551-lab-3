Download Link: https://assignmentchef.com/product/solved-math551-lab-3
<br>
<strong>Goals: </strong>We will use matrix multiplication in order to manipulate color of images and achieve different color effects.

<strong>To get started:</strong>

Create a new Matlab script file and save it as “lab03.m”.

Download the file “baboon.jpg” and save it in your working directory.

<strong>Matlab commands to learn: </strong>imread, imshow, size, figure, reshape, uint8, double, for… end

<strong>What you have to submit: </strong>The file lab03.m, which you will create during the lab session.

<h1>Reminders About the Grading Software</h1>

Remember, the labs are graded with the help of software tools. If you do not follow the instructions, you will lose points. If the instructions ask you to assign a value to a variable, you must <strong>use the variable name given in the instructions</strong>. If the instructions ask you to make a variable named x1 and instead you make a variable named x or X or X1 or any name other than x1, the grading software will not find your variable and you <em>will </em>lose points. Required variables are listed in the lab instructions in a gray box like this:

<h2>Variables: x1, A, q</h2>

At times you will also be asked to answer questions in a comment in your M-file. You must <strong>format your text answers correctly</strong>. Questions that you must answer are shown in gray boxes in the lab. For example, if you see the instruction

Q7: What does the Matlab command lu do? your file must contain a line similar to the following somewhere

% Q7: It computes the LU decomposition of a matrix.

The important points about the formatting are

<ul>

 <li>The answer is on a single line.</li>

 <li>The first characters on the line is the comment character %.</li>

 <li>The answer is labeled in the form Q<em>n</em>:, where <em>n </em>stands for the question number from the gray box.</li>

</ul>

If you do not format your answers correctly, the grading software will not find them and you <em>will </em>lose points.

<h1>INTRODUCTION</h1>

Have you ever wondered how Instagram color filters work? A color image can be represented by a matrix with the dimensions corresponding to the dimensions of the image. Each of the elements of this matrix contains the number (or numbers) representing the color of the corresponding pixel. If the image is a color image, then the color of the pixel is represented by three numbers {R,G,B} (Red, Green and Blue) with each number ranging from 0 to 255 (RGB system). In this project we will learn to manipulate these colors in order to obtain different color effects.

<h1>TASKS</h1>

<ol>

 <li>Start by loading the image into Matlab and displaying it on the screen by using the commands imshow and imread (type help imshow and help imread to learn about these commands.) Save the resulting array as ImJPG. You should see the image in the Figure 1.</li>

</ol>

<h2>Variables: ImJPG</h2>

Figure 1: The original image

<ol start="2">

 <li>Check the dimensions of the array ImJPG using the command [m,n,l]=size(ImJPG). Observe, that Matlab will return three numbers. Since the image is colored, the resulting array is three-dimensional. Among other things, Matlab allows operations on multidimensional arrays. The first two dimensions of the array ImJPG correspond to the horizontal and vertical dimensions (number of pixels) of the image, and the third dimension stores three numbers corresponding to the values of Red, Green, and Blue for each pixel. These three colors mixed together produce all other colors in the image. The values for Red, Green and Blue can range from 0 to 255, allowing us to create 256<sup>3 </sup>= 16<em>,</em>777<em>,</em>216 colors. That is more than an ordinary human eye can distinguish. In this project, we will be manipulating these three numbers to achieve various visual effects (similar color filters in Instagram).</li>

</ol>

<h2>Variables: m,n,l</h2>

<ol start="3">

 <li>First of all, let us look into amount of each of Red, Green, and Blue color in the image. To do this, let us extract individual layers or color channels from the image array. To obtain the red channel of color in the image, use the following command: redChannel = ImJPG(:,:,1);</li>

</ol>

Similarly, extract green and blue color channels and save them in the arrays greenChannel and blueChannel. Display each array in a separate figure using figure and imshow commands. Observe that individual color channels will be shown by Matlab as grayscale images. That is due to the fact that we have taken “layers” off of the matrix ImJPG and each of these layers individually looks like a two-dimensional array with numbers ranging from 0 to 255 aka like a grayscale image. If you did everything correctly, you should see three images like in Figure 2. The whiter the pixel appears on a particular color channel, the larger amount of that color is contained in that pixel. Other way around, the darker the area is, the less corresponding color is in that part of the image.

<h3>Variables: redChannel, greenChannel, blueChannel</h3>

Figure 2: Different color channels

<ol start="4">

 <li>Let us convert the original image to a grayscale image by using the following matrix:</li>

</ol>

GrayMatrix

This matrix produces an average of red, green, and blue for each pixel. Use the following code:

<table width="599">

 <tbody>

  <tr>

   <td width="27">1</td>

   <td width="572">GrayMatrix=[1/3 1/3 1/3; 1/3 1/3 1/3; 1/3 1/3 1/3];</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="572">for i = 1:m</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="572">for j = 1:n</td>

  </tr>

  <tr>

   <td width="27">4</td>

   <td width="572">PixelColor = reshape(double(ImJPG(i,j,:)),3,1);</td>

  </tr>

  <tr>

   <td width="27">5</td>

   <td width="572">ImJPGGray(i,j,:) = uint8(GrayMatrix*PixelColor);</td>

  </tr>

  <tr>

   <td width="27">6</td>

   <td width="572">end;</td>

  </tr>

  <tr>

   <td width="27">7</td>

   <td width="572">end;</td>

  </tr>

  <tr>

   <td width="27">8</td>

   <td width="572">figure;</td>

  </tr>

  <tr>

   <td width="27">9</td>

   <td width="572">imshow(ImJPGGray)</td>

  </tr>

 </tbody>

</table>

This code produces an array ImJPGGray. Observe the use of the commands reshape, uint8, double. For every pixel of the image, first, the color attributes (RGB) are extracted from the matrix ImJPG, then these color attributes are treated as a vector with three components [R,G,B], and finally, the color attributes are changed by multiplying the vector [R, G, B] by the filter matrix GrayMatrix on the left. The result is saved then as color attributes of the corresponding pixel in the array ImJPGGray. All the pixels of the array ImJPGGray have equal number of Red, Green, and Blue; this produces different shades of gray color. Observe that there are different ways to create a grayscale conversion, and this is just one of them.

<table width="417">

 <tbody>

  <tr>

   <td width="138">Variables: ImJPGGray</td>

   <td width="279"> </td>

  </tr>

  <tr>

   <td colspan="2" width="417">Q1: What do the uint8 and double commands do in the code above?</td>

  </tr>

 </tbody>

</table>

<ol start="5">

 <li>Modify the code above to produce a sepia conversion of the image. Instead of GrayMatrix use the following filter matrix, and reproduce the code above with this matrix:</li>

</ol>

<table width="243">

 <tbody>

  <tr>

   <td width="153"><sup> </sup>0<em>.</em>393SepiaMatrix = <sub> </sub>0<em>.</em>3490<em>.</em>272</td>

   <td width="44">0<em>.</em>769 0<em>.</em>6860<em>.</em>534</td>

   <td width="46">0<em>.</em>189 <sup></sup>0<em>.</em>168 <sub></sub>0<em>.</em>131</td>

  </tr>

 </tbody>

</table>

Save the result in the ImJPGSepia array and display this array using imshow command.

<h2>Variables: ImJPGSepia</h2>

<ol start="6">

 <li>Next, consider the filter matrix</li>

</ol>

RedMatrix

Modify the code again, using the matrix above as a filter matrix. The result should look like the left image in Figure 3. Save the result as ImJPGRed. Display the image.

<h2>Variables: ImJPGRed</h2>

Q2: What does the transformation (i.e. multiplying by the matrix RedMatrix) do to the image?

<ol start="7">

 <li>Now let us delete one of the colors in the image, say red. First, produce the matrix which deletes red color in the image and keeps the values of Green and Blue the same. Use it to filter the image. The result should look like the right image in Figure 3. Save the result as ImJPGDeleteRed.</li>

</ol>

<h3>Variables: ImJPGDeleteRed</h3>

Figure 3: Left: Multiplying by RedMatrix. Right: Red color deleted

<ol start="8">

 <li>Let us permute the colors in the image. To do this repeat the steps above with the matrix:</li>

</ol>

PermuteMatrix

Save the result as ImJPGPermute. If you did correctly, you should see the image in Figure 4.

<h3>Variables: ImJPGPermute</h3>

Figure 4: Colors permuted

The matrix PermuteMatrix is an example of hue rotation filter. You can produce other hue rotation effects with this more general transformation:

<table width="517">

 <tbody>

  <tr>

   <td width="195">HueRotationMatrix</td>

   <td width="44">0<em>.</em>715 0<em>.</em>7150<em>.</em>715</td>

   <td width="162"></td>

   <td width="54">−0<em>.</em>715 0<em>.</em>285−0<em>.</em>715</td>

   <td width="62"></td>

  </tr>

  <tr>

   <td width="195"> </td>

   <td width="44"> </td>

   <td width="162"></td>

   <td width="54">−0<em>.</em>7150<em>.</em>1400<em>.</em>715</td>

   <td width="62"><em> .</em></td>

  </tr>

 </tbody>

</table>

Here <em>θ </em>is the angle of rotation. You can try experimenting with various values of the angle <em>θ </em>to get different color effects.

<ol start="9">

 <li>It is also possible to amplify/deamplify individual colors in the image. For instance, consider the color transformation with the matrix:</li>

</ol>

SaturateMatrix

Modify the code with matrix SaturateMatrix. Save the result as ImJPGSaturate.

<h3>Variables: ImJPGSaturate</h3>

Q3: What does the transformation above do to the image?

<ol start="10">

 <li>It is possible to invert the colors of the image by using the following code:</li>

</ol>

<table width="599">

 <tbody>

  <tr>

   <td width="27">1</td>

   <td width="572">ImJPGInvert=255-ImJPG;</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="572">figure;</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="572">imshow(ImJPGInvert);</td>

  </tr>

 </tbody>

</table>

Observe that here again Matlab automatically substitutes matrix of appropriate dimension (in this case <em>m </em>× <em>n </em>× <em>l</em>) with all the elements equal to 255 instead of the constant 255.

<h3>Variables: ImJPGInvert</h3>