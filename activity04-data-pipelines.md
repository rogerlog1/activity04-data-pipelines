Activity 4
================
Logan

## Data and packages

Most of the functions that we will use this semester are from the
`{tidyverse}` (which is a package of many packages - a super package).
While we will focus on `{dplyr}`, it will be nice to be able to produce
graphical displays. Therefore, instead of loading both `{dplyr}` and
`{ggplot2}`, in the code chunk below we load all of the `{tidyverse}`.

``` r
library(tidyverse)
```

There is some other useful items to point out from this code chunk:

1.  It has been named (i.e., `load_packages`). Notice that the name
    doesn’t contain any spaces (I used `_` to separate words). If you
    put spaces in your R code chunk names, you might encounter errors
    later when you Knit your document. This is helpful because if you
    create a plot within a code chunk, the image will have that name!
    Another helpful thing by naming code chunks is that it helps with
    document navigation. In the upper right-hand corner of this `.Rmd`
    file, you can see the document outline
    <img src="README-img/document-outline-icon.png" alt="document outline" width = "20"/>
    icon. Clicking on this provides you with a table of contents type
    view. Another way to see this information by clicking on the “\#
    Data and packages” at the bottom left-hand area of this `.Rmd` pane.
2.  There is a code chunk option of `message = FALSE`…

### Messages

Knit your report with the `message = FALSE` R code chunk option and pay
attention to how this particular code chunk and output for loading the
`{tidyverse}` looks.

Now, switch this option to `message = TRUE` and knit your report again.
Discuss what is different when the `message` option is turned on
(`TRUE`) and turned off (`FALSE`) for the previous code chunk.

**Response**:When the message is changed to true, there is a bunch of
text that shows up under where we loaded up the tidyverse.

Turn the `message` option off and continue in this activity.

### Data

In this activity, we will explore data on college majors and earnings
from the data behind the FiveThirtyEight story [The Economic Guide To
Picking A College
Major](https://fivethirtyeight.com/features/the-economic-guide-to-picking-a-college-major/).
These data originally come from the American Community Survey (ACS)
2010-2012 Public Use Microdata Series. If you are curious about how the
raw data from the ACS were cleaned and prepared (not a requirement), see
the FiveThirtyEight author’s
[code](https://github.com/fivethirtyeight/data/blob/master/college-majors/college-majors-rscript.R).

As we progress through this activity, remember that there are many
considerations that go into picking a major. Earning potential and
employment prospects are two (important) of these considerations, but
they do not tell the entire story. Keep this in mind as we analyze the
data.

These data are from an external (to R) file - a comma separated values
(`.csv`) file. We will use the `readr::read_csv` function to read in
these data. When you see something in this form, I am referring to the
function as well as what package it is from (i.e., `package::function`).
We will talk more about `::` later in the course.

I try to be consistent with notation so here are some other forms that
you might see in documents:

-   “`{package_name}`”; for example, `{readr}`.
-   “`function_name` function”; for example, `read_csv` function.
-   “*hint*”; for example, *arrange* the variable.
-   “**Specific Area**”; for example, **Environment** tab.

``` r
# Note that the :: method is redundant here
# because we have already loaded the {tidyverse}
# and {readr} is included in this.
# However, I am using this method to make you
# aware of the specific package the read_csv
# function comes from.

college_recent_grads <- read.csv("data/recent-grads.csv")

college_recent_grads
```

    ##     rank major_code
    ## 1      1       2419
    ## 2      2       2416
    ## 3      3       2415
    ## 4      4       2417
    ## 5      5       2405
    ## 6      6       2418
    ## 7      7       6202
    ## 8      8       5001
    ## 9      9       2414
    ## 10    10       2408
    ## 11    11       2407
    ## 12    12       2401
    ## 13    13       2404
    ## 14    14       5008
    ## 15    15       2409
    ## 16    16       2402
    ## 17    17       2412
    ## 18    18       2400
    ## 19    19       2403
    ## 20    20       3201
    ## 21    21       2102
    ## 22    22       1104
    ## 23    23       2502
    ## 24    24       2413
    ## 25    25       6212
    ## 26    26       2406
    ## 27    27       5601
    ## 28    28       6204
    ## 29    29       2499
    ## 30    30       5402
    ## 31    31       2410
    ## 32    32       2500
    ## 33    33       6099
    ## 34    34       2411
    ## 35    35       6107
    ## 36    36       6207
    ## 37    37       5501
    ## 38    38       6205
    ## 39    39       2503
    ## 40    40       5102
    ## 41    41       6201
    ## 42    42       3700
    ## 43    43       2100
    ## 44    44       5007
    ## 45    45       6105
    ## 46    46       2105
    ## 47    47       3702
    ## 48    48       3701
    ## 49    49       3607
    ## 50    50       5006
    ## 51    51       2501
    ## 52    52       6104
    ## 53    53       4005
    ## 54    54       2101
    ## 55    55       4006
    ## 56    56       2303
    ## 57    57       5505
    ## 58    58       6200
    ## 59    59       1401
    ## 60    60       6210
    ## 61    61       6108
    ## 62    62       3603
    ## 63    63       6299
    ## 64    64       1101
    ## 65    65       1100
    ## 66    66       2599
    ## 67    67       2504
    ## 68    68       3605
    ## 69    69       5599
    ## 70    70       6403
    ## 71    71       5205
    ## 72    72       1102
    ## 73    73       5000
    ## 74    74       3801
    ## 75    75       5003
    ## 76    76       5701
    ## 77    77       6203
    ## 78    78       6206
    ## 79    79       5506
    ## 80    80       5504
    ## 81    81       3606
    ## 82    82       2106
    ## 83    83       3601
    ## 84    84       3602
    ## 85    85       2107
    ## 86    86       5004
    ## 87    87       6209
    ## 88    88       3202
    ## 89    89       6199
    ## 90    90       5401
    ## 91    91       5005
    ## 92    92       5206
    ## 93    93       1301
    ## 94    94       1901
    ## 95    95       5301
    ## 96    96       6004
    ## 97    97       1902
    ## 98    98       5098
    ## 99    99       1904
    ## 100  100       1501
    ## 101  101       2310
    ## 102  102       3608
    ## 103  103       5503
    ## 104  104       4002
    ## 105  105       6103
    ## 106  106       2001
    ## 107  107       5901
    ## 108  108       1303
    ## 109  109       3611
    ## 110  110       4000
    ## 111  111       5002
    ## 112  112       1302
    ## 113  113       1106
    ## 114  114       2300
    ## 115  115       6402
    ## 116  116       2602
    ## 117  117       4001
    ## 118  118       2311
    ## 119  119       6110
    ## 120  120       2305
    ## 121  121       2301
    ## 122  122       6106
    ## 123  123       3699
    ## 124  124       3600
    ## 125  125       5507
    ## 126  126       1903
    ## 127  127       6109
    ## 128  128       6211
    ## 129  129       2313
    ## 130  130       2601
    ## 131  131       2399
    ## 132  132       4007
    ## 133  133       3604
    ## 134  134       2309
    ## 135  135       6100
    ## 136  136       4801
    ## 137  137       2314
    ## 138  138       3301
    ## 139  139       2304
    ## 140  140       4101
    ## 141  141       3401
    ## 142  142       6005
    ## 143  143       5500
    ## 144  144       1105
    ## 145  145       2308
    ## 146  146       5200
    ## 147  147       6002
    ## 148  148       2306
    ## 149  149       6006
    ## 150  150       6000
    ## 151  151       2901
    ## 152  152       5404
    ## 153  153       1103
    ## 154  154       6003
    ## 155  155       2312
    ## 156  156       5299
    ## 157  157       5403
    ## 158  158       3402
    ## 159  159       4901
    ## 160  160       6007
    ## 161  161       2201
    ## 162  162       1199
    ## 163  163       5502
    ## 164  164       6102
    ## 165  165       2307
    ## 166  166       2603
    ## 167  167       6001
    ## 168  168       3302
    ## 169  169       3609
    ## 170  170       5201
    ## 171  171       5202
    ## 172  172       5203
    ## 173  173       3501
    ##                                                                 major
    ## 1                                               Petroleum Engineering
    ## 2                                      Mining And Mineral Engineering
    ## 3                                           Metallurgical Engineering
    ## 4                           Naval Architecture And Marine Engineering
    ## 5                                                Chemical Engineering
    ## 6                                                 Nuclear Engineering
    ## 7                                                   Actuarial Science
    ## 8                                          Astronomy And Astrophysics
    ## 9                                              Mechanical Engineering
    ## 10                                             Electrical Engineering
    ## 11                                               Computer Engineering
    ## 12                                              Aerospace Engineering
    ## 13                                             Biomedical Engineering
    ## 14                                                  Materials Science
    ## 15                          Engineering Mechanics Physics And Science
    ## 16                                             Biological Engineering
    ## 17                           Industrial And Manufacturing Engineering
    ## 18                                                General Engineering
    ## 19                                          Architectural Engineering
    ## 20                                                    Court Reporting
    ## 21                                                   Computer Science
    ## 22                                                       Food Science
    ## 23                                  Electrical Engineering Technology
    ## 24                        Materials Engineering And Materials Science
    ## 25                      Management Information Systems And Statistics
    ## 26                                                  Civil Engineering
    ## 27                                              Construction Services
    ## 28                                Operations Logistics And e-Commerce
    ## 29                                          Miscellaneous Engineering
    ## 30                                                      Public Policy
    ## 31                                          Environmental Engineering
    ## 32                                           Engineering Technologies
    ## 33                                            Miscellaneous Fine Arts
    ## 34                             Geological And Geophysical Engineering
    ## 35                                                            Nursing
    ## 36                                                            Finance
    ## 37                                                          Economics
    ## 38                                                 Business Economics
    ## 39                                 Industrial Production Technologies
    ## 40         Nuclear, Industrial Radiology, And Biological Technologies
    ## 41                                                         Accounting
    ## 42                                                        Mathematics
    ## 43                                   Computer And Information Systems
    ## 44                                                            Physics
    ## 45                                   Medical Technologies Technicians
    ## 46                                               Information Sciences
    ## 47                                    Statistics And Decision Science
    ## 48                                                Applied Mathematics
    ## 49                                                       Pharmacology
    ## 50                                                       Oceanography
    ## 51                              Engineering And Industrial Management
    ## 52                                         Medical Assisting Services
    ## 53                                   Mathematics And Computer Science
    ## 54                           Computer Programming And Data Processing
    ## 55                                Cognitive Science And Biopsychology
    ## 56                                          School Student Counseling
    ## 57                                            International Relations
    ## 58                                                   General Business
    ## 59                                                       Architecture
    ## 60                                             International Business
    ## 61                Pharmacy Pharmaceutical Sciences And Administration
    ## 62                                                  Molecular Biology
    ## 63                    Miscellaneous Business & Medical Administration
    ## 64                              Agriculture Production And Management
    ## 65                                                General Agriculture
    ## 66                             Miscellaneous Engineering Technologies
    ## 67                        Mechanical Engineering Related Technologies
    ## 68                                                           Genetics
    ## 69                                      Miscellaneous Social Sciences
    ## 70                                              United States History
    ## 71                           Industrial And Organizational Psychology
    ## 72                                             Agricultural Economics
    ## 73                                                  Physical Sciences
    ## 74                                              Military Technologies
    ## 75                                                          Chemistry
    ## 76  Electrical, Mechanical, And Precision Technologies And Production
    ## 77                             Business Management And Administration
    ## 78                                   Marketing And Marketing Research
    ## 79                                   Political Science And Government
    ## 80                                                          Geography
    ## 81                                                       Microbiology
    ## 82                    Computer Administration Management And Security
    ## 83                                               Biochemical Sciences
    ## 84                                                             Botany
    ## 85                         Computer Networking And Telecommunications
    ## 86                                          Geology And Earth Science
    ## 87                           Human Resources And Personnel Management
    ## 88                                          Pre-Law And Legal Studies
    ## 89                           Miscellaneous Health Medical Professions
    ## 90                                              Public Administration
    ## 91                                                        Geosciences
    ## 92                                                  Social Psychology
    ## 93                                              Environmental Science
    ## 94                                                     Communications
    ## 95                               Criminal Justice And Fire Protection
    ## 96                                  Commercial Art And Graphic Design
    ## 97                                                         Journalism
    ## 98                              Multi-Disciplinary Or General Science
    ## 99                                   Advertising And Public Relations
    ## 100                              Area Ethnic And Civilization Studies
    ## 101                                           Special Needs Education
    ## 102                                                        Physiology
    ## 103                                                       Criminology
    ## 104                                                Nutrition Sciences
    ## 105                        Health And Medical Administrative Services
    ## 106                                        Communication Technologies
    ## 107                          Transportation Sciences And Technologies
    ## 108                                      Natural Resources Management
    ## 109                                                      Neuroscience
    ## 110                                   Multi/Interdisciplinary Studies
    ## 111                              Atmospheric Sciences And Meteorology
    ## 112                                                          Forestry
    ## 113                                                      Soil Science
    ## 114                                                 General Education
    ## 115                                                           History
    ## 116     French German Latin And Other Common Foreign Language Studies
    ## 117                           Intercultural And International Studies
    ## 118                       Social Science Or History Teacher Education
    ## 119                                       Community And Public Health
    ## 120                                     Mathematics Teacher Education
    ## 121                        Educational Administration And Supervision
    ## 122                           Health And Medical Preparatory Programs
    ## 123                                             Miscellaneous Biology
    ## 124                                                           Biology
    ## 125                                                         Sociology
    ## 126                                                        Mass Media
    ## 127                                     Treatment Therapy Professions
    ## 128                                            Hospitality Management
    ## 129                                      Language And Drama Education
    ## 130               Linguistics And Comparative Language And Literature
    ## 131                                           Miscellaneous Education
    ## 132                                 Interdisciplinary Social Sciences
    ## 133                                                           Ecology
    ## 134                                       Secondary Teacher Education
    ## 135                               General Medical And Health Services
    ## 136                                  Philosophy And Religious Studies
    ## 137                                           Art And Music Education
    ## 138                                   English Language And Literature
    ## 139                                              Elementary Education
    ## 140                     Physical Fitness Parks Recreation And Leisure
    ## 141                                                      Liberal Arts
    ## 142                                  Film Video And Photographic Arts
    ## 143                                           General Social Sciences
    ## 144                                        Plant Science And Agronomy
    ## 145                            Science And Computer Teacher Education
    ## 146                                                        Psychology
    ## 147                                                             Music
    ## 148                            Physical And Health Education Teaching
    ## 149                                         Art History And Criticism
    ## 150                                                         Fine Arts
    ## 151                                      Family And Consumer Sciences
    ## 152                                                       Social Work
    ## 153                                                   Animal Sciences
    ## 154                                        Visual And Performing Arts
    ## 155                                Teacher Education: Multiple Levels
    ## 156                                          Miscellaneous Psychology
    ## 157                         Human Services And Community Organization
    ## 158                                                        Humanities
    ## 159                                  Theology And Religious Vocations
    ## 160                                                       Studio Arts
    ## 161                            Cosmetology Services And Culinary Arts
    ## 162                                         Miscellaneous Agriculture
    ## 163                                       Anthropology And Archeology
    ## 164                     Communication Disorders Sciences And Services
    ## 165                                         Early Childhood Education
    ## 166                                           Other Foreign Languages
    ## 167                                            Drama And Theater Arts
    ## 168                                          Composition And Rhetoric
    ## 169                                                           Zoology
    ## 170                                            Educational Psychology
    ## 171                                               Clinical Psychology
    ## 172                                             Counseling Psychology
    ## 173                                                   Library Science
    ##                          major_category  total sample_size    men  women
    ## 1                           Engineering   2339          36   2057    282
    ## 2                           Engineering    756           7    679     77
    ## 3                           Engineering    856           3    725    131
    ## 4                           Engineering   1258          16   1123    135
    ## 5                           Engineering  32260         289  21239  11021
    ## 6                           Engineering   2573          17   2200    373
    ## 7                              Business   3777          51   2110   1667
    ## 8                     Physical Sciences   1792          10    832    960
    ## 9                           Engineering  91227        1029  80320  10907
    ## 10                          Engineering  81527         631  65511  16016
    ## 11                          Engineering  41542         399  33258   8284
    ## 12                          Engineering  15058         147  12953   2105
    ## 13                          Engineering  14955          79   8407   6548
    ## 14                          Engineering   4279          22   2949   1330
    ## 15                          Engineering   4321          30   3526    795
    ## 16                          Engineering   8925          55   6062   2863
    ## 17                          Engineering  18968         183  12453   6515
    ## 18                          Engineering  61152         425  45683  15469
    ## 19                          Engineering   2825          26   1835    990
    ## 20                  Law & Public Policy   1148          14    877    271
    ## 21              Computers & Mathematics 128319        1196  99743  28576
    ## 22      Agriculture & Natural Resources     NA          36     NA     NA
    ## 23                          Engineering  11565          97   8181   3384
    ## 24                          Engineering   2993          22   2020    973
    ## 25                             Business  18713         278  13496   5217
    ## 26                          Engineering  53153         565  41081  12072
    ## 27  Industrial Arts & Consumer Services  18498         295  16820   1678
    ## 28                             Business  11732         156   7921   3811
    ## 29                          Engineering   9133         118   7398   1735
    ## 30                  Law & Public Policy   5978          55   2639   3339
    ## 31                          Engineering   4047          26   2662   1385
    ## 32                          Engineering   3600          39   2695    905
    ## 33                                 Arts   3340          30   1970   1370
    ## 34                          Engineering    720           5    488    232
    ## 35                               Health 209394        2554  21773 187621
    ## 36                             Business 174506        2189 115030  59476
    ## 37                       Social Science 139247        1322  89749  49498
    ## 38                             Business  13302         199   7575   5727
    ## 39                          Engineering   4631          73   3477   1154
    ## 40                    Physical Sciences   2116          31    528   1588
    ## 41                             Business 198633        2042  94519 104114
    ## 42              Computers & Mathematics  72397         541  39956  32441
    ## 43              Computers & Mathematics  36698         425  27392   9306
    ## 44                    Physical Sciences  32142         142  23080   9062
    ## 45                               Health  15914         190   3916  11998
    ## 46              Computers & Mathematics  11913         158   9005   2908
    ## 47              Computers & Mathematics   6251          37   2960   3291
    ## 48              Computers & Mathematics   4939          45   2794   2145
    ## 49               Biology & Life Science   1762           3    515   1247
    ## 50                    Physical Sciences   2418          36    752   1666
    ## 51                          Engineering   2906          29   2400    506
    ## 52                               Health  11123          67    803  10320
    ## 53              Computers & Mathematics    609           7    500    109
    ## 54              Computers & Mathematics   4168          43   3046   1122
    ## 55               Biology & Life Science   3831          25   1667   2164
    ## 56                            Education    818           4    119    699
    ## 57                       Social Science  28187         219  10345  17842
    ## 58                             Business 234590        2380 132238 102352
    ## 59                          Engineering  46420         362  25463  20957
    ## 60                             Business  25894         260  10624  15270
    ## 61                               Health  23551          38   8697  14854
    ## 62               Biology & Life Science  18300          90   7426  10874
    ## 63                             Business  17947         244  10285   7662
    ## 64      Agriculture & Natural Resources  14240         273   9658   4582
    ## 65      Agriculture & Natural Resources  10399         158   6053   4346
    ## 66                          Engineering   8804         125   7043   1761
    ## 67                          Engineering   4790          71   4419    371
    ## 68               Biology & Life Science   3635          11   1761   1874
    ## 69                       Social Science   3283          28   1499   1784
    ## 70            Humanities & Liberal Arts   3079          22   1756   1323
    ## 71             Psychology & Social Work   3014          24   1075   1939
    ## 72      Agriculture & Natural Resources   2439          44   1749    690
    ## 73                    Physical Sciences   1436          10    894    542
    ## 74  Industrial Arts & Consumer Services    124           4    124      0
    ## 75                    Physical Sciences  66530         353  32923  33607
    ## 76  Industrial Arts & Consumer Services   2435          37   1869    566
    ## 77                             Business 329927        4212 173809 156118
    ## 78                             Business 205211        2684  78857 126354
    ## 79                       Social Science 182621        1387  93880  88741
    ## 80                       Social Science  18480         179  11404   7076
    ## 81               Biology & Life Science  15232          62   6383   8849
    ## 82              Computers & Mathematics   8066         103   6607   1459
    ## 83               Biology & Life Science  39107         174  18951  20156
    ## 84               Biology & Life Science   1329           9    626    703
    ## 85              Computers & Mathematics   7613          97   5291   2322
    ## 86                    Physical Sciences  10972          78   5813   5159
    ## 87                             Business  24497         264   6184  18313
    ## 88                  Law & Public Policy  13528          92   4435   9093
    ## 89                               Health  13386          81   1589  11797
    ## 90                  Law & Public Policy   5629          46   2947   2682
    ## 91                    Physical Sciences   1978          18    809   1169
    ## 92             Psychology & Social Work   1386           8    413    973
    ## 93               Biology & Life Science  25965         225  10787  15178
    ## 94          Communications & Journalism 213996        2394  70619 143377
    ## 95                  Law & Public Policy 152824        1728  80231  72593
    ## 96                                 Arts 103480        1186  32041  71439
    ## 97          Communications & Journalism  72619         843  23736  48883
    ## 98                    Physical Sciences  62052         427  27015  35037
    ## 99          Communications & Journalism  53162         681  12862  40300
    ## 100           Humanities & Liberal Arts  31195         249   8739  22456
    ## 101                           Education  28739         246   2682  26057
    ## 102              Biology & Life Science  22060          99   8422  13638
    ## 103                      Social Science  19879         214  10031   9848
    ## 104                              Health  18909         118   2563  16346
    ## 105                              Health  18109         184   4266  13843
    ## 106             Computers & Mathematics  18035         208  11431   6604
    ## 107 Industrial Arts & Consumer Services  15150         180  13257   1893
    ## 108     Agriculture & Natural Resources  13773         152   8617   5156
    ## 109              Biology & Life Science  13663          53   4944   8719
    ## 110                   Interdisciplinary  12296         128   2817   9479
    ## 111                   Physical Sciences   4043          32   2744   1299
    ## 112     Agriculture & Natural Resources   3607          48   3156    451
    ## 113     Agriculture & Natural Resources    685           4    476    209
    ## 114                           Education 143718         919  26893 116825
    ## 115           Humanities & Liberal Arts 141951        1058  78253  63698
    ## 116           Humanities & Liberal Arts  48246         342  12835  35411
    ## 117           Humanities & Liberal Arts  24650         184   8575  16075
    ## 118                           Education  20198         157   9950  10248
    ## 119                              Health  19735         130   4103  15632
    ## 120                           Education  14237         123   3872  10365
    ## 121                           Education    804           5    280    524
    ## 122                              Health  12740          31   5521   7219
    ## 123              Biology & Life Science  10706          63   4747   5959
    ## 124              Biology & Life Science 280709        1370 111762 168947
    ## 125                      Social Science 115433        1024  32510  82923
    ## 126         Communications & Journalism  52824         590  24704  28120
    ## 127                              Health  48491         224  13487  35004
    ## 128                            Business  43647         546  15204  28443
    ## 129                           Education  30471         235   3741  26730
    ## 130           Humanities & Liberal Arts  16601          88   4416  12185
    ## 131                           Education  10150         126   3654   6496
    ## 132                      Social Science   9916          95   2337   7579
    ## 133              Biology & Life Science   9154          86   3878   5276
    ## 134                           Education  17125         156   6820  10305
    ## 135                              Health  33599         202   7574  26025
    ## 136           Humanities & Liberal Arts  54814         375  31967  22847
    ## 137                           Education  34181         338  10732  23449
    ## 138           Humanities & Liberal Arts 194673        1436  58227 136446
    ## 139                           Education 170862        1629  13029 157833
    ## 140 Industrial Arts & Consumer Services 125074        1014  62181  62893
    ## 141           Humanities & Liberal Arts  71369         569  22339  49030
    ## 142                                Arts  38761         331  22357  16404
    ## 143                      Social Science  12920         113   5079   7841
    ## 144     Agriculture & Natural Resources   7416         110   4897   2519
    ## 145                           Education   6483          59   2049   4434
    ## 146            Psychology & Social Work 393735        2584  86648 307087
    ## 147                                Arts  60633         419  29909  30724
    ## 148                           Education  28213         259  15670  12543
    ## 149           Humanities & Liberal Arts  21030         204   3240  17790
    ## 150                                Arts  74440         623  24786  49654
    ## 151 Industrial Arts & Consumer Services  58001         518   5166  52835
    ## 152            Psychology & Social Work  53552         374   5137  48415
    ## 153     Agriculture & Natural Resources  21573         255   5347  16226
    ## 154                                Arts  16250         132   4133  12117
    ## 155                           Education  14443         142   2734  11709
    ## 156            Psychology & Social Work   9628          60   1936   7692
    ## 157            Psychology & Social Work   9374          89    885   8489
    ## 158           Humanities & Liberal Arts   6652          49   2013   4639
    ## 159           Humanities & Liberal Arts  30207         310  18616  11591
    ## 160                                Arts  16977         182   4754  12223
    ## 161 Industrial Arts & Consumer Services  10510         117   4364   6146
    ## 162     Agriculture & Natural Resources   1488          24    404   1084
    ## 163           Humanities & Liberal Arts  38844         247  11376  27468
    ## 164                              Health  38279          95   1225  37054
    ## 165                           Education  37589         342   1167  36422
    ## 166           Humanities & Liberal Arts  11204          56   3472   7732
    ## 167                                Arts  43249         357  14440  28809
    ## 168           Humanities & Liberal Arts  18953         151   7022  11931
    ## 169              Biology & Life Science   8409          47   3050   5359
    ## 170            Psychology & Social Work   2854           7    522   2332
    ## 171            Psychology & Social Work   2838          13    568   2270
    ## 172            Psychology & Social Work   4626          21    931   3695
    ## 173                           Education   1098           2    134    964
    ##     sharewomen employed employed_fulltime employed_parttime
    ## 1   0.12056434     1976              1849               270
    ## 2   0.10185185      640               556               170
    ## 3   0.15303738      648               558               133
    ## 4   0.10731320      758              1069               150
    ## 5   0.34163050    25694             23170              5180
    ## 6   0.14496697     1857              2038               264
    ## 7   0.44135557     2912              2924               296
    ## 8   0.53571429     1526              1085               553
    ## 9   0.11955890    76442             71298             13101
    ## 10  0.19645026    61928             55450             12695
    ## 11  0.19941264    32506             30315              5146
    ## 12  0.13979280    11391             11106              2724
    ## 13  0.43784687    10047              9017              2694
    ## 14  0.31082028     3307              2751               878
    ## 15  0.18398519     3608              2999               811
    ## 16  0.32078431     6170              5455              1983
    ## 17  0.34347322    15604             14879              2243
    ## 18  0.25295984    44931             41235              7199
    ## 19  0.35044248     2575              2277               343
    ## 20  0.23606272      930               808               223
    ## 21  0.22269500   102087             91485             18726
    ## 22          NA     3149              2558              1121
    ## 23  0.29260700     8587              7530              1873
    ## 24  0.32509188     2449              1658              1040
    ## 25  0.27879015    16413             15141              2420
    ## 26  0.22711794    43041             38302             10080
    ## 27  0.09071251    16318             15690              1751
    ## 28  0.32483805    10027              9639              1183
    ## 29  0.18997044     7428              6811              1662
    ## 30  0.55854801     4547              4163              1306
    ## 31  0.34222881     2983              2384               930
    ## 32  0.25138889     2799              2257               689
    ## 33  0.41017964     2914              2049              1067
    ## 34  0.32222222      604               524               126
    ## 35  0.89601899   180903            151191             40818
    ## 36  0.34082496   145696            137921             21463
    ## 37  0.35546906   104117             96567             25325
    ## 38  0.43053676    10914             10048              1937
    ## 39  0.24919024     4428              3988               597
    ## 40  0.75047259     1778              1392               579
    ## 41  0.52415258   165527            151967             27693
    ## 42  0.44809868    58118             46399             18079
    ## 43  0.25358330    28459             26348              4332
    ## 44  0.28193641    25302             19428              8721
    ## 45  0.75392736    13150             11510              2665
    ## 46  0.24410308     9881              9105              1468
    ## 47  0.52647576     4247              3190              1840
    ## 48  0.43429844     3854              3465              1176
    ## 49  0.70771850     1144               657               532
    ## 50  0.68899917     1638              1931               379
    ## 51  0.17412251     2125              1992               462
    ## 52  0.92780725     9168              5643              4107
    ## 53  0.17898194      559               584                 0
    ## 54  0.26919386     3257              3204               482
    ## 55  0.56486557     2741              2470               711
    ## 56  0.85452323      730               595               135
    ## 57  0.63298684    21190             18681              5563
    ## 58  0.43630163   190183            171385             36241
    ## 59  0.45146489    34158             29223             10206
    ## 60  0.58971190    19660             17563              4890
    ## 61  0.63071632    16620             12537              5346
    ## 62  0.59420765    11581              9441              4590
    ## 63  0.42692372    14826             13364              3366
    ## 64  0.32176966    12323             11119              2196
    ## 65  0.41792480     8884              7589              2031
    ## 66  0.20002272     7502              7001              1240
    ## 67  0.07745303     4186              4175               247
    ## 68  0.51554333     2463              1787               847
    ## 69  0.54340542     2727              2183               907
    ## 70  0.42968496     2787              2103               839
    ## 71  0.64333112     2343              1644              1095
    ## 72  0.28290283     2174              1819               620
    ## 73  0.37743733     1146               768               437
    ## 74  0.00000000        0               111                 0
    ## 75  0.50514054    48535             39509             15066
    ## 76  0.23244353     2107              2057               287
    ## 77  0.47318952   276234            251540             50357
    ## 78  0.61572723   178862            156668             35829
    ## 79  0.48592988   133454            117709             43711
    ## 80  0.38290043    14057             11367              5651
    ## 81  0.58094800     9685              7453              3379
    ## 82  0.18088272     6509              6289              1030
    ## 83  0.51540645    25678             20643              9948
    ## 84  0.52896915     1010               946               169
    ## 85  0.30500460     6144              5495              1447
    ## 86  0.47019687     8296              6966              2913
    ## 87  0.74756093    20760             18550              3767
    ## 88  0.67216144     9762              7851              3595
    ## 89  0.88129389    10076              7514              4145
    ## 90  0.47646118     4158              4148               847
    ## 91  0.59100101     1441              1264               354
    ## 92  0.70202020     1080               828               433
    ## 93  0.58455613    20859             16987              7071
    ## 94  0.66999851   179633            147335             49889
    ## 95  0.47501047   125393            109970             32242
    ## 96  0.69036529    83483             67448             24387
    ## 97  0.67314339    61022             51411             15902
    ## 98  0.56463933    46138             37850             13133
    ## 99  0.75806027    45326             38815             10948
    ## 100 0.71985895    24629             18755              9541
    ## 101 0.90667734    24639             21584              5153
    ## 102 0.61822303    14643             10732              6541
    ## 103 0.49539715    16181             13616              4543
    ## 104 0.86445608    13217              9601              6648
    ## 105 0.76442653    15419             13534              3299
    ## 106 0.36617688    14779             11981              4690
    ## 107 0.12495049    12266             11688              2633
    ## 108 0.37435562    11797             10722              2613
    ## 109 0.63814682     9087              8027              3078
    ## 110 0.77090111     9821              8032              3173
    ## 111 0.32129607     3431              2659              1309
    ## 112 0.12503465     3007              2473               891
    ## 113 0.30510949      613               488               185
    ## 114 0.81287661   118241             98408             29558
    ## 115 0.44873231   105646             84681             40657
    ## 116 0.73396758    38315             29340             14569
    ## 117 0.65212982    18824             14354              7978
    ## 118 0.50737697    17700             14002              5168
    ## 119 0.79209526    14512             10099              6377
    ## 120 0.72803259    13115             11259              2273
    ## 121 0.65174129      703               733                 0
    ## 122 0.56664050     7052              5029              3891
    ## 123 0.55660377     7767              6076              2568
    ## 124 0.60185815   182295            144512             72371
    ## 125 0.71836477    92721             73475             29639
    ## 126 0.53233379    44679             35769             13078
    ## 127 0.72186591    37861             30020             12346
    ## 128 0.65165991    36728             32160              7494
    ## 129 0.87722753    26033             21419              7239
    ## 130 0.73399193    11165              8462              4831
    ## 131 0.64000000     8691              7264              2202
    ## 132 0.76432029     7444              5843              2834
    ## 133 0.57636006     7585              5603              2741
    ## 134 0.60175183    15116             12520              3782
    ## 135 0.77457662    24406             18166             11088
    ## 136 0.41680957    40157             31086             16659
    ## 137 0.68602440    30007             23018              9209
    ## 138 0.70089843   149180            114386             57825
    ## 139 0.92374548   149339            123177             37965
    ## 140 0.50284631   103078             77428             38515
    ## 141 0.68699295    54844             43401             19187
    ## 142 0.42320890    31433             22457             12818
    ## 143 0.60688855     9602              7700              3396
    ## 144 0.33967098     6594              5798              1246
    ## 145 0.68394262     5362              4764              1227
    ## 146 0.77993320   307933            233205            115172
    ## 147 0.50672076    47662             29010             24943
    ## 148 0.44458229    23794             19420              7230
    ## 149 0.84593438    17579             13262              6140
    ## 150 0.66703385    59679             42764             23656
    ## 151 0.91093257    46624             36747             15872
    ## 152 0.90407454    45038             34941             13481
    ## 153 0.75214388    17112             14479              5353
    ## 154 0.74566154    12870              8447              6253
    ## 155 0.81070415    13076             11734              2214
    ## 156 0.79891982     7653              5201              3221
    ## 157 0.90558993     8294              6455              2405
    ## 158 0.69738424     5052              3565              2225
    ## 159 0.38371901    24202             18079              8767
    ## 160 0.71997408    13908             10451              5673
    ## 161 0.58477640     8650              7662              2064
    ## 162 0.72849462     1290              1098               335
    ## 163 0.70713624    29633             20147             14515
    ## 164 0.96799812    29763             19975             13862
    ## 165 0.96895368    32551             27569              7001
    ## 166 0.69011068     7052              5197              3685
    ## 167 0.66611945    36165             25147             15994
    ## 168 0.62950456    15053             10121              6612
    ## 169 0.63729338     6259              5043              2190
    ## 170 0.81709881     2125              1848               572
    ## 171 0.79985906     2101              1724               648
    ## 172 0.79874622     3777              3154               965
    ## 173 0.87795993      742               593               237
    ##     employed_fulltime_yearround unemployed unemployment_rate p25th median
    ## 1                          1207         37       0.018380527 95000 110000
    ## 2                           388         85       0.117241379 55000  75000
    ## 3                           340         16       0.024096386 50000  73000
    ## 4                           692         40       0.050125313 43000  70000
    ## 5                         16697       1672       0.061097712 50000  65000
    ## 6                          1449        400       0.177226407 50000  65000
    ## 7                          2482        308       0.095652174 53000  62000
    ## 8                           827         33       0.021167415 31500  62000
    ## 9                         54639       4650       0.057342278 48000  60000
    ## 10                        41413       3895       0.059173845 45000  60000
    ## 11                        23621       2275       0.065409275 45000  60000
    ## 12                         8790        794       0.065162085 42000  60000
    ## 13                         5986       1019       0.092083860 36000  60000
    ## 14                         1967         78       0.023042836 39000  60000
    ## 15                         2004         23       0.006334343 25000  58000
    ## 16                         3413        589       0.087143069 40000  57100
    ## 17                        11326        699       0.042875544 37900  57000
    ## 18                        33540       2859       0.059824231 36000  56000
    ## 19                         1848        170       0.061930783 38000  54000
    ## 20                          808         11       0.011689692 50000  54000
    ## 21                        70932       6884       0.063172771 39000  53000
    ## 22                         1735        338       0.096931460 32000  53000
    ## 23                         5681        824       0.087557114 35000  52000
    ## 24                         1151         70       0.027788805 35000  52000
    ## 25                        13017       1015       0.058239614 38000  51000
    ## 26                        29196       3270       0.070609574 40000  50000
    ## 27                        12313       1042       0.060023041 36000  50000
    ## 28                         7724        504       0.047858703 40000  50000
    ## 29                         5476        597       0.074392523 39000  50000
    ## 30                         2776        670       0.128426299 35000  50000
    ## 31                         1951        308       0.093588575 42000  50000
    ## 32                         1723        163       0.055030385 43000  50000
    ## 33                         1200        286       0.089375000 25000  50000
    ## 34                          396         49       0.075038285 42800  50000
    ## 35                       122817       8497       0.044862724 39000  48000
    ## 36                       108595       9413       0.060686356 35000  47000
    ## 37                        70740      11452       0.099092317 35000  47000
    ## 38                         8000       1165       0.096448381 33000  46000
    ## 39                         3242        129       0.028308097 35000  46000
    ## 40                         1115        137       0.071540470 38000  46000
    ## 41                       123169      12411       0.069749014 34000  45000
    ## 42                        33738       2884       0.047277138 33000  45000
    ## 43                        21130       2934       0.093460326 30000  45000
    ## 44                        14389       1282       0.048224496 30000  45000
    ## 45                         9005        505       0.036982790 36000  45000
    ## 46                         7378        639       0.060741445 32500  45000
    ## 47                         2151        401       0.086273666 26700  45000
    ## 48                         2593        385       0.090823307 34000  45000
    ## 49                          565        107       0.085531575 40000  45000
    ## 50                         1595         99       0.056994819 23000  44700
    ## 51                         1358         74       0.033651660 30000  44000
    ## 52                         4290        407       0.042506527 30000  42000
    ## 53                          391          0       0.000000000 30000  42000
    ## 54                         2453        419       0.113982590 20000  41300
    ## 55                         1584        223       0.075236167 20000  41000
    ## 56                          545         88       0.107579462 41000  41000
    ## 57                        13583       2271       0.096798943 31200  40100
    ## 58                       138299      14946       0.072861468 30000  40000
    ## 59                        20026       4366       0.113331949 31000  40000
    ## 60                        12823       2092       0.096175064 30000  40000
    ## 61                         9131        977       0.055520827 20000  40000
    ## 62                         6183       1067       0.084361164 29000  40000
    ## 63                        10637       1150       0.071982974 30000  40000
    ## 64                         9093        649       0.050030836 25000  40000
    ## 65                         5888        178       0.019642463 30000  40000
    ## 66                         5825        416       0.052538520 30400  40000
    ## 67                         3607        250       0.056357078 27000  40000
    ## 68                         1487         87       0.034117647 34000  40000
    ## 69                         1530        215       0.073079538 30000  40000
    ## 70                         1274        138       0.047179487 30000  40000
    ## 71                         1409        286       0.108786611 32000  40000
    ## 72                         1528        182       0.077249576 27000  40000
    ## 73                          653         42       0.035353535 30000  40000
    ## 74                          111          0       0.000000000 40000  40000
    ## 75                        29910       2769       0.053972400 30000  39000
    ## 76                         1752         64       0.029479503 22500  38400
    ## 77                       199897      21502       0.072218341 29000  38000
    ## 78                       127230      11663       0.061215064 30000  38000
    ## 79                        83236      15022       0.101174601 28000  38000
    ## 80                         8628       1799       0.113458628 30000  38000
    ## 81                         5080        693       0.066775872 29600  38000
    ## 82                         4936        721       0.099723375 25000  37500
    ## 83                        13785       2249       0.080531385 29000  37400
    ## 84                          740          0       0.000000000 26000  37000
    ## 85                         4369       1100       0.151849807 27000  36400
    ## 86                         5008        677       0.075448568 28000  36200
    ## 87                        15446       1315       0.059569649 28000  36000
    ## 88                         5370        757       0.071965016 29200  36000
    ## 89                         5868        893       0.081411250 23000  36000
    ## 90                         2952        789       0.159490600 23000  36000
    ## 91                         1011         36       0.024373731 21000  36000
    ## 92                          529         33       0.029649596 34000  36000
    ## 93                        10916       1779       0.078584681 25000  35600
    ## 94                       116251      14602       0.075176976 27000  35000
    ## 95                        88548      11268       0.082452199 26000  35000
    ## 96                        52243       8947       0.096797577 25000  35000
    ## 97                        39524       4535       0.069176442 26000  35000
    ## 98                        28966       2727       0.055806815 24000  35000
    ## 99                        30932       3305       0.067960766 27000  35000
    ## 100                       13109       1668       0.063429289 24500  35000
    ## 101                       16642       1067       0.041507819 32000  35000
    ## 102                        7588       1088       0.069162800 20000  35000
    ## 103                       10548       1743       0.097243919 25000  35000
    ## 104                        6625        975       0.068700676 26000  35000
    ## 105                       10982       1518       0.089626262 27000  35000
    ## 106                        9085       2006       0.119511469 25000  35000
    ## 107                        9170        962       0.072724524 22000  35000
    ## 108                        6954        842       0.066619195 25000  35000
    ## 109                        5482        463       0.048481675 30000  35000
    ## 110                        6234        749       0.070860927 25000  35000
    ## 111                        2161         78       0.022228555 28000  35000
    ## 112                        1763        322       0.096725743 28600  35000
    ## 113                         383          0       0.000000000 18500  35000
    ## 114                       73531       7195       0.057359929 26000  34000
    ## 115                       59218      11176       0.095666912 25000  34000
    ## 116                       20056       3132       0.075566386 25000  34000
    ## 117                        8801       1718       0.083633531 24000  34000
    ## 118                        8871       1012       0.054082941 23050  34000
    ## 119                        7460       1833       0.112144387 21000  34000
    ## 120                        8073        216       0.016202835 30000  34000
    ## 121                         504          0       0.000000000 29000  34000
    ## 122                        3236        529       0.069779712 23000  33500
    ## 123                        4542        483       0.058545455 23000  33500
    ## 124                      100336      13874       0.070724732 24000  33400
    ## 125                       56561       8608       0.084951001 25000  33000
    ## 126                       27521       4410       0.089836827 25000  33000
    ## 127                       21735       2409       0.059821207 24000  33000
    ## 128                       23106       2393       0.061169193 25000  33000
    ## 129                       15266       1379       0.050306435 24000  33000
    ## 130                        5821       1302       0.104435710 25000  33000
    ## 131                        5816        547       0.059211951 30000  33000
    ## 132                        4714        757       0.092305816 24000  33000
    ## 133                        3912        437       0.054475193 23000  33000
    ## 134                        9193        833       0.052228980 25000  32500
    ## 135                       12809       2183       0.082101621 25000  32400
    ## 136                       21816       4267       0.096051684 23000  32200
    ## 137                       16537       1206       0.038637747 25000  32100
    ## 138                       81180      14345       0.087723590 23000  32000
    ## 139                       86540       7297       0.046585715 23400  32000
    ## 140                       57978       5593       0.051467273 24000  32000
    ## 141                       33438       4657       0.078267592 25000  32000
    ## 142                       15740       3718       0.105772240 22000  32000
    ## 143                        5679       1108       0.103454715 27000  32000
    ## 144                        4522        314       0.045454545 22900  32000
    ## 145                        3247        266       0.047263682 28000  32000
    ## 146                      174438      28169       0.083810867 24000  31500
    ## 147                       21425       3918       0.075959674 22300  31000
    ## 148                       13651       1920       0.074667496 24000  31000
    ## 149                        9965       1128       0.060298284 23000  31000
    ## 150                       31877       5486       0.084186296 21000  30500
    ## 151                       26906       3355       0.067128194 22900  30000
    ## 152                       27588       3329       0.068827920 25000  30000
    ## 153                       10824        917       0.050862499 22000  30000
    ## 154                        6322       1465       0.102197419 22000  30000
    ## 155                        8457        496       0.036545830 24000  30000
    ## 156                        3838        419       0.051907830 20800  30000
    ## 157                        5061        326       0.037819026 24000  30000
    ## 158                        2661        372       0.068584071 20000  30000
    ## 159                       13944       1617       0.062628297 22000  29000
    ## 160                        7413       1368       0.089552239 19200  29000
    ## 161                        5949        510       0.055676856 20000  29000
    ## 162                         936         82       0.059766764 23000  29000
    ## 163                       13232       3395       0.102791571 20000  28000
    ## 164                       14460       1487       0.047584000 20000  28000
    ## 165                       20748       1360       0.040104981 21000  28000
    ## 166                        3214        846       0.107115726 22900  27500
    ## 167                       16891       3040       0.077541130 19200  27000
    ## 168                        7832       1340       0.081742207 20000  27000
    ## 169                        3602        304       0.046320280 20000  26000
    ## 170                        1211        148       0.065112187 24000  25000
    ## 171                        1293        368       0.149048198 25000  25000
    ## 172                        2738        214       0.053620646 19200  23400
    ## 173                         410         87       0.104945718 20000  22000
    ##      p75th college_jobs non_college_jobs low_wage_jobs
    ## 1   125000         1534              364           193
    ## 2    90000          350              257            50
    ## 3   105000          456              176             0
    ## 4    80000          529              102             0
    ## 5    75000        18314             4440           972
    ## 6   102000         1142              657           244
    ## 7    72000         1768              314           259
    ## 8   109000          972              500           220
    ## 9    70000        52844            16384          3253
    ## 10   72000        45829            10874          3170
    ## 11   75000        23694             5721           980
    ## 12   70000         8184             2425           372
    ## 13   70000         6439             2471           789
    ## 14   65000         2626              391            81
    ## 15   74000         2439              947           263
    ## 16   76000         3603             1595           524
    ## 17   67000         8306             3235           640
    ## 18   69000        26898            11734          3192
    ## 19   65000         1665              649           137
    ## 20   54000          402              528           144
    ## 21   70000        68622            25667          5144
    ## 22   70000         1183             1274           485
    ## 23   60000         5126             2686           696
    ## 24   62000         1911              305            70
    ## 25   60000         6342             5741           708
    ## 26   60000        28526             9356          2899
    ## 27   60000         3275             5351           703
    ## 28   60000         1466             3629           285
    ## 29   65000         3445             2426           365
    ## 30   70000         1550             1871           340
    ## 31   56000         2028              830           260
    ## 32   60000         1017             1269           142
    ## 33   66000          693             1714           755
    ## 34   57000          501               50            49
    ## 35   58000       151643            26146          6193
    ## 36   64000        24243            48447          9910
    ## 37   65000        25582            37057         10653
    ## 38   58000         1578             4612          1284
    ## 39   65000         1394             2454           480
    ## 40   53000          162             1475           124
    ## 41   56000        11417            39323         10886
    ## 42   60000        34800            14829          4569
    ## 43   60000        13344            11783          1672
    ## 44   68000        18674             4576          1823
    ## 45   50000         5546             7176          1002
    ## 46   58000         4390             4102           608
    ## 47   60000         2298             1200           343
    ## 48   63000         2437              803           357
    ## 49   45000          603              478            93
    ## 50   50000          459              996           186
    ## 51   50000          482              844           245
    ## 52   65000         2091             6948          1270
    ## 53   78000          452               67            25
    ## 54   46000         2024             1033           263
    ## 55   60000         1369              921           135
    ## 56   43000          509              221             0
    ## 57   53000         6774             9570          2499
    ## 58   55000        29334           100831         27320
    ## 59   50000        16178            13724          4221
    ## 60   50000         3383             9482          3046
    ## 61   90000        11573             4493          1121
    ## 62   47000         7225             3145          1168
    ## 63   51000         2236             8937          1758
    ## 64   50000         1925             6221          1362
    ## 65   50000         2418             4717           839
    ## 66   56000         2446             3896           386
    ## 67   52000         1861             2121           406
    ## 68   45000         1675              678           201
    ## 69   54000          744             1654           573
    ## 70   42000          801             1591           302
    ## 71   53000          559             1224           272
    ## 72   54000          535              893            94
    ## 73   55000          530              465           269
    ## 74   40000            0                0             0
    ## 75   49900        30382            14718          4288
    ## 76   45000          221             1659            81
    ## 77   50000        36720           148395         32395
    ## 78   50000        25320            93889         27968
    ## 79   50000        36854            66947         19803
    ## 80   50000         5350             6830          1905
    ## 81   50000         5577             3174          1246
    ## 82   50000         2354             3244           308
    ## 83   50000        15654             8394          3012
    ## 84   40000          677              184            56
    ## 85   49000         2593             2941           352
    ## 86   47000         4858             2792           959
    ## 87   45000         2406             9629          1906
    ## 88   46000         2002             6454          1336
    ## 89   42000         5652             3835          1422
    ## 90   60000          919             2313           496
    ## 91   41000          784              591           221
    ## 92   45000          434              593            37
    ## 93   40200         8149            10076          3175
    ## 94   45000        40763            97964         27440
    ## 95   45000        24348            88858         18404
    ## 96   45000        37389            38119         14839
    ## 97   42900        23279            26672          8512
    ## 98   50000        17923            22039          5751
    ## 99   47000         9659            23059          7214
    ## 100  44000         8465            11818          3677
    ## 101  42000        20185             3797          1179
    ## 102  50000         6587             6894          2237
    ## 103  45000         3373            10605          1895
    ## 104  45000         6535             5473          2449
    ## 105  42000         2589             8592          1391
    ## 106  45000         4545             8794          2495
    ## 107  52000         4575             6147           557
    ## 108  42000         4333             5808          1405
    ## 109  44000         5605             2301           902
    ## 110  44000         5176             3903          1061
    ## 111  50000         1808             1317           237
    ## 112  48000         1096             1692           327
    ## 113  44000          355              144             0
    ## 114  41000        82007            31112         11443
    ## 115  47000        35336            54569         16839
    ## 116  45000        15051            18193          5267
    ## 117  45000         4956            10343          3168
    ## 118  42000        10928             5561          1806
    ## 119  45000         5225             7385          1854
    ## 120  40000        10699             1977           786
    ## 121  35000          346              206           111
    ## 122  40000         3051             3539          1159
    ## 123  48000         4253             2722           459
    ## 124  45000        88232            81109         28339
    ## 125  44000        29051            48899         13748
    ## 126  45000        12855            25297          6429
    ## 127  41000        22215            14616          4468
    ## 128  42000         2325            23341          9063
    ## 129  40000        17985             6824          2819
    ## 130  40000         4122             5695          2085
    ## 131  45000         5284             2438           657
    ## 132  40000         2630             3906          1470
    ## 133  42000         2856             4159           976
    ## 134  38000        10304             3967          1385
    ## 135  45000         9364            12889          3816
    ## 136  47100        14444            20313          8051
    ## 137  40000        20821             8260          2767
    ## 138  41000        57690            71827         26503
    ## 139  38000       108085            36972         11502
    ## 140  43000        27581            63946         16838
    ## 141  42000        18565            28558          9030
    ## 142  42000         7368            20721          5862
    ## 143  50000         3602             4778          1634
    ## 144  40000         2089             3545          1231
    ## 145  39000         4214             1106           591
    ## 146  41000       125148           141860         48207
    ## 147  42000        13752            28786          9286
    ## 148  40000        12777             9328          2042
    ## 149  40000         5139             9738          3426
    ## 150  41000        20792            32725         11880
    ## 151  40000        20985            20133          5248
    ## 152  35000        27449            14416          4344
    ## 153  40000         5443             9571          2125
    ## 154  40000         3849             7635          2840
    ## 155  37000        10766             1949           722
    ## 156  40000         2960             3948          1650
    ## 157  35000         2878             4595           724
    ## 158  49000         1168             3354          1141
    ## 159  38000         9927            12037          3304
    ## 160  38300         3948             8707          3586
    ## 161  36000          563             7384          3163
    ## 162  42100          483              626            31
    ## 163  38000         9805            16693          6866
    ## 164  40000        19957             9404          5125
    ## 165  35000        23515             7705          2868
    ## 166  38000         2326             3703          1115
    ## 167  35000         6994            25313         11068
    ## 168  35000         4855             8100          3466
    ## 169  39000         2771             2947           743
    ## 170  34000         1488              615            82
    ## 171  40000          986              870           622
    ## 172  26000         2403             1245           308
    ## 173  22000          288              338           192

``` r
# Typical style once {tidyverse} is loaded:
# college_recent_grads <- read_csv("data/recent-grads.csv")
```

Notice that this dataset is in a folder called `data`. We read it in
with the `read_csv` function, then saved the results as a new data frame
called `college_recent_grads`. You can view the entire dataset by
clicking on the name of the data frame in the **Environment** tab (make
sure you have run both the `load_packages` and `load_data` code chunks).

Explore and describe what the `message` option does in `load_data` code
chunk.

**Response**: I bet it has a bunch of annoying stuff, but I won’t waste
my time looking and knitting.

Turn the `message` option off and continue in this activity.

#### Aside

Base R has a function for reading in a csv file as well. First, knit
this report and look at the output for the `load_data` code chunk.

Now, edit the reading in data code in the `load_data` code chunk to
instead be:

    college_recent_grads <- read.csv("data/recent-grads.csv")

Then, knit this report and look at the output for the `load_data` code
chunk. What did you notice about the output from these different
functions? When creating a report, which function would be better to
use?

Now, edit the reading in data code in the `load_data` back to what is
was originally:

    college_recent_grads <- readr::read_csv("data/recent-grads.csv")

If you were to load the data using `read.csv` in an `.Rmd` file and try
to view it, it will print the ENTIRE dataset - this could make a short
report many hundreds of pages depending on the size of your dataset.
Historically, there were some other benefits of `readr::read_csv` over
`read.csv`, but these have mostly been updated to no longer be issues. I
strongly recommend that you use `readr::read_csv` instead of `read.csv`.

![](README-img/noun_pause.png) **Planned Pause Point**: If you have any
questions, contact your instructor. Otherwise feel free to continue on.

### Data Codebook

Descriptions of the variables are provided below.

| Header                         | Description                                                                 |
|:-------------------------------|:----------------------------------------------------------------------------|
| `rank`                         | Rank by median earnings                                                     |
| `major_code`                   | Major code, FO1DP in ACS PUMS                                               |
| `major`                        | Major description                                                           |
| `major_category`               | Category of major from Carnevale et al                                      |
| `total`                        | Total number of people with major                                           |
| `sample_size`                  | Sample size (unweighted) of full-time, year-round ONLY (used for earnings)  |
| `men`                          | Male graduates                                                              |
| `women`                        | Female graduates                                                            |
| `sharewomen`                   | Women as share of total                                                     |
| `employed`                     | Number employed (ESR == 1 or 2)                                             |
| `employed_full_time`           | Employed 35 hours or more                                                   |
| `employed_part_time`           | Employed less than 35 hours                                                 |
| `employed_full_time_yearround` | Employed at least 50 weeks (WKW == 1) and at least 35 hours (WKHP &gt;= 35) |
| `unemployed`                   | Number unemployed (ESR == 3)                                                |
| `unemployment_rate`            | Unemployed / (Unemployed + Employed)                                        |
| `median`                       | Median earnings of full-time, year-round workers                            |
| `p25th`                        | 25th percentile of earnings                                                 |
| `p75th`                        | 75th percentile of earnings                                                 |
| `college_jobs`                 | Number with job requiring a college degree                                  |
| `non_college_jobs`             | Number with job not requiring a college degree                              |
| `low_wage_jobs`                | Number in low-wage service jobs                                             |

We can see that this data frame has a lot of useful information. In the
remaining sections we will answer the following questions (I’ll tell you
what to do, you don’t need to do anything yet):

-   Which major has the lowest unemployment rate?
-   Which major has the highest percentage of women?
-   Which STEM majors have incomes less than the median income of all
    majors?

Note that the ACS only asks [one
question](https://www.census.gov/acs/www/about/why-we-ask-each-question/sex/)
about a person’s sexual identity and we are therefore missing a lot of
important details about individuals.

## Analysis

### Which major has the lowest unemployment rate?

#### Describe your process

What information (variables) do we need to answer this question?
Describe how you would go about answering this question using a
different software (e.g., Excel, SAS, Python) that you are familiar with
or simply a general process. You do not need to code anything. As you
write this process, think of it as a series of steps and it might be
helpful to start at the goal and work backwards.

**Response**:

#### Using `{dplyr}`

In the R code chunk below, name it `rearrange_college`.

Take the `college_recent_grads` dataset, *then* `arrange` the dataset by
`unemployment_rate`.

We have all of the information to answer our question (i.e., “Which
major has the lowest unemployment rate?”), but it is not in an effective
format. The major names barely fit on the page, we have many variables
are not that useful in answering our question (e.g., `major_code`,
`major_category`), and some variables that we might want
front-and-center are not easily viewed (i.e., `unemployment_rate`).
Also, notice that by default when you *arrange* by a variable, it
defaults to *ascending* order.

#### Removing unnecessary information

Use the pipeline that you made in the `rearrange_college` code chunk as
the start to this solution, **then** `select` only the variables `rank`,
`major`, and `unemployment_rate`. Name this code chunk
`lowest_unemploy`.

**Response**:

<img src="README-img/noun_pause.png" alt="pause" width = "20"/>
<b>Planned Pause Point</b>: If you feel that you have a good
understanding of these commands, feel free to start working on your
project. The remainder of this activity will help to expand these
commands.

### Which major has the highest proportion of women?

Using the `college_recent_grads` dataset and functions from `{dplyr}`,
`arrange` the dataset by `sharewomen`, and `select` only `rank`,
`major`, and `sharewomen`. Name your code chunk `highest_prop_women`.

Discuss your output as it relates to the research question.

**Response**:

![](README-img/noun_pause.png) **Planned Pause Point**: If you have any
questions, contact your instructor. Otherwise feel free to continue on.

### Which STEM majors have incomes less than the median income of all majors?

One of the sections of the FiveThirtyEight story is “All STEM fields
aren’t the same”. We will see if this is true.

Below is a new vector called `stem_categories` that lists the *major
categories* (this is not the `majors` variable - look back at the Data
Codebook) that are considered STEM fields.

``` r
stem_categories <- c("Biology & Life Science",
                     "Computers & Mathematics",
                     "Engineering",
                     "Physical Sciences")
```

In our next activity we will see how to calculate summary statistics,
but for now believe me that the median salary for all majors is $36,000.

Using the `stem_categories` vector and knowledge that the median salary
for all majors is $36,000 to *keep* the rows in the
`college_recent_grads` data set that are in the STEM fields and earn
*less* than the `median` salary of all majors. Only display the
variables `major`, `p25th`, `median`, and `p75th` Name the code chunk
`stem_low_salaries`.

Discuss your output as it relates to the research question.

**Response**:

![](README-img/noun_pause.png) **(Final) Planned Pause Point**: If you
have any questions, contact your instructor. Otherwise feel free to
continue on.

Knit, then stage everything listed in your **Git** pane, commit (with a
meaningful commit message), and push to your GitHub repo. Go to GitHub
and verify that your `activity04-data-pieplines.Rmd` file appears as you
intended it to.

You can now go back to the `README` file.

## Attribution

This activity is inspired by a lab from [Dr. Mine
Çetinkaya-Rundel](http://www2.stat.duke.edu/~mc301/)’s STA 199 course.
