## Initial Benchmarking of YUI 2 vs YUI 3 DataTables

This was a basic "brute force" testing for basic timings, using the YUI Console tool -- definitely not a comprehensive study (i.e. no profiling, etc..).

The basic test consists of creating and rendering a simple DT (no parsing, formatting, sorting, scrolling, editing, etc...) using a local Javascript Array for the data with 500 records.  *Yes, I know 500 records is quite a lot of data without using other features (pagination, scrolling), but I wanted something to allow enough time and enough page elements to make it somewhat interesting!*

CASE 1 :  The YUI 2.9 DT example [dt_290_array500.html](http://www.blunderalong.com/pub/yui3/bench_dt_jan12/dt_290_array500.html) and source at [gist 1567371](https://gist.github.com/1567371)

CASE 2 : The YUI 3.4.1 DT example [dt_341_array500.html](http://www.blunderalong.com/pub/yui3/bench_dt_jan12/dt_341_array500.html) and source at [gist 1567375](https://gist.github.com/1567375)

CASE 3 : The YUI 3.5.0PR1 DT example [dt_350pr1_array500.html](http://www.blunderalong.com/pub/yui3/bench_dt_jan12/dt_350pr1_array500.html) and source at [gist 1567382](https://gist.github.com/1567382)

(Note:  The 3.5.0PR1 wasn't accessible on the gallery when I ran this, and my github "cloning-forking" skills are lacking!.  So I ended up copying the source from lsmith's git and including it brute force.   This shouldn't effect the timings though)

For all of these cases, the data JS array (http://www.blunderalong.com/pub/yui3/bench_dt_jan12/bench_data500.js) is included separately ...

###Performance Timings

I ran these 3 test cases above on a variety of browsers (Chrome, Safari, Firefox, IE) on my MacOSX and on WinXP (virtual box) and Win7 (real thing), and for grins on Ubuntu Linux.  Since each of these browsers on each system has different tweaks to caches, virtual memory, paging, etc... a comparison between one browser to another is incorrect.  

BUT, the comparative timings on **ONE BROWSER ON ONE OS** between the 3 test cases *should be representative*.

Each test case was re-loaded several times (to optimize any internal caching) prior to collecting timings.  Then 10 subsequent reloads were done and the timings for (a) instantiating the DT and (b) rendering the DT where recorded.  This was then completed for CASE 1, 2, 3.

Below are the average results (across all the OS's) of the "Total Time" (i.e. instantiation and rendering of DT).  
Times are in msecs.

    Browser              YUI 2.9        YUI 3.4.1       YUI 3.5.0PR1
    --------           ----------       ---------       ------------
    Firefox 9.0.1         338.9           878.5             420.4
    Chrome 16.0.912       246.4           716.6             299.7
    Safari 5.1.2          159.6           624.8             278.6

and also displayed below are the execution times compared to YUI 2.9;

    Browser              YUI 2.9        YUI 3.4.1       YUI 3.5.0PR1
    --------            ---------       ---------       ------------
    Firefox 9.0.1         1.00            2.59              1.24
    Chrome 16.0.912       1.00            2.91              1.22
    Safari 5.1.2          1.00            3.91              1.75

A spreadsheet of the FULL DETAILS and raw results are at [Google Docs Spreadsheet](<https://docs.google.com/spreadsheet/ccc?key=0AlEOqgoBagH2dF9FZ2FLVjFiS2lFZThOZzRjNjJERXc).  
(It has tabs to switch between the Summary and Raw Results)

Also, I ran these test both from internally within my private network (localhost) and externally thru my public web address.  As you would expect, once things loaded ... the timings where the same internally.

##Footprint
As for the improvements of the 3.x codeline towards smaller "down-the-wire" download size, for my simple example the 3.5.0PR1 had a total size of around 213KB, where the 2.9 had around 300KB.

Your results may vary!

##Remarks

*   Clearly the "new" DataTable in 3.5+ is a vast timing improvement over the 3.4.1 offering.
*   If you look at the details, the "instantiation" time for the 3.5 DT is longer, due to ModelList and Views, etc...
*   I include 2.9.0 timings as a basis, mostly because I am MOST familiar with it.  **I Realize it is an unmaintained codeline!**

Also I realize that these timings are on an "absolute basis" ... i.e. real time, not very significant, and probably not 
noticeable by most users (except for some of the IE stuff).

I kind of feel like the timing difference from 2.9 to 3.5 (slightly longer times...) are worth it for the improved code line of YUI 3.  IMHO

NOTE: This file was originally in gist:1562898
