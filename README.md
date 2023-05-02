Download Link: https://assignmentchef.com/product/solved-cop3502-assignment-4-reflections-and-kindred-spirits-2
<br>
This program is designed to get you thinking recursively with binary trees. Rather than solving one big problem, you will code up solutions to three smaller problems, each of which will rely on recursion to some degree.

This time around, I’m not giving you a slew of function definitions that essentially pre-define the structure of your program. Accordingly, this assignment will challenge you to think creatively, both in terms of how to solve the problems, as well as how to make appropriate use of helper functions as you plan out how to structure your code – especially with the <em>kindredSpirits()</em> function. This will be fun.

<strong>Deliverables</strong>

<em>KindredSpirits.c</em>

<strong><em>Note!</em></strong> The capitalization and spelling of your filename matter!

<strong><em>Note!</em></strong> Code must be tested on Eustis, but submitted via Webcourses.

<h1>1. Overview, Part 1 of 2: Reflections</h1>

Given two binary trees, we say that one is a reflection of the other if they are symmetric in terms of both their structure and their node values. For example, the following trees are reflections of one another:

<strong><em>Figure 1: </em></strong><em>Two trees that are reflections of one another.</em>

The following trees are <em>not</em> reflections of one another, because although they are symmetric images of one another <em>structurally</em>, they are not symmetric in terms of their <em>values</em>:

<strong><em>Figure 2: </em></strong><em>Two structurally symmetric trees that are not reflections of one another because they are lack symmetry with respect to their node values.</em>

Because the following binary trees are not structurally symmetric (and therefore they also cannot be symmetric in terms of the values contained in each node), they are not reflections of one another:

<strong><em>Figure 3: </em></strong><em>Structurally asymmetric trees cannot be reflections of one another.</em>

The following binary trees are reflections of one another:

<strong><em>Figure. 4: </em></strong><em>Two trees that are reflections of one another. They are perfect binary trees. They are also large and in charge.</em>

Recall that the tree above is a perfect binary tree. You might ask yourself, “Is it always the case that a perfect binary tree is a reflection of itself?” The answer is, “No!” Here’s a counterexample that shows that a perfect binary tree is not always a reflection of itself:

<strong><em>Figure 5: </em></strong><em>This perfect binary tree is not a reflection of itself. Despite its structural symmetry, it is not symmetric to itself with respect to its node values.</em>

Any binary tree with a single node is a reflection of itself. For example:

33              33

<strong><em>Figure 6: </em></strong><em>Two trees that are reflections of one another.</em>

However, it is <em>not</em> the case that all binary trees with a single node are reflections of one another. For example:

15              21

<strong><em>Figure 7: </em></strong><em>Two trees that are not reflections of one another, because they are not symmetric with respect to their values.</em>

Finally, note that the empty tree is a reflection of itself:

<strong><em>Figure 8:</em></strong><em> Two trees (both empty) that are reflections of one another.</em>

<em>This example is serene and beautiful, and brings with it an overwhelming sense that everything is going to be okay.</em>

<h1>2. Overview, Part 2 of 2: Kindred Spirits</h1>

We say that two binary trees are <em>kindred spirits</em> if the preorder traversal of one of the trees corresponds to the postorder traversal of the other tree. For example, the following trees are kindred spirits:

<strong><em>Figure 9:</em></strong><em> These trees are kindred spirits. The preorder traversal of the tree on the left is 23, 12, 5, 18, 71, 56, which corresponds to the postorder traversal of the tree on the right.</em>

Note that the trees above are still kindred spirits even if we swap their order:

<strong><em>Figure 10:</em></strong><em> These trees from Figure 9 are still kindred spirits, despite the fact that the preorder traversal of the tree on the right now matches the postorder traversal of the tree on the left, instead of the other way around.</em>

<h1>3. Binary Tree Node Struct (KindredSpirits.h)</h1>

You must use the node struct we have specified in KindredSpirits.h without any modifications. You will have to #include the header file in your KindredSpirits.c source file like so:

#include “KindredSpirits.h”

Note that the capitalization of KindredSpirits.c matters! Filenames are case sensitive in Linux, and that is of course the operating system we’ll be using to test your code.

The node struct is defined in KindredSpirits.h as follows:

typedef struct node

{    int data;

struct node *left, *right; } node;

<h1>4. Test Cases and the test-all.sh Script</h1>

As always, I’ve included several test cases, which show some ways in which I might test your code. These test cases are not comprehensive. You should also create your own test cases if you want to test your code comprehensively.

I’ve also included a script, test-all.sh, that will compile and run all test cases for you. Using the test-all.sh script on Eustis is the safest, most sure-fire way to make sure your code is working properly before submitting. To run the script on Eustis, type the following:

bash test-all.sh

<h1>5. Output</h1>

The functions you write for this assignment should not produce any output. If your functions cause anything to print to the screen, it might interfere with our test case evaluation. Be sure to disable or remove any printf() statements you have in your code before submitting this assignment.

<h1>6. Function Requirements</h1>

You have a lot of leeway with how to approach this assignment. There are only five required functions, and you may write helper functions as you see fit. For the kindredSpirits() function, you will likely need quite a few helper functions, and a good measure of creative thinking and/or cleverness.

Function descriptions for this assignment are included on the following page. Please do not include a main() function in your submission.

int isReflection(node *a, node *b);

<strong>Description:</strong> A function to determine whether the trees rooted at <em>a</em> and <em>b</em> are reflections of one another, according to the definition of “reflection” given above. This must be implemented recursively.

<strong>Returns:</strong> 1 if the trees are reflections of one another, 0 otherwise.

node *makeReflection(node *root);

<strong>Description:</strong> A function that creates a new tree, which is a reflection of the tree rooted at <em>root</em>. This function must create an entirely new tree in memory. As your function creates a new tree, it must <em>not </em>destroy or alter the structure or values in the tree that was passed to it as a parameter. Tampering with the tree rooted at <em>root </em>will cause test case failure.

<strong>Returns:</strong> A pointer to the root of the new tree. (This implies, of course, that all the nodes in the new tree must be dynamically allocated.)

int kindredSpirits(node *a, node *b);

<strong>Description:</strong> A function that determines whether the trees rooted at <em>a</em> and <em>b</em> are kindred spirits. (See definition of “kindred spirits” above.) The function must not destroy or alter the trees in any way. Tampering with these trees will cause test case failure.

<strong>Special Restrictions:</strong> To be eligible for credit, the worst-case runtime of this function cannot exceed O(<em>n</em>), where <em>n </em>is the number of nodes in the larger of the two trees being compared. This function must also be able to handle arbitrarily large trees. (So, do not write a function that has a limit as to how many nodes it can handle.) You may write helper functions as needed.

<strong>Returns:</strong> 1 if the trees are kindred spirits, 0 otherwise.

double difficultyRating(void);

<strong>Returns:</strong> A double indicating how difficult you found this assignment on a scale of 1.0 (ridiculously easy) through 5.0 (insanely difficult).

double hoursSpent(void);

<strong>Returns:</strong> A reasonable estimate (greater than zero) of the number of hours you spent on this assignment.

<em>The remaining pages of this document contain compilation instructions (pg. 7), style requirements (pg. 8), special restrictions and guidelines for your program (pg. 9), and grading criteria (pg. 9).</em>




<h1>Compilation and Testing (Linux/Mac Command Line)</h1>

To compile multiple source files (.c files) at the command line:

gcc KindredSpirits.c testcase01.c

By default, this will produce an executable file called a.out, which you can run by typing:

./a.out

If you want to name the executable file something else, use:

gcc KindredSpirits.c testcase01.c -o KindredSpirits.exe

…and then run the program using:

./KindredSpirits.exe

Running the program could potentially dump a lot of output to the screen. If you want to redirect your output to a text file in Linux, it’s easy. Just run the program using the following command, which will create a file called whatever.txt that contains the output from your program:

./KindredSpirits.exe &gt; whatever.txt

Linux has a helpful command called diff for comparing the contents of two files, which is really helpful here since we’ve provided several sample output files. You can see whether your output matches ours exactly by typing, e.g.:

diff whatever.txt output01.txt

If the contents of whatever.txt and output01.txt are exactly the same, diff won’t have any output:

<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="afdccacec1dcd5efcadadcdbc6dc">[email protected]</a>:~$ diff whatever.txt output01.txt <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="6f1c0a0e011c152f0a1a1c1b061c">[email protected]</a>:~$ _

If the files differ, it will spit out some information about the lines that aren’t the same. For example:

<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="9fecfafef1ece5dffaeaecebf6ec">[email protected]</a>:~$ diff whatever.txt output01.txt

1c1

&lt; fail whale &#x1f641;

—

&gt; Success!

<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="b6c5d3d7d8c5ccf6d3c3c5c2dfc5">[email protected]</a>:~$ _

<h1>Style Restrictions (<em>Super Important!</em>)</h1>

Please conform as closely as possible to the style I use while coding in class. To encourage everyone to develop a commitment to writing consistent and readable code, the following restrictions will be strictly enforced:

 Any time you open a curly brace, that curly brace should start on a new line.

 Any time you open a new code block, indent all the code within that code block one level deeper than you were already indenting.

 (<strong><em>New!</em></strong>) Be consistent with the amount of indentation you’re using, and be consistent in using either spaces or tabs for indentation throughout your source file. If you’re using spaces for indentation, please use at least two spaces for each new level of indentation, because trying to read code that uses just a single space for each level of indentation is downright painful.

 Please avoid block-style comments: /*<em> comment </em>*/

 Instead, please use inline-style comments: //<em> comment</em>

 Always include a space after the “//” in your comments: “// <em>comment</em>” instead of “//<em>comment</em>”

 The header comments introducing your source file should always be placed above your #include statements.

 Comments longer than three words should always be placed <em><u>above</u></em> the lines of code to which they refer. Furthermore, such comments should be indented to properly align with the code to which they refer. For example, if line 16 of your code is indented with two tabs, and line 15 contains a comment referring to line 16, then line 15 should also be intended with two tabs.

 Any libraries you <em>#include</em> should be listed <em>after</em> the header comment at the top of your file that includes your name, course number, semester, NID, and so on.

 Please do not write excessively long lines of code. Lines must be no longer than 100 characters wide.

 Avoid excessive consecutive blank lines. In general, you should never have more than one or two consecutive blank lines.

 When defining a function that doesn’t take any arguments, always put <em>void</em> in its parentheses. For example, define a function using <em>int do_something(void)</em> instead of <em>int do_something()</em>.

 Please leave a space on both sides of any binary operators you use in your code (i.e., operators that take two operands). For example, use <em>(a + b) – c</em> instead of <em>(a+b)-c</em>.

 When defining or calling a function, do not leave a space before its opening parenthesis. For example: use <em>int main(void)</em> instead of <em>int main (void)</em>. Similarly, use <em>printf(“…”)</em> instead of <em>printf (“…”)</em>.

 Do leave a space before the opening parenthesis in an <em>if</em> statement or a loop. For example, use use <em>for (i = 0; i &lt; n; i++)</em> instead of <em>for(i = 0; i &lt; n; i++)</em>, and use <em>if (condition)</em> instead of <em>if(condition)</em> or <em>if( condition )</em>.