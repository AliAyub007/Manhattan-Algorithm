# Manhattan Algorithm (3D)

Imagine seeking a path from a given source to given destination in a Manhattan-like city grid.
How many path there are to arrive to point a to point b?

This variant assumes that that the grid is a 3D space

ANSWER:

(define manhattan-3d<br/>               
&emsp;(lambda (i j k)<br/>
&emsp;&emsp;(cond<br/>
&emsp;&emsp;&emsp;((and (= j 0) (= k 0)) 1)<br/>
&emsp;&emsp;&emsp;((and (= j 0) (= i 0)) 1)<br/>
&emsp;&emsp;&emsp;((and (= k 0) (= i 0)) 1)<br/>
 &emsp;&emsp;&emsp;((= i 0) (+  (manhattan-3d i (- j 1) k)<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;   (manhattan-3d i j (- k 1))))<br/>
&emsp;&emsp;&emsp;((= k 0) (+  (manhattan-3d i (- j 1) k)<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;   (manhattan-3d (- i 1) j k)))<br/>
&emsp;&emsp;&emsp;((= j 0) (+  (manhattan-3d i j (- k 1))<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;   (manhattan-3d (- i 1) j k)))<br/>
&emsp;&emsp;&emsp;(else<br/>
&emsp;&emsp;&emsp;   (+  (manhattan-3d i (- j 1) k)<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;(manhattan-3d (- i 1) j k)<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;(manhattan-3d i j (- k 1))))<br/>
&emsp;&emsp;)<br/>
&emsp;)<br/>
)<br/>

(manhattan-3d 0 0 7) ;1
(manhattan-3d 2 0 2) ;6
(manhattan-3d 1 1 1) ;6
(manhattan-3d 1 1 5) ;42
(manhattan-3d 2 3 1) ;60
(manhattan-3d 2 3 3) ;560