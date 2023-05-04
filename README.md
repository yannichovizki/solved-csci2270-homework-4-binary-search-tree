Download Link: https://assignmentchef.com/product/solved-csci2270-homework-4-binary-search-tree
<br>
OBJECTIVES

<ol>

 <li><strong>Insert nodes to build a binary search tree (BST) </strong></li>

 <li><strong>Search and Traverse a BST </strong></li>

 <li><strong>Delete nodes in a BST </strong></li>

 <li><strong>Perform a Rotate on your BST </strong></li>

</ol>

<strong> </strong>Background

In 2009, Netflix held a competition to see who could best predict user ratings for films based on previous ratings without any other information about the users or films. The grand prize of

US$1,000,000 was given to the BellKor’s Pragmatic Chaos team which bested Netflix’s own algorithm for predicting ratings by 10.06%. This kind of data science is facilitated with the application of good data structures. In fact, cleaning and arranging data in a conducive manner is half the battle in making successful predictions. Imagine you are attempting to predict user ratings given a dataset of IMDB’s top 100 movies. Building a binary search tree will enable you to search for movies and extract their features very efficiently. The movies will be accessed by their titles, but they will also store the following features:

<ul>

 <li>IMDB ranking (1-100)</li>

 <li>Title</li>

 <li>Year released</li>

 <li>IMDB average rating</li>

</ul>

Your binary search tree will utilize the following struct with default and overloaded constructors:

<table width="640">

 <tbody>

  <tr>

   <td width="640"><strong>struct </strong><strong>MovieItem</strong>{ int ranking; string title; int year; float rating;MovieItem* left = <strong>NULL</strong>;MovieItem* right = <strong>NULL</strong>; <strong>MovieItem</strong>(int rank, string t, int y, float r) { title = t; ranking = rank; year = y; rating = r;}};</td>

  </tr>

 </tbody>

</table>

<h2>MovieInventory Class</h2>

Your code should implement a binary search tree of MovieItem data type. A header file that lays out this tree can be found in <em>MovieInventory.hpp </em>on Moodle. As usual, <strong>DO NOT </strong>modify the header file. <em>You may implement helper functions in your .cpp file to facilitate recursion if you want as long as you don’t add those functions to the MovieInventory class</em>.

<strong>MovieInventory() </strong>

<ul>

 <li>Constructor: Initialize any member variables of the class to default</li>

</ul>




<strong>~MovieInventory() </strong>

<ul>

 <li>Destructor: Free all memory that was allocated</li>

</ul>




<h3>void printMovieInventory()</h3>

➔ Print every node in the tree in alphabetical order of titles using the following format:




<strong>// for every Movie node (m) in the tree</strong>

<strong>cout </strong>&lt;&lt; “Movie: ” &lt;&lt; m-&gt;title &lt;&lt; ” ” &lt;&lt; m-&gt;rating &lt;&lt; <strong>endl</strong>;




If there is no movie entry in the tree, print the following message instead:




<strong>cout </strong>&lt;&lt; “Tree is Empty. Cannot print” &lt;&lt; <strong>endl</strong>;

<h3> void addMovieItem(int ranking, std::string title, int year, float rating)</h3>

<ul>

 <li>Add a node to the tree in the correct place based on its <strong>title</strong>. Every node’s left children should come before it alphabetically, and every node’s right children should come after it alphabetically. <em>Hint: you can compare strings with &lt;, &gt;, ==, string::compare() function.</em></li>

</ul>

<em> </em>

<ul>

 <li><em>For example</em>, if the root node of the tree is the movie “Forrest Gump”, then the movie</li>

</ul>

“Iron Man” should be in the root’s right subtree and “Aladdin” should be in its left subtree.




<ul>

 <li>You can assume that no two movies have the same title</li>

</ul>

<strong> </strong>

<h3>void deleteMovieItem(std::string title)</h3>

➔ Delete the node that contains the title. <strong>When deleting a tree node with both children take the replacement from its in-order successor </strong>(min of the right sub-tree). If the movie does not exist in the data structure, print the following message




<strong>cout </strong>&lt;&lt; “Movie: ” &lt;&lt; title &lt;&lt; ” not found, cannot delete.” &lt;&lt; <strong>endl</strong>;







<h3>void getMovie(string title)</h3>

➔ Find the movie with the given <strong>title</strong>, then print out its information:

<strong>cout </strong>&lt;&lt; “Movie Info:” &lt;&lt; <strong>endl;</strong> <strong>cout </strong>&lt;&lt; “==================” &lt;&lt; <strong>endl;</strong> <strong>cout </strong>&lt;&lt; “Ranking:” &lt;&lt; node-&gt;ranking &lt;&lt; <strong>endl; cout </strong>&lt;&lt; “Title :” &lt;&lt; node-&gt;title &lt;&lt; <strong>endl; cout </strong>&lt;&lt; “Year :” &lt;&lt; node-&gt;year &lt;&lt; <strong>endl; cout </strong>&lt;&lt; “rating :” &lt;&lt; node-&gt;rating &lt;&lt; <strong>endl;</strong>

<sub>                                                </sub>

If the movie isn’t found, print the following message instead:

<strong>cout </strong>&lt;&lt; “Movie not found.” &lt;&lt; <strong>endl</strong>;




<h3> void searchMovies(float rating, int year)</h3>

➔ Print all the movies whose rating is at least as good as the input parameter <strong>rating </strong>and that are newer than <strong>year </strong>in the <strong>in-order </strong>fashion using the following format:




<strong>cout </strong>&lt;&lt; “Movies that came out after ” &lt;&lt; year &lt;&lt; ” with rating at least ” &lt;&lt; rating &lt;&lt; “:” &lt;&lt; <strong>endl</strong>;

<strong>// each movie that satisfies the constraints should be printed with </strong><strong>cout </strong>&lt;&lt; m-&gt;title &lt;&lt; “(” &lt;&lt; m-&gt;year &lt;&lt; “) ” &lt;&lt; m-&gt;rating &lt;&lt; <strong>endl</strong>;




If there is no movie entry in the tree, print the following message instead:




<strong>cout </strong>&lt;&lt; “Tree is Empty. Cannot query Movies” &lt;&lt; <strong>endl</strong>;







<h3>void averageRating()</h3>

➔ Print the average rating for all movies in the tree. If the tree is empty, print 0.0. Use the following format:

<strong>cout </strong>&lt;&lt; “Average rating:” &lt;&lt; average &lt;&lt; <strong>endl</strong>;







If there is no movie entry in the tree, print the following message instead:




<strong>cout </strong>&lt;&lt; “Average rating:0.0” &lt;&lt; <strong>endl</strong>;




<h3>void leftRotate(std::string title)</h3>

<strong> </strong>

➔ Rotate the node with the given <strong>title</strong> towards the left. Refer to the following illustration. A left rotation is performed at node <strong>x. </strong>

<ul>

 <li>After the rotation, the parent of <strong>x </strong>now becomes the parent of <strong>y</strong>. <strong>y </strong>becomes parent of <strong>x</strong>.</li>

 <li>Set the children pointers: Three children pointers are modified. i) The left subtree of <strong>y </strong>becomes the right subtree of <strong>x</strong>. ii) <strong>x </strong>and it’s left descendants become the left subtree of <strong>y</strong>, with <strong>x </strong>as the left child. iii) If <strong>x </strong>was the left (or right) child of <strong>xp </strong>before the rotation, make <strong>y </strong>the left (or right) child of <strong>xp </strong>after rotation accordingly. This can be implemented by comparing the titles of <strong>y </strong>and <strong>xp</strong>: if <strong>title </strong>&lt; <strong>xp.title</strong>, make <strong>y </strong>the left child of <strong>xp</strong>, else make <strong>y </strong>the right child of <strong>xp</strong>. A less riskier approach is to keep track of whether <strong>x </strong>was the left child or the right child before the rotation, and make <strong>y </strong>the left or the right child accordingly.</li>

 <li>Take care of the boundary cases: i) If <strong>x </strong>was the root before rotation, make <strong>y </strong>the new root. ii) If <strong>x </strong>does not have a right child, don’t perform any rotation.</li>

</ul>
















<h3><u> Driver</u></h3>

<strong> </strong>

For this assignment, the driver code has been provided to you in the <em>Driver.cpp </em>file. The main function will read information about each movie from a CSV file and store that information in a MovieInventory using your <strong>addMovieItem </strong>function implementation.

<strong>The name of the CSV file with this information should be passed in as a command-line argument. </strong>Example files are <em>Movies.csv</em>, <em>Documentaries.csv </em>on Moodle in the format:




&lt;Movie 1 ranking&gt;,&lt;Movie 1 title&gt;,&lt;Movie 1 year&gt;,&lt;Movie 1 rating&gt;

&lt;Movie 2 ranking&gt;,&lt;Movie 2 title&gt;,&lt;Movie 2 year&gt;,&lt;Movie 2 rating&gt; Etc…

<em>Note: For autograding’s sake, insert the nodes to the tree in the order they are read in</em>.




After reading the information on each movie from the file and building the tree, the user is displayed the following menu:




======Main Menu======

<ol>

 <li>Find a movie</li>

</ol>




<ol start="2">

 <li>Search movies</li>

 <li>Print the inventory</li>

 <li>Average Rating of movies</li>

</ol>




<ol start="5">

 <li>Delete movie</li>

</ol>




<ol start="6">

 <li>Rotate movies around</li>

 <li>Quit</li>

</ol>










The menu options have the following behavior:

<ul>

 <li><strong>Find a movie: </strong>Calls your tree’s <strong>getMovie </strong>function on a movie specified by the user. The user is prompted for a movie title.</li>

</ul>




<strong>cout </strong>&lt;&lt; “Enter a movie title:” •          &lt;&lt; <strong>endl</strong>;




<ul>

 <li><strong>Search movies: </strong>Calls your tree’s <strong>searchMovies </strong>function on a rating and year specified by the user. Prompts the user for a rating and year.</li>

</ul>

<table width="550">

 <tbody>

  <tr>

   <td width="550"><strong>cout </strong>&lt;&lt; “Enter a minimum rating:” &lt;&lt; <strong>endl</strong>;<strong>// get user input </strong><strong>cout </strong>&lt;&lt; “Enter a minimum year:” &lt;&lt; <strong>endl</strong>;</td>

  </tr>

 </tbody>

</table>




<ul>

 <li><strong>Print the inventory: </strong>Call your tree’s <strong>printMovieInventory </strong>function</li>

</ul>




<h4>● Average Rating of movies: Calls your tree’s averageRating function</h4>




<ul>

 <li><strong>Delete movie</strong>: Calls your <strong>deleteMovieItem </strong>function on a movie specified by the user. The user is prompted for a movie title.</li>

</ul>




<ul>

 <li><strong>cout </strong>&lt;&lt; “Enter a movie title:” &lt;&lt; <strong>endl</strong>;</li>

</ul>




<ul>

 <li><strong>Rotate movies around: </strong>Calls your <strong>leftRotate </strong>on a movie specified by the user.</li>

</ul>




<strong><em>Instructors: Ashraf, Godley </em></strong>

The user is prompted for a movie title, which is the title of the node the rotation is centered on.

<strong> </strong><strong>cout </strong>&lt;&lt; “Enter a movie title:” &lt;&lt; <strong>endl</strong>;

<strong> </strong>

<ul>

 <li><strong>Quit: </strong>Program exits after printing a friendly message to the user.</li>

</ul>

<strong>cout </strong>&lt;&lt; “Goodbye!” &lt;&lt; <strong>endl</strong>;










“Please note that once you are done with your assignment on Coderunner you need to click on ‘finish attempt’ and the ‘submit all and finish’. If you don’t do this, your submission will not get graded.”