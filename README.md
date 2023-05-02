Download Link: https://assignmentchef.com/product/solved-comp9044-lab-7
<br>



Before the lab you should re-read the relevant lecture slides and their accompanying examples.

Create a new directory for this lab called lab07, change to this directory, and fetch the provided code for this week by running these commands:

$ <strong>mkdir lab07</strong>

$ <strong>cd lab07</strong>

$ <strong>2041 fetch lab07</strong>

Or, if you’re not working on CSE, you can download the provided code as a <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/07/provided.zip">zip</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/07/provided.zip">file</a> or a <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/07/provided.tar">tar</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/07/provided.tar">file</a>.

In these exercises you will work with a dataset containing sing lyrics.

This <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/total_words/lyrics.zip">zip</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/total_words/lyrics.zip">file</a> contains the lyrics of the songs of 10 well known artists.

<table width="961">

 <tbody>

  <tr>

   <td width="961">wget -q https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/total_words/lyrics.zip unzip lyrics.zipArchive:  lyrics.zip    creating: lyrics/   inflating: lyrics/David_Bowie.txt   inflating: lyrics/Adele.txt   inflating: lyrics/Metallica.txt   inflating: lyrics/Rage_Against_The_Machine.txt   inflating: lyrics/Taylor_Swift.txt   inflating: lyrics/Keith_Urban.txt   inflating: lyrics/Ed_Sheeran.txt   inflating: lyrics/Justin_Bieber.txt   inflating: lyrics/Rihanna.txt   inflating: lyrics/Leonard_Cohen.txt   inflating: song0.txt   inflating: song1.txt   inflating: song2.txt   inflating: song3.txt   inflating: song4.txt</td>

  </tr>

 </tbody>

</table>

The lyrics for each song have been re-ordered to avoid copyright concerns.

The zip file also contains lyrics from 5 songs where we don’t know the artists.

$ <strong>cat song0.txt</strong>

I’ve made up my mind,  Don’t need to think it over,

If I’m wrong I am right,

Don’t need to look no further,

This ain’t lust,

I know this is love but,




If I tell the world,

I’ll never say enough,

Cause it was not said to you,

And that’s exactly what I need to do,

If I’m in love with you,

$ <strong>cat song1.txt</strong>

Come Mr. DJ song pon de replay

Come Mr. DJ won’t you turn the music up

All the gal pon the dance floor wantin’ some more what

Come Mr. DJ won’t you turn the music up

$ <strong>cat song2.txt</strong>

And they say

She’s in the class A team

Stuck in her daydream

They are each from one of the artists in the dataset but they are not from a song in the dataset.

To start on this analysis write a Perl script total_words.pl which counts the total number of words found in its input (STDIN).

For the purposes of this program and the following programs we will define a word to be maximal non-empty contiguous sequences of alphabetic characters ([a-zA-Z]).

Any characters other than [a-zA-Z] separate words.

So for example the phrase “<sub>The soul’s desire</sub>” contains 4 words: (“The”, “soul”, “s”, “desire”) For example:

$ <strong>./total_words.pl &lt;lyrics/Justin_Bieber.txt</strong>

46589 words

$ <strong>./total_words.pl &lt;lyrics/Metallica.txt</strong>

38096 words

$ <strong>./total_words.pl &lt;lyrics/Rihanna.txt</strong>

53157 words

Hint: if your word counts are out a little you might be counting empty strings (split can return these). As usual:

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest total_words</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab07_total_words total_words.pl</strong>

before Tuesday 21 July 18 00 to obtain the marks for this lab exercise.

Write a Perl script count_word.pl which counts the number of times a specified word is found in its input (STDIN).

A word is as defined for the previous exercise.

The word you should count will be specified as a command line argument.

Your: program should ignore the case of words.

For example:

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>./count_word.pl death &lt;lyrics/Metallica.txt</strong> death occurred 69 times$ <strong>./count_word.pl death &lt;lyrics/Justin_Bieber.txt</strong> death occurred 0 times$ <strong>./count_word.pl love &lt;lyrics/Ed_Sheeran.txt</strong> love occurred 218 times$ <strong>./count_word.pl love &lt;lyrics/Rage_Against_The_Machine.txt</strong> love occurred 4 times</td>

  </tr>

 </tbody>

</table>

Hint: modify the code from the last exercise.

Hint: the Perl functions uc &amp; lc convert strings to lowercase &amp; uppercase respectively.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest count_word</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab07_count_word count_word.pl</strong>

before Tuesday 21 July 18 00 to obtain the marks for this lab exercise.

Write a Perl script frequency.pl which prints the frequency with which each artist uses a word specified as an argument. So if Justin Bieber uses the word “love” 493 times in the 46583 words of his songs, then its frequency is

493/46583 = 0.0105832599875491. For example:

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>./frequency.pl love</strong>165/ 16359 = 0.010086191 Adele189/ 34080 = 0.005545775 David Bowie218/ 18207 = 0.011973417 Ed Sheeran493/ 46589 = 0.010581897 Justin Bieber  217/ 27016 = 0.008032277 Keith Urban212/ 26192 = 0.008094075 Leonard Cohen57/ 38096 = 0.001496220 Metallica4/ 18985 = 0.000210693 Rage Against The Machine494/ 53157 = 0.009293226 Rihanna89/ 26188 = 0.003398503 Taylor Swift</td>

  </tr>

 </tbody>

</table>

So of these artists, Ed Sheeran uses the word “love” most frequently. If you choose a word a randomly from an Ed Sheeran song the probability it will be “love” is just over in 1 in a hundred (1%).

Make sure your Perl script produces exactly the output above (the printf format is “%4d/%6d = %.9f %s
”).

Note you should ignore case (change A-Z to a-z).

You should treat as a word any sequence of alphabetic characters.

You should treat non-alphabetic characters (characters other than a-z) as spaces.

Hint: use a hash table of hash tables indexed by artist and word to store the word counts.

Hint: this loop executes once for each .txt file in the directory lyrics.

foreach $file (glob “lyrics/*.txt”) {         print “$file
”;

}

Hint: reuse code from the last exercise.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest frequency</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab07_frequency frequency.pl</strong>

before Tuesday 21 July 18 00 to obtain the marks for this lab exercise.

Now suppose we have the song line “truth is beauty”. Given that David Bowie uses the word “truth” with frequency 0.000146727 and the word “is” with frequency 0.005898407, the word “beauty” with frequency 0.000264108; we can estimate the probability of Bowie writing the phrase “truth is beauty” as:

0.000146727 * 0.005898407 * 0.000264108 = 2.28573738067596e-10

We could similarly estimate probabilities for each of the other 9 artists, and then determine which of the 10 artists is most likely to sing “truth is beauty” (it’s Leonard Cohen).

<a href="https://en.wikipedia.org/wiki/Bag_of_words_model">A sidenote</a><a href="https://en.wikipedia.org/wiki/Bag_of_words_model">:</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">we</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">are</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">actually</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">making</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">a</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">large</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">simplifying</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">assumption</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">in</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">calculating</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">this</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">probability</a><a href="https://en.wikipedia.org/wiki/Bag_of_words_model">.</a><a href="https://en.wikipedia.org/wiki/Bag_of_words_model"> It</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">is</a><a href="https://en.wikipedia.org/wiki/Bag_of_words_model"> o</a><a href="https://en.wikipedia.org/wiki/Bag_of_words_model">ften</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">called</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">the</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">ba</a><a href="https://en.wikipedia.org/wiki/Bag_of_words_model">g</a><a href="https://en.wikipedia.org/wiki/Bag_of_words_model"> o</a><a href="https://en.wikipedia.org/wiki/Bag_of_words_model">f</a> <a href="https://en.wikipedia.org/wiki/Bag_of_words_model">words model</a><a href="https://en.wikipedia.org/wiki/Bag_of_words_model">.</a>

Multiplying probabilities like this quickly leads to very small numbers and may result in arithmetic underflow of our floating point representation. A common solution to this underflow is instead to work with the log of the numbers.

So instead we will calculate the the log of the probability of the phrase. You do this by adding the log of the probabilities of each word. For example, you calculate the log-probability of Bowie singing the phrase “Truth is beauty.” like this:

log(0.000146727) + log(0.005898407) + log(0.000264108) = -22.1991622527613 = log(2.28573738067596e-10)

Log-probabilities can be used directly to determine the most likely artist, as the artist with the highest log-probability will also have the highest probability.

Another problem is that we might be given a word that an artist has not used in the dataset we have. For example:

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>./frequency.pl fear</strong>2/ 16359 = 0.000122257 Adele13/ 34080 = 0.000381455 David Bowie0/ 18207 = 0.000000000 Ed Sheeran10/ 46589 = 0.000214643 Justin Bieber    0/ 27016 = 0.000000000 Keith Urban4/ 26192 = 0.000152718 Leonard Cohen39/ 38096 = 0.001023730 Metallica26/ 18985 = 0.001369502 Rage Against The Machine3/ 53157 = 0.000056437 Rihanna3/ 26188 = 0.000114556 Taylor Swift</td>

  </tr>

 </tbody>

</table>

It is not useful to assume there is zero probability that Ed Sheeran would use the word fear in a song even though he hasn’t used it previously.

You should avoid this when estimating probabilities by adding 1 to the count of occurrences of each word. So for example we’d estimate the probability of Ed Sheeran using the word fear as (0+1)/18205 and the probability of Metallica using the word fear as (39+1)/38082. This is a simple version of <a href="https://en.wikipedia.org/wiki/Additive_smoothing">Additive</a> <a href="https://en.wikipedia.org/wiki/Additive_smoothing">smoothin</a><a href="https://en.wikipedia.org/wiki/Additive_smoothing">g</a>.

Write a perl script log_probability.pl which given an argument prints the estimate log of the probability that an artist would use this word. For example:

$ <strong>./log_probability.pl fear</strong> log((2+1)/ 16359) =  -8.6039 Adele log((13+1)/ 34080) =  -7.7974 David Bowie log((0+1)/ 18207) =  -9.8096 Ed Sheeran log((10+1)/ 46589) =  -8.3512 Justin Bieber log((0+1)/ 27016) = -10.2042 Keith Urban log((4+1)/ 26192) =  -8.5638 Leonard Cohen log((39+1)/ 38096) =  -6.8590 Metallica log((26+1)/ 18985) =  -6.5556 Rage Against The Machine log((3+1)/ 53157) =  -9.4947 Rihanna log((3+1)/ 26188) =  -8.7868 Taylor Swift

You will only need to copy your frequency.pl and make a small modification. Make sure your output matches the above exactly (the printf format is <sub>“log((%d+1)/%6d) = %8.4f %s
”</sub>)

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest log_probability</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab07_log_probability log_probability.pl</strong>

before Tuesday 21 July 18 00 to obtain the marks for this lab exercise.

Write a Perl script identify_artist.pl that given 1 or more files, each containing part of song), prints the most likely artist to have sung those words.

In other words, for each file given as argument you should go through all (10) artists calculating the log-probability that the artist sung those words by summing the log-probability of that artist using each word in the file. You should print the artist with the highest log-probability.

Your program should produce exactly this output:

$ <strong>./identify_artist.pl song?.txt</strong> song0.txt most resembles the work of Adele (log-probability=-352.4) song1.txt most resembles the work of Rihanna (log-probability=-254.9) song2.txt most resembles the work of Ed Sheeran (log-probability=-206.6) song3.txt most resembles the work of Justin Bieber (log-probability=-1089.8) song4.txt most resembles the work of Leonard Cohen (log-probability=-493.8)

Hint: only read each file once. Store the data in a (2-dimensional) hash. If you read the files many times your program will be very slow and exceed autotest time limits.

You may find it helpful to add a ‘-d’ flag which provides debugging information (this is optional), for example:

$ <strong>./identify_artist.pl -d song2.txt</strong> song2.txt: log_probability of -206.6 for Ed Sheeran song2.txt: log_probability of -210.8 for Adele song2.txt: log_probability of -211.5 for Taylor Swift song2.txt: log_probability of -211.7 for Keith Urban song2.txt: log_probability of -215.0 for Leonard Cohen song2.txt: log_probability of -215.4 for Rage Against The Machine song2.txt: log_probability of -215.7 for David Bowie song2.txt: log_probability of -217.2 for Justin Bieber song2.txt: log_probability of -222.2 for Metallica song2.txt: log_probability of -223.4 for Rihanna

song2.txt most resembles the work of Ed Sheeran (log-probability=-206.6)

Hint: you may like to create simpler input to use in debugging, for example:

$ <strong>./log_probability.pl Andrew</strong> log((0+1)/ 16359) =  -9.7025 Adele log((0+1)/ 34080) = -10.4365 David Bowie log((0+1)/ 18207) =  -9.8096 Ed Sheeran log((0+1)/ 46589) = -10.7491 Justin Bieber log((0+1)/ 27016) = -10.2042 Keith Urban log((0+1)/ 26192) = -10.1732 Leonard Cohen log((0+1)/ 38096) = -10.5479 Metallica log((0+1)/ 18985) =  -9.8514 Rage Against The Machine log((0+1)/ 53157) = -10.8810 Rihanna log((0+1)/ 26188) = -10.1731 Taylor Swift

$ <strong>./log_probability.pl Rocks</strong> log((0+1)/ 16359) =  -9.7025 Adele log((10+1)/ 34080) =  -8.0386 David Bowie log((0+1)/ 18207) =  -9.8096 Ed Sheeran log((1+1)/ 46589) = -10.0560 Justin Bieber log((0+1)/ 27016) = -10.2042 Keith Urban log((0+1)/ 26192) = -10.1732 Leonard Cohen log((1+1)/ 38096) =  -9.8547 Metallica log((0+1)/ 18985) =  -9.8514 Rage Against The Machine log((2+1)/ 53157) =  -9.7824 Rihanna

Hint: if a word appears multiple times its log-probability needs to be summed multiple times.

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>cat echo.txt</strong> echo echo$ <strong>./log_probability.pl echo</strong> log((0+1)/ 16359) =  -9.7025 Adele log((0+1)/ 34080) = -10.4365 David Bowie log((0+1)/ 18207) =  -9.8096 Ed Sheeran log((0+1)/ 46589) = -10.7491 Justin Bieber log((0+1)/ 27016) = -10.2042 Keith Urban log((0+1)/ 26192) = -10.1732 Leonard Cohen log((0+1)/ 38096) = -10.5479 Metallica log((14+1)/ 18985) =  -7.1434 Rage Against The Machine log((0+1)/ 53157) = -10.8810 Rihanna log((1+1)/ 26188) =  -9.4799 Taylor Swift $ <strong>./identify_artist.pl -d echo.txt</strong> echo.txt: log_probability of -14.3 for Rage Against The Machine echo.txt: log_probability of -19.0 for Taylor Swift echo.txt: log_probability of -19.4 for Adele echo.txt: log_probability of -19.6 for Ed Sheeran echo.txt: log_probability of -20.3 for Leonard Cohen echo.txt: log_probability of -20.4 for Keith Urban echo.txt: log_probability of -20.9 for David Bowie</td>

  </tr>

 </tbody>

</table>

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest identify_artist</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab07_identify_artist identify_artist.pl</strong>

before Tuesday 21 July 18 00 to obtain the marks for this lab exercise.

Write a Perl program perl_print_n.pl which is given a two arguments, an integer n and a string.

If n is 1 it should output a Perl program which prints the string.

If n is 2 it should output a Perl program which prints a Perl program which prints a Perl program which prints the string.

If n is 2 it should output a Perl program which prints a Perl program which prints a Perl program which prints the string.

If n is 3 it should output a Perl program which prints a Perl program which prints a Perl program which prints a Perl program which prints a Perl program which prints the string.

And so on for any value of n.

For example:

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>./perl_print_n.pl 1 ‘Perl that prints Perl’</strong> print “Perl that prints Perl
”$ <strong>./perl_print_n.pl 2 ‘Perl that prints Perl that Prints Perl’|perl|perl</strong>Perl that prints Perl that Prints Perl$ <strong>./perl_print_n.pl 2 ‘Perl that ….’|perl|perl</strong> Perl that ….$ <strong>./perl_print_n.pl 4 ‘Andrew Rocks!’|perl|perl|perl|perl</strong> Andrew Rocks!$ <strong>./perl_print_n.pl 10 ‘I love COMP(2041|9044)!’|perl|perl|perl|perl|perl|perl|perl|perl|perl|perl</strong>I love COMP(2041|9044)!</td>

  </tr>

 </tbody>

</table>

You can assume n is a positive integer.

You can assume the string contains only ASCII characters.

You can not make other assumptions about the characters in the string.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest perl_print_n</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab07_perl_print_n perl_print_n.pl</strong>

before Tuesday 21 July 18 00 to obtain the marks for this lab exercise.

When you are finished each exercises make sure you submit your work by running give.

You can run give multiple times. Only your last submission will be marked.

Don’t submit any exercises you haven’t attempted.

If you are working at home, you may find it more convenient to upload your work via <a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">g</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">ive</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">‘</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">s</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">web</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">interface</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">.</a>

Remember you have until Tuesday 21 July 18 00 to submit your work.

You cannot obtain marks by e-mailing your code to tutors or lecturers.

You check the files you have submitted <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/student/">here</a>.

Automarking will be run by the lecturer several days after the submission deadline, using test cases different to those autotest runs for you. (Hint: do your own testing as well as running autotest.)

<a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">After</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">automarking</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">is</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">run</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">by</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">the</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">lecturer</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">you</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">can</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">view</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">y</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">our</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">results</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">here</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">.</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">The</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">resulting</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">mark</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">will</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">also</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">be</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">available</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">via</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">g</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">ive</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">‘</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">s</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">web interface</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">.</a>


