---
title: |
       ![](Slides_files/RUB.jpg){width=2.5in}
subtitle:  "Workshop: Working with Strings in R"
author: "Simon Ress | Ruhr-Universität Bochum"
#institute: "Conference: 56. Jahrestagung der DGSMP, Leipzig, 2021"
date: "October 18, 2021"

output:
  beamer_presentation:
    keep_md: true
    keep_tex: no
    latex_engine: xelatex
    #theme: metropolis
    slide_level: 2 # which header level should be printed as slides
    incremental: no
header-includes:
  - \usetheme[numbering=fraction]{metropolis}
#Define footer:
  - \definecolor{beaublue}{rgb}{0.74, 0.83, 0.9}
  - \setbeamertemplate{frame footer}{\tiny{\textcolor{beaublue}{Conference 56. Jahrestagung der DGSMP, 2021 | SIMON RESS}}}
#hide footer on title page:
  - |
    \makeatletter
    \def\ps@titlepage{%
      \setbeamertemplate{footline}{}
    }
    \addtobeamertemplate{title page}{\thispagestyle{titlepage}}{}
    \makeatother
#show footer on section's start/title pages:
  #overwrite "plain,c,noframenumbering" in section pages definition -> enables footer:
  - |
    \makeatletter
    \renewcommand{\metropolis@enablesectionpage}{
      \AtBeginSection{
        \ifbeamer@inframe
          \sectionpage
        \else
          \frame[c]{\sectionpage}
        \fi
      }
    }
    \metropolis@enablesectionpage
    \makeatother
  #define footer of section pages:
  - |
    \makeatletter
    \def\ps@sectionpage{%
      \setbeamertemplate{frame footer}{\tiny{\textcolor{beaublue}{Conference 56. Jahrestagung der DGSMP, 2021 | SIMON RESS}}}
    }
    \addtobeamertemplate{section page}{\thispagestyle{sectionpage}}{}
    \makeatother
#add secrtion numbers to TOC:
  - |
    \setbeamertemplate{section in toc}{
    \leavevmode%
    \inserttocsectionnumber. 
    \inserttocsection\par%
    }
    \setbeamertemplate{subsection in toc}{
    \leavevmode\leftskip=2.5em\inserttocsubsection\par}
---



## Content
\tableofcontents[]

# Base R

## Overview

The primary R functions for dealing with strings:

- substr()/substring(): Extract or replace substrings in a character vector
- strsplit(): Split the elements of a character vector x into substrings according to a given character
- paste(): concatenate n number of strings
- nchar(): returns a vector of the number of characters of x

- Dealing wirth regular expressions:
  - grep(), grepl(): These functions search for matches of a regular expression/pattern in a character vector.
  - regexpr(), gregexpr(): Search a character vector for regular expression matches and return the indices of the string where the match begins and the length of the match
  - sub(), gsub(): Search a character vector for regular expression matches and replace that match with another string


## Pattern matching and replacement

grep(): Index in vector which matches regex

```r
grep("b+", c("abc", "bda", "cca a", "abd"))
```

```
## [1] 1 2 4
```

regexpr(): Search a character vector for regular expression matches and return the indices of the string where the match begins and the length of the match

```r
str = "Line 129: O that this too too solid flesh would melt,Thaw, and resolve itself into a dew!"
regexpr("1",str)
```

```
## [1] 6
## attr(,"match.length")
## [1] 1
## attr(,"index.type")
## [1] "chars"
## attr(,"useBytes")
## [1] TRUE
```



## Matching

substr()/substring(): Extract or replace substrings in a character vector

```r
num <- "12345678"
substr(num, 4, 5)
```

```
## [1] "45"
```

```r
substring(num, 1:3, 7)
```

```
## [1] "1234567" "234567"  "34567"
```

## Other

strsplit(): Split the elements of a character vector x into substrings according to a given character

```r
str = "Splitting sentence into words"
strsplit(str, " ")
```

```
## [[1]]
## [1] "Splitting" "sentence"  "into"      "words"
```


paste(): concatenate n number of strings

```r
paste("Count number", "of characters")
```

```
## [1] "Count number of characters"
```

nchar(): returns a vector of the number of characters of x

```r
nchar("Count number of characters")
```

```
## [1] 26
```



# Package: Stringr

## String basics

### String length

## Matching patterns with regular expressions

## Process Matches

- Bullet 1
- Bullet 2
- Bullet 3



# Helpful sources

- [Stringr: Introduction](https://cloud.r-project.org/web/packages/stringr/vignettes/stringr.html)
- [Stringr: Cheatsheet](https://github.com/rstudio/cheatsheets/blob/master/strings.pdf)
- [Stringr: Reference manual](https://cloud.r-project.org/web/packages/stringr/stringr.pdf)
- [Base R String-functions vs Stringr](https://stringr.tidyverse.org/articles/from-base.html)
- [Regular expressions](https://cloud.r-project.org/web/packages/stringr/vignettes/regular-expressions.html)
- [Primary R functions for dealing with regular expressions](https://bookdown.org/rdpeng/rprogdatascience/regular-expressions.html)


```r
summary(cars)
```

```
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
```

## Slide with Plot


```r
plot(pressure)
```

![](Slides_files/figure-beamer/pressure-1.pdf)<!-- --> 



## Two column layout

Here is some text above which goes over to whole slide

<!-- -------------------------- -->
<!-- Start of two column layout -->

:::::::::::::: {.columns}
::: {.column width="50%"}


```r
plot(AirPassengers)
```

![](Slides_files/figure-beamer/AirPassengers-1.pdf)<!-- --> 

:::
::: {.column width="50%"}

- Description of plot
- Second point

:::
::::::::::::::

<!-- End of two column layout -->
<!-- ------------------------ -->


and here some text below which goes over to whole slide


_ _ _  <!-- Create new page without title -->

\LARGE Breakout page

## Using LaTeX Parts: Blocks

As one example of falling back into \LaTeX, consider the example of
three different block environments are pre-defined and may be styled
with an optional background color.

<!-- this sets the background -->
\metroset{block=fill} 

\begin{block}{Default}
  Block content.
\end{block}

\begin{alertblock}{Alert}
  Block content.
\end{alertblock}

\begin{exampleblock}{Example}
  Block content.
\end{exampleblock}