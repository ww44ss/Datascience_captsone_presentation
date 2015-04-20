Word RippeR     
========================================================
left: 60%
author: Winston A. Saunders
font-family: 'Helvetica'
date: April 19, 2015 
transition: rotate
   
  


***
![alt text](tactical.001.jpg)


Word Ripper Use Instructions
========================================================
 
__Toolkit:__      
- Corpus-RippeR:  <small>_creates computable text samples._</small>    
- n-gram-creatoR:  <small>_builds n-gram frequency tables_</small>  
- n-gram-reduceR:   <small>_combines & reduces mulitple n-gram tables._</small>

__Web Interface:__
- Word-RippeR:  <small>[Web based interface](https://ww44ss.shinyapps.io/Coursera_Shiny_Capstone/) _providing_ __context__ _or_ __nearest word__ _based predictions._</small>    
  
<center>__Agile, Flexible, and Compact Natural Language Prediction__</center>
        
Algorithm Description
========================================================

The __Word-Match Algorithm__ as the following steps:  
1. Extract last three words from text string.  
2. Count matches to four-gram "stems".  
3. Repeat for three- and two-grams.  
4. Calculate conditional probabilities and sort results.   
5. Select highest probability/highest order matched n-gram as best match.  

The __Context Match Algorithm__ works similarly, except stop words are removed from text and n-grams processing. 

Markov n-gram look-up tables
========================================================

Basing prediction on n-gram frequencies stored as integers


```r
freq <- as.integer(2000*log10(word_count))
```

give faster look-up based conditional probability



<!-- html table generated in R 3.1.3 by xtable 1.7-4 package -->
<!-- Mon Apr 20 14:10:28 2015 -->
<table border=1>
<tr> <th> n_gram </th> <th> frequency </th> <th> stem </th> <th> root </th> <th> root_freq </th>  </tr>
  <tr> <td> that it was </td> <td align="right"> 2766 </td> <td> that it </td> <td> was </td> <td align="right"> 4973 </td> </tr>
  <tr> <td> to do with </td> <td align="right"> 2955 </td> <td> to do </td> <td> with </td> <td align="right"> 5031 </td> </tr>
  <tr> <td> is a good </td> <td align="right"> 2671 </td> <td> is a </td> <td> good </td> <td align="right"> 4423 </td> </tr>
  <tr> <td> a series of </td> <td align="right"> 2690 </td> <td> a series </td> <td> of </td> <td align="right"> 5479 </td> </tr>
   </table>


```r
log_cond_prob <- frequency - root_freq
```

Example Results
=============================================


  
__phrase__: Theres a lady who's sure all that glitters is gold and ...   
  ...silver  __(word based prediction)__    
  ...medals  __(context based prediction)__   

Prediction relies on different stem depending on matching method




<img src="Presentation 2-figure/unnamed-chunk-8-1.png" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" style="display: block; margin: auto;" />


