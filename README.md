# latex-tikzexternalize-name-replace
Externalizes tikz figures that wrap an external figure keeping the same name

```latex

\usetikzlibrary{external}
\tikzexternalize[prefix=figures/]

\def\parsefurther#1#2\endparse{The argument of \detokenize{#1} is 
  ``\detokenize{#2}''% ``\StrBetween{\detokenize{#2}}{./}{\}\}}''%
}

\def\parsefurtherAC#1#2\endparseAC{\detokenize{#2}%
}
\def\getfname#1\endgetfname{%
%\StrBehind{\parsefurtherAC#1\endparseAC}{./}%
\StrGobbleRight{\parsefurtherAC#1\endparseAC}{5}[\tempString]%
%\StrBehind{\noexpandarg\StrGobbleRight{\parsefurtherAC#1\endparseAC}{1}}{./}%
\StrBehind{\tempString}{./}[\tempStringA]
\tikzsetnextfilename{\tempStringA}
}
```
