# HouseholderQR
Householder QR Decomposition

Many problems in real life will be transformed into a linear system. There usually are two approaches to solve the linear system:

Iterative Method and Direct Method

The key for the success of iterative method is to build a good preconditioner after matrix reordering. Sometimes it may converge to 
the solution very slow for nearly singular matrix.

The key for the success of direct method is the stability and memory constraints. For good matrix like SPD matrix, a cholesky decomposition
could be good enough since no stability issues. But for general matrix, usually we can do LU or QR decomposition. The LU decomposition is not
quite stable and will need full / partial pivoting. The QR decomposition especially with the Householder transformation is much stabler for 
nonsingular matrix. The problem is it may needs many memory for large scale sparse matrix. A good reordering strategy is needed for Householder
QR. For symmetric matrix, the Reverse Cuthill-Mckee algorithm could be good enough for the first try. For unsymmetric matrix, an approximate
minimal degree algorithm or dissection algorithm could be needed for better memory consumation.

After tried a few iterative methods like gmres/lanczos/cg preconditioned with ilu,amg etc., I decided to work on the 
sparse Householder QR decomposition for its stability.

I spent lots of time on this project using Python and finally finished the coding and make it work for large sparse matrix. There still have some 
rooms to improve like using multiproccsing / joblib for parallel, testing different matrix ordering algorithms (could not find good packages in Python).

There are a few tests on ill conditioned matrices in HouseholderQR/HStoneQR_test. The largest size is (62424, 62424) with 1,717,763 nonzero entries for 
matrix "Simon/venkat25". https://sparse.tamu.edu/Simon/venkat25 . The absolute error is 1.3314367399876832e-14 which is quite good and it takes 1Gb memory 
and ~87 seconds in a windows desktop with i7-10700T @ 2.00 GHz and 16GB RAM. 

If you have some difficult linear system to solve and wanna give it a try, feel free to drop me an email at HStoneQR@gmail.com . 

HStoneQR

HStoneQR@gmail.com

