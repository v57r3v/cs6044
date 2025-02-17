java c
Homework   1 
Due   on   Friday,   January   24th
Instructions: 
• Install   pdflatex,   R,   and   RStudio on   your   computer.
•      Please    edit    the    HW1 First Last   .Rnw    ﬁle    in    Rstudio    and    compile    with    knitr    instead    of   Sweave.         Go   to   the   menu   RStudio| Preferences   .   .   .   | Sweave   choose   the   knitr   option,   i.e.,   Weave      Rnw      files      using      knitr?   You   may   have   to   install   knitr   and   other   necessary   pack-   ages.
•      Replace      ”First”      and      ”Last”      in      the      ﬁle-name      with      your      ﬁrst      and      last      names,      respectively.   Complete   your   assignment   by   modifying   and/or   adding   necessary   R-code   in   the   text   below.
•   You   should   submit   both   the data and   the   HW1 First Last.Rnw   ﬁle   in   a   zip-ﬁle   in   Canvas.   The   zip-ﬁle   should   be   named   ”HW1 First Last.zip”   and   it   should   contain   all   the   necessary   data   ﬁles,   the   HW1 First Last   .Rnw   and   HW1 First Last.pdf   ﬁle,   which   was   obtained   from   compiling   HW1 First Last   .Rnw with   knitr   and   LATEX.
NOTE: ”First”   is   your   ﬁrst   name   and   ”Last”   your   last   name.
•      The   GSI   grader   will   unzip   your   ﬁle   and   compile   it   with   Rstudio   and   knitr.   If the   ﬁle   fails   to   compile due to errors other   than   missing   packages,   there   will   be   an   automatic   10%   deduction   to   your   score.   Then,   the   GSI   will   proceed   with   grading   your   submitted   PDF.
• Data. The   zip-ﬁle   should   include   also   the   ”   .csv”   ﬁle   with   the   stock   market   data   you   down-   loaded   frin   WRDS      so   that   when   everything   is   unzipped   in   one      folder,      the      GSI   is      able   to   compile   and   reproduce   your   PDF.
Problems: 
1. (a) Read   the   tutorial   on   accessing   and   downloading   data   from   WRDS   available   on this   link. 
(b) Execute   a   query   in      Center   for   Research   in      Security   Prices,      LLC    (CRSP)   database   to   download   the   closing   daily   prices   of the   stocks   with   tickers   TSLA and   NVDA for   the   period   Jan   1,   2022   through   Dec   31,   2024. 
(c) Place the   resulting   csv ﬁle   in   a   desired   folder   in your   computer   and   modify   the   following   code      to      produce      plots      of   daily      prices,      returns,    log-returns,    and      a      scatter-plot      of   the   log-returns   of   TSLA   against   those   of   NVDA.
Identify   the   times   of splits   if   any   for   the   TSLA   and   NVDA   stock   in   this   period,   if   any.
Uncomment,   i.e.,   remove   the      ’%’,   in   the   following   lines   when   ready   to    compile.    Remove    also   \begin{verbatim}   and   \end{verbatim}   in   the    ”.Rnw”   ﬁle.
%    <>=
%      dat      =      read.csv("data_file.csv",header=TRUE)
%      #      Add    code      here      to      populate      the      necessary      variables   .   %      par(mfrow=c(2,2))
%      plot(times$AAPL,stocks$AAPL,type="l")
%      plot(times$TSLA,stocks$TSLA,col="red")
%    #      Add   more      code   .   .   .
%      @
2.      Download   the      ﬁle      ”sp500 full.csv”      available      in   the      Data   folder      of   the      Files   section      in   Canvas.    It   provides   the   data   on   daily   prices   and   returns    (among   other   things)   of   the   SP
500   index.   This   is   the   same   data   set   used   in   lectures.(a) Plot   the   time-series   of   daily   returns   and   daily   log-returns.    You   need   to   identify   which   variable gives the returns and also compute the log-returns from the   daily   closing values   of the   index.    Comment   on   the   extreme   drops   in   daily   returns/log-returns.    Can   they   be   associated   with   known   market   events?
(b) Plot   the   auto-correlation   functions   of   the      1-day      (i.e.,   daily),   5-day,      10-day   and   20-day   log-returns   and   their   squares.(c) Provide   a table   of the   basic   summary   statistics   for the   4 time   series   from   part (b).    That   is,   compute   the   minimum,   1st   quartile,   the   median,   the   3rd   quartile   and   the   maximum,   for   the   k-day   log-returns   for   k   =   1;   5; 10;   and   20.    You   can   modify   the   code   in   the   ”.Rnw”   ﬁle   that   produces:returns = list("r1"=rnorm(100),"r5"=rnorm(50), "r10" = rnorm(20), "r20"=rnorm(10))# The list is populated with random numbers, which you'd have to replace by the# corresponding returns.sum.stat = lapply(returns,summary) # What does this command do?x = matrix(0,nrow=4,ncol=6,dimnames=list(c("1-day","5-day","10-day","20-day"),names(sum.stat$r1)))x[1,]=sum.stat$r1x[2,]=sum.stat$r5x[3,]=sum.stat$r10x[4,]=sum.stat$r20kable(x)

Min. 
1st Qu. 
Median 
Mean 
3rd Qu. 
Max. 
1-day 
-3.567441 
-0.5695184 
-0.0377745 
-0.0477111 
0.7411075 
2.110397 
5-day 
-1.622665 
-0.6787439 
0.1826113 
0.0351285 
0.7654330 
2.101873 
10-day 
-1.649655 
-0.5967488 
-0.2456982 
-0.1598409 
0.3084510 
1.703530 
20-day 
-2.057332 
-1.1316308 
-0.3999786 
-0.3146389 
0.7523935 
1.237850 
3. (a) Using      the    same      data      set      as      in      the      previous      problem,    make    a    2      ×   2    array    of   normal   quantile-quantile   plots.   You   can   uncomment   and   and   modify   the   following   code
%<>=
%par(mfrow=c(2,2))         %qqnorm(returns$r1)
%qqline(returns$r1,col="red")   %qqnorm(returns$r5)
%qqline(returns$r5,col="red")
%qqnorm(returns$r10)
%qqline(returns$r10,col="red")   %qqnorm(returns$r20)
%qqline(returns$r20,col="red")   %@
(b) What   can   you   say   about   the   tails   of the   returns?
4. (a) Goto the US Treasury web-site and lookup the annual yield to maturity of   US government   issued   zero-coupon   bonds   of   maturities   3   months,   5   years   and   30   years,   respectively.    What   are   the   names   of these   3   types   of securities?(b) Suppose that a bond with maturity T = 30 years,   PAR $1000   and   annual   coupon   payments   C   is   selling   precisely   at   its   par   value.    Determine   the   value   of 代 写Homework 1R
代做程序编程语言the   coupon   payments    C.    You   can   assume   that   the   yield   to   maturity   is   the   one   you   found   in   part (a),   corresponding   to   maturity   T =   30.(c) Use   the   R-function   uniroot   to   ﬁnd   the   yield   to   maturity   of   a   30-year,   par   $1000   bond   with   annual   coupon   payments   of   $40,   which   is   selling   for   $1200   now.    Provide   the   R-code   as   well   as   the   output.uniroot(function(x)(sin(x)-0.5), interval=c(0,pi/2))$root - pi/6## [1] -1.687498e-07# Put your code above...Hint:   Write an R-function that computes the price   of a   bond   with   yield   to   maturity   r,   annual   coupon   payments   C,   par   value   PAR   and   maturity   T.      You   can   borrow   the   function   deﬁnition   from   the   lectures.    You   can   then   use   this   function   in   your   call   to   uniroot   as   I   did   in   class,   for   example.
5.    Suppose   (although this   is   dangerously   far   from   reality) that the   daily   log-returns   of the   SP
500   are   independent   and   identically   distributed   N   (μ,   σ2   ).
(a) Using   the   data   in   ﬁle   ”sp500 full.csv”,   estimate   μ   and   σ   with   the   sample   mean   and   standard   deviation.(b) Using   the   independence   and   Normality   assumptions,   compute   the   value-at-risk   at   levels   Q = 0.05   and   Q   = 0.01,   i.e.,   VaR0.05    and   VaR0.01    for   the   k-day   log-returns,   where   k   =   1,   5, 10   and   20.
Hint:   What is the distribution of   the k-day log-returns, under the assumptions in the problem.(c) Provide   a   2-row   table   of   the   proportion   of   times   the   k-day   log-returns   were   lower   than   the   -VaRQ    values   computed   in   part (b) for   Q   =   0.05   and   Q   =   0.01.    That   is,   each   entry   in   the   table   is   the   proportion   of   time   the   k-day   log-losses   were   worse   than   the   corresponding   value-at-risk.p = matrix(0,nrow=2,ncol=4)colnames(p) = c("1-day","5-day","10-day","20-day")rownames(p) = c("0.05", "0.01")# Put your code here that populates p with the desired empirical proportionskable(p)

1-day 
5-day 
10-day 
20-day 
0.05 
0 
0 
0 
0 
0.01 
0 
0 
0 
0 
Comment on the results.    What should the values of these   empirical   frequencies   be   for   models   that   agree   with   the   data?
6.      In   this   problem   we   will   ﬁrst   ﬁnd   a   slightly   more   appropriate   model   for   the   log-returns   of the   SP500 index data set.    The idea is to replace the increments   of the normal random walk   model   in   the   previous   problem   with   t-distribued   increments.    We   will   do   so   by   trial   and   error   and   eyeballing   QQ-plots.      More   sophisticated   inference   methods   will   come   shortly.(a) As   in   Problem      2      above,      load   the      SP500   data   set   from   ﬁle    sp500 full   .csv.       Select      a   consecutive      period      of      10   years.       Standardize    the      log-returns      in   this   period      and      produce      a   series   of   QQ-plots   of   the   daily   log-returns   against   simulated   samples   from   the   standardized   t-distribution   for   varying   degrees   of   freedom   v   =   2.1;   3;   4; . . ..      Pick   a   value   for   the   degrees   of   freedom   v   > 2   that   result   in   the   QQ-plot   with   the   best   ﬁt.    Produce   a   QQ-plot   with   this   “best   ﬁt”   value   as   well   as   with   two   other   values   of   v –   one   smaller   and   the   other   larger.   You   can   use   some   of the   following   code   as   a template   and   modify   it   as you   see   ﬁt. Comment on why the value of v you chose is reasonable. 
%<>=
%sp500      =      read.csv("sp500_full.csv",header=TRUE)
%t.sp      =      as.Date(x=as.character(dat$caldt),format="%Y%m%d")
%idx      =      which(t.sp>as.Date("2000-01-01")            t.sp      < as.Date("2010-01-01")) %rt = diff(log(sp500$spindx[idx]));
%mu      =   mean(rt);   %sig      =      sd(rt);
%rt_standardized      =    (rt-mu)/sig;   %
%%      The      following      function      produces      the      desired      QQ-plots   .   %
%qqplot_against_std      <- function(standardized_log_returns,nu = 2 .1){ % require(fGarch)
%      n      =      length(standardized_log_returns);
%      qqplot(standardized_log_returns,fGarch::rstd(n,nu      =      nu),   %                                  xlab="SP500    standardized    log-returns",
%                               ylab    =    "standardized    t-distribution    samples",    main=paste("QQ-plot:      nu      =    ",nu));   %abline(a=0,b=1,col="red")
%}
%         %@
(b) In the   previous   part,   we   have   obtained   using   graphical   methods   a   rough   ﬁt   of the   SP500 log-returns   via   the   follwing   model:rt   = log(St) - log(St-1   ) =   μ + σ∈t   ,                                                                                                                        (1)
where ∈t      follow   the   standardized   t-distribution   with   v   degrees   of freedom   and   St    is   the   value   of the   SP500   index   on   day   t.
Read Problem 4 on   page   13   of Ruppert      Matteson. 
Modify the code therein where the returns are   modeled   as   in   (1)   and   write   an   R-function   that takes   as   an   input the   mean   μ and the   standard   deviation   σ of the   log-returns,   the   parameter   v of the degrees of freedom for the standardized   t-distribution,   and   niter.    The output   of the   function   should   be   the   simulation-based   estimate   of the   probability   of   default   for   the   hedge   fund.Produce   a   table   or   a   graph   with   the   default   probabilities   as   a   function   of   v   >   2   and   the   volatility   σ   .      Comment   on   how   do   the   volatility   and   the   weight   of   the   tail      (represented   by   the      parameter    v)    afect      the    default      probability. Note: Initially,    use    μ    =    0.05/253    and   σ   =   0.23/√253   as   in   the   text   and   vary   v.    Then   you   can   ﬁx   a   value   of   v   and   vary   σ   .    Feel   free to   also produce   heat-map   images or   2-way tables   of the   default   probability   for   a   range   of   values   of   v   and   σ   .

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
