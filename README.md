Download Link: https://assignmentchef.com/product/solved-csci3220-assignment-1-sequence-alignment
<br>
Aims: 1. Get familiar with concepts related to sequence alignment

<ol start="2">

 <li>Practice using dynamic programming to solve sequence alignment problems optimally</li>

 <li>Establish scientific rigor by cross-checking your results using multiple means</li>

</ol>

<strong>Description: </strong>

In this assignment, you will first use dynamic programming to solve optimal sequence alignment problems, both manually and by writing a computer program. You will then study ways to skip some entries in the dynamic programming table that would not affect the final results. Finally, you will go through some steps of FASTA on some example sequences.

The bonus part is for those who enjoy challenges. The maximum score you can get from this assignment is capped at 100, but doing this bonus part would give you a better chance of getting a high score.

<strong>Questions: </strong>

In Questions <strong>1-2</strong>, we will use a scoring scheme of having <strong>+2</strong> scores for a match, <strong>-1</strong> score for a mismatch, and <strong>-2</strong> scores for an indel <strong>without</strong> applying affine gap penalty.

<ol>

 <li>Fill in the following dynamic programming table to perform optimal <strong>global</strong> alignment between the sequences <em>r</em>=GTACC and <em>s</em>=CCTCC based on the scoring scheme stated above. Draw <strong>all arrows</strong> that lead to the score of each cell (i.e., only the “red arrows”). You can use the PowerPoint table template in the file CSCI3220_2018Fall_Assignment1_template.pptx if you want. Report the <strong>optimal alignment score</strong> and <strong>all</strong> <strong>alignments</strong> with this optimal score. When showing an alignment, indicate the names of the sequences clearly.</li>

 <li>Repeat Question 1 but perform a local alignment instead of a global alignment. When showing an alignment, indicate the sequence names <strong>and the starting and ending positions of the aligned regions</strong></li>

 <li>Write a computer program in C, C++, Java or Python for performing optimal pairwise <strong>global</strong> alignments of DNA sequences using dynamic programming, <strong>without</strong> affine gap penalty. Your program should take the following inputs from stdin (<strong>not</strong> from a file) in the specified order, each occupying a different line:</li>

 <li>Score for a match (a positive integer) ii. Score for a mismatch (a negative integer) iii. Score for an indel (a negative integer) iv. First DNA sequence (a text string)</li>

 <li>Second DNA sequence (a text string)</li>

</ol>

You do not need to check for errors in the inputs.

Your program should output to the screen (i.e., stdout) the <strong>highest alignment score</strong> and <strong>all optimal alignments</strong> in the following format:




&lt;Best alignment score&gt;&lt;line break&gt;

[&lt;line break&gt;

&lt;first sequence with gaps filled&lt;line break&gt;

&lt;second sequence with gaps filled&lt;line break&gt;]




The part in square brackets repeats for each optimal alignment. During the traceback, whenever a table entry has multiple incoming arrows, the horizontal one should be the first to traceback,

2

followed by the diagonal one, and finally the vertical one. <strong>The resulting optimal alignments in the output should also follow this order.</strong>




The non-comment portion of your program is expected to contain no more than 150 lines of code.




Here is a screen shot when a sample Java program called DP was run on an example from the lecture notes:




&gt;java DP

1

-1

-1

ATGCGT

ACGGCGT

3




A_TGCGT

ACGGCGT




AT_GCGT

ACGGCGT




ATG_CGT

ACGGCGT




Your program will be graded based on i) whether it can be compiled/run successfully, ii) whether it follows the input/output formats as specified above, iii) its accuracy on a number of test cases and iv) whether the program is well-documented with appropriate comments added to explain the meaning of the code. In view of the large size of our class, for easy grading, you may get zero score if your program cannot be compiled or it does not conform to the input/output formats specified.

Do not forget to use your program to check your answer to Question 1, and the examples in the lecture notes and tutorial notes.

<ol start="4">

 <li>In Question 1, we found the optimal global alignment(s) by filling in the whole dynamic programming table. However, given the specific scoring scheme we considered (+2 for a match, -1 for a mismatch and -2 for an indel), it is actually not necessary to fill in the whole table.</li>

</ol>

<ul>

 <li>List all the entries in the dynamic programming table that can never be involved in an optimal global alignment between any two length-5 sequences given the above scoring scheme. Explain why these entries can never be involved in an optimal global alignment. (Hint: Consider what score each table entry needs to achieve in order to be involved in an optimal alignment, and whether the entry can actually achieve this score.)</li>

 <li>Based on your answer in Part a, explain how the dynamic programming algorithm can be modified to skip the table entries that can never be involved in an optimal global alignment, assuming that the table is still a 6´6 two-dimensional array. Give as much specific detail as possible</li>

 <li>[Optional] Now we generalize the results in Part a to two sequences of any lengths |<em>r</em>|=<em>n</em> and |<em>s</em>|=<em>m</em>³<em>n</em>, and any reasonable scoring scheme without affine gap penalty. Specifically,</li>

</ul>

<ol start="2">

 <li>Repeat Question 1 but perform a local alignment instead of a global alignment. When showing an alignment, indicate the sequence names <strong>and the starting and ending positions of the aligned regions</strong></li>

 <li>Write a computer program in C, C++, Java or Python for performing optimal pairwise <strong>global</strong> alignments of DNA sequences using dynamic programming, <strong>without</strong> affine gap penalty. Your program should take the following inputs from stdin (<strong>not</strong> from a file) in the specified order, each occupying a different line:</li>

 <li>Score for a match (a positive integer) ii. Score for a mismatch (a negative integer) iii. Score for an indel (a negative integer) iv. First DNA sequence (a text string)</li>

 <li>Second DNA sequence (a text string)</li>

</ol>

You do not need to check for errors in the inputs.

Your program should output to the screen (i.e., stdout) the <strong>highest alignment score</strong> and <strong>all optimal alignments</strong> in the following format:

&lt;Best alignment score&gt;&lt;line break&gt;

[&lt;line break&gt;

&lt;first sequence with gaps filled&lt;line break&gt;

&lt;second sequence with gaps filled&lt;line break&gt;]

The part in square brackets repeats for each optimal alignment. During the traceback, whenever a table entry has multiple incoming arrows, the horizontal one should be the first to traceback,

consider a scoring scheme with a match score of <em>s</em><sub>match</sub>&gt;0, a mismatch score of <em>s</em><sub>mismatch</sub>&lt;0, and an indel score of <em>s</em><sub>indel</sub>&lt;<em>s</em><sub>mismatch</sub>. Derive a formula that determines whether the entry on the <em>i</em>-th row and <em>j</em>-th column (first row and first column counted as 1) in the dynamic programming table can never be involved in any optimal global alignment. Don’t forget to use the formula you obtain for this general case to verify your answer to the special case in

<ol start="5">

 <li>This question is about FASTA.</li>

</ol>

<ul>

 <li>Build a lookup table for the 2-mers in sequence <em>r</em>=ACGCGTCA. The table should be sorted by the 2-mers.</li>

 <li>Now you are given another sequence <em>s</em>=CCGTGCAC. List all maximal diagonal runs of length 2 or more in the dot plot of <em>r</em> and <em>s</em> by recording the starting and ending positions in <em>r</em> and <em>s</em> without actually making the plot. A diagonal run is maximal if it is not contained by another diagonal run.</li>

 <li>Suppose lookup(kmer) is a function that takes a k-mer as input and returns the list of all its occurrence locations in <em>r</em> as output. Give the pseudocode of an algorithm that can produce the output of Part b using this function.</li>

</ul>