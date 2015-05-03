Word RippeR     
========================================================
left: 60%  
font-family: 'Helvetica'  
transition: rotate  

<br>  
Winston A. Saunders  
April 19, 2015   
<br>  
<small>R version 3.2.0 (2015-04-16)</small>  

   
  


***
<br>
<br>
![alt text](tactical.001.jpg)


Word RippeR: Use Instructions
========================================================
 
__Toolkit:__      
- Corpus-RippeR:  <small>_creates computable corpus-based text samples._</small>    
- n-gram-creatoR:  <small>_builds n-gram frequency tables_</small>  
- n-gram-reduceR:   <small>_combines & reduces mulitple n-gram tables._</small>

__Web Interface:__
- Word-RippeR:  <small>[Web based interface](https://ww44ss.shinyapps.io/Coursera_Shiny_Capstone/) _providing_ __context__ _or_ __nearest word__ _based predictions._</small>    
  
<center>__Agile, Flexible, and Compact Natural Language Prediction__</center>
        
Word RippeR: Algorithm 
========================================================

__Word-Match Algorithm__ has the following steps:  
<small>  
<br>
1. Extracts the last three words from text string.  
2. Count matches to four-gram "stems".  
3. Repeat for three- and two-grams.  
4. Calculate conditional probabilities and sort results.   
5. Select highest probability of the highest order matched n-gram as best match.  
</small>  
<br>
<br>
__Context Match Algorithm__ works similarly, except stop words are removed from n-grams. 

<center>__Algorithm Adapability for Different Use-Cases__</center>

Word RippeR: n-gram tables
========================================================

Computed n-gram data tables stored as integers


```r
freq <- as.integer(2000*log10(word_count))
```

giving faster look-up based probability analysis



<!-- html table generated in R 3.2.0 by xtable 1.7-4 package -->
<!-- Mon Apr 27 23:16:26 2015 -->
<table border=1>
<tr> <th> n_gram </th> <th> frequency </th> <th> stem </th> <th> root </th> <th> root_freq </th>  </tr>
  <tr> <td> i dont want </td> <td align="right"> 2868 </td> <td> i dont </td> <td> want </td> <td align="right"> 4201 </td> </tr>
  <tr> <td> front of the </td> <td align="right"> 2647 </td> <td> front of </td> <td> the </td> <td align="right"> 5855 </td> </tr>
  <tr> <td> but i think </td> <td align="right"> 2711 </td> <td> but i </td> <td> think </td> <td align="right"> 4273 </td> </tr>
  <tr> <td> the middle of </td> <td align="right"> 2850 </td> <td> the middle </td> <td> of </td> <td align="right"> 5479 </td> </tr>
   </table>

and higher algorthim performance.


```r
log_cond_prob <- frequency - root_freq
```

Word RippeR: Example Results
=============================================


  
__Phrase__: There's a lady who's sure all that glitters is gold and ...   
       ...silver    __(word based prediction)__    
       ...medals    __(context based prediction)__   

In the root-stem graph below, a _lower_ log value corresponds to a _higher_ probability. 




<img src="Presentation 2-figure/unnamed-chunk-8-1.png" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" style="display: block; margin: auto;" />


