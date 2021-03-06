Word Ripper
========================================================
author: Winston A Saunders
date: April 12, 2015

Language Model Advantages:
- _Scalable_ to large and multiple corpora for improved fidelity.
- _Toolkit_ reduces to term frequency tables for minimized client overhead.

Word Ripper Toolkit Use Instructions
========================================================

- Corpus-RippeR _to create computable text samples from very large corpora._    
- n-gram-creatoR _to build individual n-gram frequency tables_  
- n-gram-reduceR _to combine & reduce mulitple n-gram tables._
- Markov-CalculatoR _ to tabulate conditional probabilities._
- Word-RippeR _Web based interface providing_ __context__ _or nearest_ __word__ _based predictions._  
  
__Agile, flexible, and compact Natural Language Prediction.__
        
Algorithm Description
========================================================

The __Word-Match Algorithm__ as the following steps:  
1. Extract last three words from text string.  
2. Count matches to four-gram "stems".  
3. Repeat for three- and two-grams.  
4. Calculate conditional probabilities and sort results.   
5. Select highest probability/highest order matched n-gram as best match.  

The __Context Match Algorithm__ works similarly, except stop words are removed from the n-grams. 

Compact Markov n_grams
========================================================

Prediction is based on n_gram frequencies stored as



```r
freq <- as.integer(2000*log10(word_count))
```

Faster interger addition and subraction



<!-- html table generated in R 3.1.3 by xtable 1.7-4 package -->
<!-- Mon Apr 20 09:09:39 2015 -->
<table border=1>
<tr> <th>  </th> <th> n_gram </th> <th> frequency </th> <th> stem </th> <th> root </th> <th> root_freq </th>  </tr>
  <tr> <td align="right"> 51 </td> <td> you have a </td> <td align="right"> 3047 </td> <td> you have </td> <td> a </td> <td align="right"> 5554 </td> </tr>
  <tr> <td align="right"> 52 </td> <td> the united states </td> <td align="right"> 3041 </td> <td> the united </td> <td> states </td> <td align="right"> 3564 </td> </tr>
  <tr> <td align="right"> 53 </td> <td> rest of the </td> <td align="right"> 3031 </td> <td> rest of </td> <td> the </td> <td align="right"> 5855 </td> </tr>
  <tr> <td align="right"> 54 </td> <td> if you are </td> <td align="right"> 3031 </td> <td> if you </td> <td> are </td> <td align="right"> 4869 </td> </tr>
  <tr> <td align="right"> 55 </td> <td> to make a </td> <td align="right"> 3027 </td> <td> to make </td> <td> a </td> <td align="right"> 5554 </td> </tr>
  <tr> <td align="right"> 56 </td> <td> it will be </td> <td align="right"> 3022 </td> <td> it will </td> <td> be </td> <td align="right"> 4914 </td> </tr>
   </table>


Example Results
=============================================


  
__phrase__: You cook the best food I have ever  ...   
  ...seen  __(word based prediction)__    
  ...experienced  __(context based prediction)__   


<!-- html table generated in R 3.1.3 by xtable 1.7-4 package -->
<!-- Mon Apr 20 09:09:52 2015 -->
<table border=1>
<tr> <th>  </th> <th> n_gram </th> <th> stem </th> <th> root </th> <th> log conditional prob </th>  </tr>
  <tr> <td align="right"> 8154 </td> <td> have ever seen </td> <td> have ever </td> <td> seen </td> <td align="right"> -1964 </td> </tr>
  <tr> <td align="right"> 25907 </td> <td> have ever been </td> <td> have ever </td> <td> been </td> <td align="right"> -3371 </td> </tr>
  <tr> <td align="right"> 27484 </td> <td> have ever had </td> <td> have ever </td> <td> had </td> <td align="right"> -3505 </td> </tr>
   </table>
<!-- html table generated in R 3.1.3 by xtable 1.7-4 package -->
<!-- Mon Apr 20 09:09:52 2015 -->
<table border=1>
<tr> <th>  </th> <th> n_gram </th> <th> stem </th> <th> root </th> <th> log conditional prob </th>  </tr>
  <tr> <td align="right"> 53363 </td> <td> ever experienced </td> <td> ever </td> <td> experienced </td> <td align="right">   0 </td> </tr>
  <tr> <td align="right"> 107481 </td> <td> ever encountered </td> <td> ever </td> <td> encountered </td> <td align="right"> -636 </td> </tr>
  <tr> <td align="right"> 3855 </td> <td> ever seen </td> <td> ever </td> <td> seen </td> <td align="right"> -1139 </td> </tr>
   </table>

   
