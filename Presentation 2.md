Word RippeR     
========================================================
left: 60%
author: Winston A. Saunders
font-family: 'Helvetica'
date: April 19, 2015 
transition: rotate
   
  


***
![alt text](tactical.001.jpg)


Word RippeR: Use Instructions
========================================================
 
__Toolkit:__      
- Corpus-RippeR:  <small>_creates computable text samples._</small>    
- n-gram-creatoR:  <small>_builds n-gram frequency tables_</small>  
- n-gram-reduceR:   <small>_combines & reduces mulitple n-gram tables._</small>

__Web Interface:__
- Word-RippeR:  <small>[Web based interface](https://ww44ss.shinyapps.io/Coursera_Shiny_Capstone/) _providing_ __context__ _or_ __nearest word__ _based predictions._</small>    
  
<center>__Agile, Flexible, and Compact Natural Language Prediction__</center>
        
Word RippeR: Algorithm 
========================================================

The __Word-Match Algorithm__ has the following steps:  
1. Extracts the last three words from text string.  
2. Count matches to four-gram "stems".  
3. Repeat for three- and two-grams.  
4. Calculate conditional probabilities and sort results.   
5. Select highest probability of the highest order matched n-gram as best match.  

The __Context Match Algorithm__ works similarly, except stop words are removed. 

<center>__Algorithm Adapability for Different Use-Cases__</center>

Word RippeR: n-gram tables
========================================================

Computed n-gram data tables stored as integers


```r
freq <- as.integer(2000*log10(word_count))
```

giving faster look-up based probability



<!-- html table generated in R 3.1.3 by xtable 1.7-4 package -->
<!-- Mon Apr 20 14:56:30 2015 -->
<table border=1>
<tr> <th> n_gram </th> <th> frequency </th> <th> stem </th> <th> root </th> <th> root_freq </th>  </tr>
  <tr> <td> is not the </td> <td align="right"> 2622 </td> <td> is not </td> <td> the </td> <td align="right"> 5855 </td> </tr>
  <tr> <td> am going to </td> <td align="right"> 2629 </td> <td> am going </td> <td> to </td> <td align="right"> 5618 </td> </tr>
  <tr> <td> side of the </td> <td align="right"> 2851 </td> <td> side of </td> <td> the </td> <td align="right"> 5855 </td> </tr>
  <tr> <td> to find a </td> <td align="right"> 2663 </td> <td> to find </td> <td> a </td> <td align="right"> 5554 </td> </tr>
   </table>

analysis for high algorthim performance.


```r
log_cond_prob <- frequency - root_freq
```

Word RippeR: Example Results
=============================================


  
__Phrase__: There's a lady who's sure all that glitters is gold and ...   
       ...silver    __(word based prediction)__    
       ...medals    __(context based prediction)__   

results differ based on stem and prediction method. Note that a lower log value corresponds to a higher probability. 




<img src="Presentation 2-figure/unnamed-chunk-8-1.png" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" style="display: block; margin: auto;" />


