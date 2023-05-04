Download Link: https://assignmentchef.com/product/solved-cs426-project-1-2
<br>






<h1>PART A: Compute Sum</h1>

The objective of the problem is to write a serial, then a parallel program that takes as input an array of integers, stored in an ASCII file with one integer per line, and prints out the sum of the elements in the file.




% cat input

1

24

9

% my_program input

34




You will write several versions of this program in serial and in MPI.




<ul>

 <li><strong>Serial: </strong>Write a serial program to solve this problem. Name the source code <sub>sum</sub>c.</li>

 <li><strong>MPIv1: </strong>Write an MPI implementation of the above program in which a master process reads in the entire input file and then dispatches pieces of it to workers, which these pieces being of as equal size as possible. The master must also perform computation. Each processor computes a local sum and results are then collected and aggregated by the master. This implementation should not use any collective communications, but only point-to-point. Name the source file <sub>sum-mpi-ppv1.c</sub>.</li>

 <li><strong>MPIv2: </strong>This is similar to MPIv1 except that all processors should have the computed overall sum. In this implementation, you are expected to use collective communication features of MPI.(MPI_Allreduce()/MPI_Bcast()) Name the source file <sub>sum-mpi</sub>c.</li>

</ul>

<h1>PART B: MM <sub> </sub></h1>

The objective of this problem is to write a serial, then parallel program that takes as input two integer <strong>square</strong> matrices of same dimension, stored in ASCII files whose first line gives the number of rows, and in which each following line lists space-separated integer elements of each row. The program writes the matrix that is the product of the two input matrices to a file, in the same format as the input.




% cat mat1

3

2 4 5

5 2 3

1 4 2

% cat mat2

3

4 2 1

4 1 1

1 2 1

% my_program mat1 mat2 mat3

% cat mat3

3

29 18 11

31 18 10

22 10 7




<ul>

 <li><strong>Serial: </strong>Write a serial program called <sub>matmult-serial.c.</sub></li>

 <li><strong>MPI: </strong>Write an MPI implementation of the matrix multiply program in which a master process read in both input files and then dispatches it to workers. <strong>The master must perform computation as well</strong>. Assume that the number of processors used is a perfect square (4, 9, etc.), and that the matrix dimensions are perfectly divisible by the square root of the number of processors (e.g., if matrices are 30×30, then we use 9 processors). The processors are thought of, logically, as organized in a 2-D “processor grid”.</li>

</ul>

In this implementation, the master partitions the first input matrix in blocks of rows, and the second matrix in blocks of columns. Row-blocks (resp. column-blocks) should contain the same number of rows (resp. columns). This is called a 1-D block distribution, and is illustrated on the figure below.




As seen in the figure, each processor computes the product of one block-row by one blockcolumn, and returns the result to the master. The master then writes the output file. Name this source code matmult-mpi-1d.c.







<strong>           </strong>


