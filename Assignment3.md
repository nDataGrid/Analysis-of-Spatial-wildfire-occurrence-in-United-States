This dataset is a dummy data created by IBM data scientists to uncover
multiple factor which leads to employee’s attrition.  
This is the second dataset chosen from Assignment#1

Reference:
<https://www.kaggle.com/pavansubhasht/ibm-hr-analytics-attrition-dataset>

Loading of Libraries

``` r
library(tidyverse)
library(ggplot2)
```

Loading of Dataset

``` r
emp_attrition <- read.csv("F:/RCodes/DAB501/WA_Fn-UseC_-HR-Employee-Attrition.csv")
```

**Exercise 1:**  
*Part 1 : Head of the Dataset*

``` r
head(emp_attrition)
```

    ##   ï..Age Attrition    BusinessTravel DailyRate             Department
    ## 1     41       Yes     Travel_Rarely      1102                  Sales
    ## 2     49        No Travel_Frequently       279 Research & Development
    ## 3     37       Yes     Travel_Rarely      1373 Research & Development
    ## 4     33        No Travel_Frequently      1392 Research & Development
    ## 5     27        No     Travel_Rarely       591 Research & Development
    ## 6     32        No Travel_Frequently      1005 Research & Development
    ##   DistanceFromHome Education EducationField EmployeeCount EmployeeNumber
    ## 1                1         2  Life Sciences             1              1
    ## 2                8         1  Life Sciences             1              2
    ## 3                2         2          Other             1              4
    ## 4                3         4  Life Sciences             1              5
    ## 5                2         1        Medical             1              7
    ## 6                2         2  Life Sciences             1              8
    ##   EnvironmentSatisfaction Gender HourlyRate JobInvolvement JobLevel
    ## 1                       2 Female         94              3        2
    ## 2                       3   Male         61              2        2
    ## 3                       4   Male         92              2        1
    ## 4                       4 Female         56              3        1
    ## 5                       1   Male         40              3        1
    ## 6                       4   Male         79              3        1
    ##                 JobRole JobSatisfaction MaritalStatus MonthlyIncome MonthlyRate
    ## 1       Sales Executive               4        Single          5993       19479
    ## 2    Research Scientist               2       Married          5130       24907
    ## 3 Laboratory Technician               3        Single          2090        2396
    ## 4    Research Scientist               3       Married          2909       23159
    ## 5 Laboratory Technician               2       Married          3468       16632
    ## 6 Laboratory Technician               4        Single          3068       11864
    ##   NumCompaniesWorked Over18 OverTime PercentSalaryHike PerformanceRating
    ## 1                  8      Y      Yes                11                 3
    ## 2                  1      Y       No                23                 4
    ## 3                  6      Y      Yes                15                 3
    ## 4                  1      Y      Yes                11                 3
    ## 5                  9      Y       No                12                 3
    ## 6                  0      Y       No                13                 3
    ##   RelationshipSatisfaction StandardHours StockOptionLevel TotalWorkingYears
    ## 1                        1            80                0                 8
    ## 2                        4            80                1                10
    ## 3                        2            80                0                 7
    ## 4                        3            80                0                 8
    ## 5                        4            80                1                 6
    ## 6                        3            80                0                 8
    ##   TrainingTimesLastYear WorkLifeBalance YearsAtCompany YearsInCurrentRole
    ## 1                     0               1              6                  4
    ## 2                     3               3             10                  7
    ## 3                     3               3              0                  0
    ## 4                     3               3              8                  7
    ## 5                     3               3              2                  2
    ## 6                     2               2              7                  7
    ##   YearsSinceLastPromotion YearsWithCurrManager
    ## 1                       0                    5
    ## 2                       1                    7
    ## 3                       0                    0
    ## 4                       3                    0
    ## 5                       2                    2
    ## 6                       3                    6

*Part 2: Tail of Dataset*

``` r
tail(emp_attrition)
```

    ##      ï..Age Attrition    BusinessTravel DailyRate             Department
    ## 1465     26        No     Travel_Rarely      1167                  Sales
    ## 1466     36        No Travel_Frequently       884 Research & Development
    ## 1467     39        No     Travel_Rarely       613 Research & Development
    ## 1468     27        No     Travel_Rarely       155 Research & Development
    ## 1469     49        No Travel_Frequently      1023                  Sales
    ## 1470     34        No     Travel_Rarely       628 Research & Development
    ##      DistanceFromHome Education EducationField EmployeeCount EmployeeNumber
    ## 1465                5         3          Other             1           2060
    ## 1466               23         2        Medical             1           2061
    ## 1467                6         1        Medical             1           2062
    ## 1468                4         3  Life Sciences             1           2064
    ## 1469                2         3        Medical             1           2065
    ## 1470                8         3        Medical             1           2068
    ##      EnvironmentSatisfaction Gender HourlyRate JobInvolvement JobLevel
    ## 1465                       4 Female         30              2        1
    ## 1466                       3   Male         41              4        2
    ## 1467                       4   Male         42              2        3
    ## 1468                       2   Male         87              4        2
    ## 1469                       4   Male         63              2        2
    ## 1470                       2   Male         82              4        2
    ##                        JobRole JobSatisfaction MaritalStatus MonthlyIncome
    ## 1465      Sales Representative               3        Single          2966
    ## 1466     Laboratory Technician               4       Married          2571
    ## 1467 Healthcare Representative               1       Married          9991
    ## 1468    Manufacturing Director               2       Married          6142
    ## 1469           Sales Executive               2       Married          5390
    ## 1470     Laboratory Technician               3       Married          4404
    ##      MonthlyRate NumCompaniesWorked Over18 OverTime PercentSalaryHike
    ## 1465       21378                  0      Y       No                18
    ## 1466       12290                  4      Y       No                17
    ## 1467       21457                  4      Y       No                15
    ## 1468        5174                  1      Y      Yes                20
    ## 1469       13243                  2      Y       No                14
    ## 1470       10228                  2      Y       No                12
    ##      PerformanceRating RelationshipSatisfaction StandardHours StockOptionLevel
    ## 1465                 3                        4            80                0
    ## 1466                 3                        3            80                1
    ## 1467                 3                        1            80                1
    ## 1468                 4                        2            80                1
    ## 1469                 3                        4            80                0
    ## 1470                 3                        1            80                0
    ##      TotalWorkingYears TrainingTimesLastYear WorkLifeBalance YearsAtCompany
    ## 1465                 5                     2               3              4
    ## 1466                17                     3               3              5
    ## 1467                 9                     5               3              7
    ## 1468                 6                     0               3              6
    ## 1469                17                     3               2              9
    ## 1470                 6                     3               4              4
    ##      YearsInCurrentRole YearsSinceLastPromotion YearsWithCurrManager
    ## 1465                  2                       0                    0
    ## 1466                  2                       0                    3
    ## 1467                  7                       1                    7
    ## 1468                  2                       0                    3
    ## 1469                  6                       0                    8
    ## 1470                  3                       1                    2

*Part 3: Summary of Dataset*

``` r
summary(emp_attrition)
```

    ##      ï..Age       Attrition         BusinessTravel       DailyRate     
    ##  Min.   :18.00   Length:1470        Length:1470        Min.   : 102.0  
    ##  1st Qu.:30.00   Class :character   Class :character   1st Qu.: 465.0  
    ##  Median :36.00   Mode  :character   Mode  :character   Median : 802.0  
    ##  Mean   :36.92                                         Mean   : 802.5  
    ##  3rd Qu.:43.00                                         3rd Qu.:1157.0  
    ##  Max.   :60.00                                         Max.   :1499.0  
    ##   Department        DistanceFromHome   Education     EducationField    
    ##  Length:1470        Min.   : 1.000   Min.   :1.000   Length:1470       
    ##  Class :character   1st Qu.: 2.000   1st Qu.:2.000   Class :character  
    ##  Mode  :character   Median : 7.000   Median :3.000   Mode  :character  
    ##                     Mean   : 9.193   Mean   :2.913                     
    ##                     3rd Qu.:14.000   3rd Qu.:4.000                     
    ##                     Max.   :29.000   Max.   :5.000                     
    ##  EmployeeCount EmployeeNumber   EnvironmentSatisfaction    Gender         
    ##  Min.   :1     Min.   :   1.0   Min.   :1.000           Length:1470       
    ##  1st Qu.:1     1st Qu.: 491.2   1st Qu.:2.000           Class :character  
    ##  Median :1     Median :1020.5   Median :3.000           Mode  :character  
    ##  Mean   :1     Mean   :1024.9   Mean   :2.722                             
    ##  3rd Qu.:1     3rd Qu.:1555.8   3rd Qu.:4.000                             
    ##  Max.   :1     Max.   :2068.0   Max.   :4.000                             
    ##    HourlyRate     JobInvolvement    JobLevel       JobRole         
    ##  Min.   : 30.00   Min.   :1.00   Min.   :1.000   Length:1470       
    ##  1st Qu.: 48.00   1st Qu.:2.00   1st Qu.:1.000   Class :character  
    ##  Median : 66.00   Median :3.00   Median :2.000   Mode  :character  
    ##  Mean   : 65.89   Mean   :2.73   Mean   :2.064                     
    ##  3rd Qu.: 83.75   3rd Qu.:3.00   3rd Qu.:3.000                     
    ##  Max.   :100.00   Max.   :4.00   Max.   :5.000                     
    ##  JobSatisfaction MaritalStatus      MonthlyIncome    MonthlyRate   
    ##  Min.   :1.000   Length:1470        Min.   : 1009   Min.   : 2094  
    ##  1st Qu.:2.000   Class :character   1st Qu.: 2911   1st Qu.: 8047  
    ##  Median :3.000   Mode  :character   Median : 4919   Median :14236  
    ##  Mean   :2.729                      Mean   : 6503   Mean   :14313  
    ##  3rd Qu.:4.000                      3rd Qu.: 8379   3rd Qu.:20462  
    ##  Max.   :4.000                      Max.   :19999   Max.   :26999  
    ##  NumCompaniesWorked    Over18            OverTime         PercentSalaryHike
    ##  Min.   :0.000      Length:1470        Length:1470        Min.   :11.00    
    ##  1st Qu.:1.000      Class :character   Class :character   1st Qu.:12.00    
    ##  Median :2.000      Mode  :character   Mode  :character   Median :14.00    
    ##  Mean   :2.693                                            Mean   :15.21    
    ##  3rd Qu.:4.000                                            3rd Qu.:18.00    
    ##  Max.   :9.000                                            Max.   :25.00    
    ##  PerformanceRating RelationshipSatisfaction StandardHours StockOptionLevel
    ##  Min.   :3.000     Min.   :1.000            Min.   :80    Min.   :0.0000  
    ##  1st Qu.:3.000     1st Qu.:2.000            1st Qu.:80    1st Qu.:0.0000  
    ##  Median :3.000     Median :3.000            Median :80    Median :1.0000  
    ##  Mean   :3.154     Mean   :2.712            Mean   :80    Mean   :0.7939  
    ##  3rd Qu.:3.000     3rd Qu.:4.000            3rd Qu.:80    3rd Qu.:1.0000  
    ##  Max.   :4.000     Max.   :4.000            Max.   :80    Max.   :3.0000  
    ##  TotalWorkingYears TrainingTimesLastYear WorkLifeBalance YearsAtCompany  
    ##  Min.   : 0.00     Min.   :0.000         Min.   :1.000   Min.   : 0.000  
    ##  1st Qu.: 6.00     1st Qu.:2.000         1st Qu.:2.000   1st Qu.: 3.000  
    ##  Median :10.00     Median :3.000         Median :3.000   Median : 5.000  
    ##  Mean   :11.28     Mean   :2.799         Mean   :2.761   Mean   : 7.008  
    ##  3rd Qu.:15.00     3rd Qu.:3.000         3rd Qu.:3.000   3rd Qu.: 9.000  
    ##  Max.   :40.00     Max.   :6.000         Max.   :4.000   Max.   :40.000  
    ##  YearsInCurrentRole YearsSinceLastPromotion YearsWithCurrManager
    ##  Min.   : 0.000     Min.   : 0.000          Min.   : 0.000      
    ##  1st Qu.: 2.000     1st Qu.: 0.000          1st Qu.: 2.000      
    ##  Median : 3.000     Median : 1.000          Median : 3.000      
    ##  Mean   : 4.229     Mean   : 2.188          Mean   : 4.123      
    ##  3rd Qu.: 7.000     3rd Qu.: 3.000          3rd Qu.: 7.000      
    ##  Max.   :18.000     Max.   :15.000          Max.   :17.000

**Exercise 2:**  
*Question 1: How has work-life balance affected the attrition rate?*

``` r
work_bal_attr <- emp_attrition %>% select(Attrition, BusinessTravel, WorkLifeBalance) %>% 
  group_by(Attrition, BusinessTravel) %>% 
  summarize(count = n()) %>% 
  mutate(pct_attr = round(prop.table(count),2) * 100)
```

``` r
plot1 <- ggplot(work_bal_attr, aes(x = Attrition, y = count, 
                          fill = BusinessTravel, color = Attrition)) +
  facet_wrap(~BusinessTravel) +
  geom_bar(stat='identity')
plot1
```

![](Assignment3_files/figure-markdown_github/unnamed-chunk-7-1.png)

*Question 2: What are the top 5 job roles that has highest rate of
attrition?*

``` r
job_role_attr <- emp_attrition %>% select(JobRole, Attrition) %>%
  group_by(JobRole, Attrition) %>% summarize(amount = n()) %>%
  mutate(pct_jr = round(prop.table(amount), 2) * 100) %>% arrange(pct_jr)
```

``` r
job_role_attr1 <-
  job_role_attr %>% select(JobRole, Attrition, amount, pct_jr) %>%
  filter(Attrition == "Yes") %>% arrange(pct_jr)

#Learnt a new thing while performing slice()  
#slice will work with data.frame() and not with parameter  
job_role_attr5 <- slice(data.frame(job_role_attr1),-4:0)
job_role_attr5
```

    ##                 JobRole Attrition amount pct_jr
    ## 1    Research Scientist       Yes     47     16
    ## 2       Sales Executive       Yes     57     17
    ## 3       Human Resources       Yes     12     23
    ## 4 Laboratory Technician       Yes     62     24
    ## 5  Sales Representative       Yes     33     40

*Question 3: Has the overtime in the company led to attrition?*

``` r
attr_ot <- emp_attrition %>% select(OverTime, Attrition) %>%
  filter(Attrition == "Yes") %>%
  group_by(Attrition, OverTime) %>%
  summarize(n = n()) %>% mutate(pct_ot = round(prop.table(n), 2) * 100)
```

``` r
plot2 <- ggplot(attr_ot, aes(x = OverTime, y = pct_ot)) +
  geom_bar(stat = 'identity')
plot2
```

![](Assignment3_files/figure-markdown_github/unnamed-chunk-11-1.png)
