Download Link: https://assignmentchef.com/product/solved-ece467-project-1-implement-a-text-categorization-system
<br>
For this project, you will implement a text categorization system. I recommend that you use one of the three machine learning methods for text categorization that we covered in class. You are free, however, to implement the system in any way that you choose as long as you implement the crux of the algorithm yourself. You are allowed to use available NLP resources that are not specifically related to text categorization, machine learning, or word statistics. For example, you may use an existing tokenizer or part-of-speech tagger if you find one that is compatible with your system. Assuming you program in Python (which I also recommend), you may use NLTK. However, you may not use any pre-existing routine (from NLTK or any other library) that calculates word statistics or that applies text categorization or a machine learning approach.




Your program must allow the user to specify the names of two input files. The first will contain a list of labeled training documents. Each row of the file will list the relative path and filename of one training document followed by a single space and then the category of the document. The system should use these training documents to train itself appropriately so that it can predict the labels of future documents according to the learned categories. The second file will contain a list of unlabeled test documents. Each row will consist of a single string representing the relative path and filename of one test document. The program should loop through the indicated test documents and categorize each one based on how it has been trained. After all of the predictions have been made, the program should allow the user to specify the name of one output file. This file should list the test documents along with their predicted labels; the file format should be same as the format of the training file. <em>Do not assume any specific file or folder names.</em>




If you wish, you may separate the training and testing into two separate programs. The disadvantage of this would be that your training program would need to save all of its learned statistics in a file, and the test program would have to reload this information. (If you choose to do this, you should have both programs prompt the user for the name of this file.) The advantage is that this would allow you to train your system once for a set of categories, and then using the saved representation of your trained system, you could evaluate the trained system on multiple test sets without having to retrain it. Since training is much more computationally intensive than testing, this can be very beneficial in practice; but for this project, it is optional.




To test your programs, I am providing you with one entire corpus, including a training set and a test set. This corpus involves the categorization of news documents into the categories: Str (<em>Struggle</em>), Pol (<em>Politics</em>), Dis (<em>Disaster</em>), Cri (<em>Crime</em>), or Oth (<em>Other</em>). It is guaranteed that each document belongs to exactly one of these categories (i.e., the categories are mutually exclusive and exhaustive). I am also provided you with just the training sets (but not the test sets) for two other corpora. The second corpus involves the categorization of images based on the first sentences of their captions into the mutually exclusive and exhaustive categories: O (<em>Outdoor</em>) or I (<em>Indoor</em>). The third corpus involves the categorization of news documents into the mutually exclusive and exhaustive categories: Wor (<em>World News</em>), USN (<em>U.S. News</em>), Sci (<em>Science and Technology</em>), Fin (<em>Finance</em>), Spo (<em>Sports</em>), or Ent (<em>Entertainment</em>).




Note that I am only providing the training sets for two of the corpora. (I have separate test sets for these corpora that I will use for my evaluation.) Since I am not providing you these test sets, you should use one of the methods discussed in class to evaluate your system for these corpora; i.e., you can either divide the training set into a smaller training set and a tuning set, or you can use k-fold cross-validation. You should never include any documents in both the training set and the test set for a single experiment; that would likely lead to an unreasonably high estimate of future accuracy. However, using either a tuning set or cross-validation should give you a reasonable idea as to what sort of accuracy to expect when I run the system on my test sets. (If you tune parameters, improving accuracy as you go, the estimate still might be a bit high.)




I will post a file on the course website called TC_provided.tar.gz. If you download this file to a Linux system or to a Windows system with Cygwin, you can extract the contents by typing “gunzip TC_provided.tar.gz” and then “tar -xvf TC_provided.tar”. This will create a directory called TC_provided. The contents of this directory will include the following files:

<ul>

 <li>labels: This file contains the list of labeled training files for corpus 1. Note that there are 885 training documents, and the 5 categories are not represented equally (there are 282 Str, 243 Pol, 207 Dis, 100 Cri, and 53 Oth documents).</li>

 <li>list: This file contains the list of 443 test files for corpus 1.</li>

 <li>labels: This file contains the list of labeled test files for corpus 1. I am providing this to you so that you can evaluate your text categorization system after applying it to the files listed in corpus1_test.list.</li>

 <li>labels: This file contains the list of labeled training files for corpus 2. Note that there are 894 training documents including 621 with category O and 273 with category I.</li>

 <li>labels: This file contains the list of labeled training files for corpus 3. Note that there are 955 training documents, and the 6 categories are not represented equally (there are 338 Wor, 245 USN, 124 Sci, 114 Fin, 92 Spo, and 42 Ent documents).</li>

</ul>




There are also 3 folders called corpus1, corpus2, and corpus3. Within corpus1, you will find both the training and test documents. Within corpus2 and corpus3, you will find only the training documents. Of course, I have test sets for all three corpora. I can tell you that in all cases, files were distributed randomly between the training and test sets, so while the relative sizes of categories in the test set will not be identical to the training set, you can expect them to be similar. Also, in all three cases, approximately 1/3 of the documents were placed in the test set.




I have also provided, in the root directory, a file called analyze.pl, a Perl script that I wrote to compare the output of your text categorization system to a file with the actual labels for the test set. You can use this directly to evaluate your system’s results for corpus1. For example, if you name your output file “corpus1_predictions.labels” for corpus1, you can type the following (assuming Perl is installed on your system):




perl analyze.pl corpus1_predictions.labels corpus1_test.labels




If your output file is in the correct format, this will display a confusion matrix indicating the breakdown of correct and incorrect predictions according to categories, with columns indicating actual categories and rows indicating predictions. You will also see reported the precision, recall, and F1 measures for each category, as well as the overall accuracy of the system.




A user-friendly text categorization system should not assume specific categories; it should learn them from the training set that it is provided. However, you may assume that your system will only be applied to the sets of categories mentioned in this document, and you may hardcode them into your system if you wish. In any case, you should not require the user to indicate which set of categories is being used. If you decide to hardcode the categories, your system should still figure out which of the three sets of categories it is dealing with based on the training set. (Of course, you also have the option of creating a general system which detects all of the categories based on the training set.) Also, I don’t think I should have to specify this, but for the first corpus, you may not hardcode the answers for any specific documents, nor may you include rules that are in any way specific to the examples in the test set. Doing something like that would invalidate the evaluation for that corpus.




<em>Your project may be written in any language, as long as I can run it easily using Cygwin or Ubuntu, but I recommend using Python. </em>If you e-mail me your program early (at least two days before the deadline), I will test it on the three data sets and let you know the performance on the test sets (one of which is provided to you). You will then have an opportunity to improve your system and resubmit it if you are not satisfied. (Expect that it might take me a couple of days to reply to each presubmission.) Assuming that your program meets all of the requirements, the grade will largely depend on how well the system performs. I will also specifically consider the performance relative to other systems I have received over the years that have used the same sort of machine learning approach.




When you e-mail me your final project, I would also like a short writeup describing your system; one or two pages should be enough. The information provided in your writeup should include:

<ul>

 <li>Instructions explaining how to use your system (including how to compile the code, if necessary; what libraries I need to have installed, and how to install them; etc.).</li>

 <li>Which basic machine learning method did you use?</li>

 <li>How does your system tokenize training and test files?</li>

 <li>What weighting scheme, if any, is used for tokens?</li>

 <li>If you used Naïve Bayes, what method of smoothing is used?</li>

 <li>Which optional parameters or features did you experiment with (e.g., possibilities might include case sensitivity, POS tagging, stop lists, etc.)? Which parameters or features made a significant difference, and how are they set in your final system?</li>

 <li>How did you evaluate your system’s performance for the second and third data sets?</li>

 <li>You may include any additional information that you wish.</li>

</ul>