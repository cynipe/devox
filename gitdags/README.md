# gitdags docker image

## Usage

```
cd /path/to/workspace
cat >> sample.tex <<_TEX
% taken from  https://github.com/Jubobs/gitdags/wiki
\documentclass{article}

\usepackage{subcaption}
\usepackage{gitdags}

\begin{document}

\begin{figure}
  \begin{subfigure}[b]{\textwidth}
    \centering
    \begin{tikzpicture}
      % Commit DAG
      \gitDAG[grow right sep = 2em]{
        A -- B -- {
          C,
          D -- E,
        }
      };
      % Tag reference
      \gittag
        [v0p1]       % node name
        {v0.1}       % node text
        {above=of A} % node placement
        {A}          % target
      % Remote branch
      \gitremotebranch
        [origmaster]    % node name
        {origin/master} % node text
        {above=of C}    % node placement
        {C}             % target
      % Branch
      \gitbranch
        {master}     % node name and text
        {above=of E} % node placement
        {E}          % target
      % HEAD reference
      \gitHEAD
        {above=of master} % node placement
        {master}          % target
    \end{tikzpicture}
    \subcaption{Before\ldots}
  \end{subfigure}

  \begin{subfigure}[b]{\textwidth}
    \centering
    \begin{tikzpicture}
      \gitDAG[grow right sep = 2em]{
        A -- B -- {
          C -- D' -- E',
          {[nodes=unreachable] D -- E },
        }
      };
      % Tag reference
      \gittag
        [v0p1]       % node name
        {v0.1}       % node text
        {above=of A} % node placement
        {A}          % target
      % Remote branch
      \gitremotebranch
        [origmaster]    % node name
        {origin/master} % node text
        {above=of C}    % node placement
        {C}             % target
      % Branch
      \gitbranch
        {master}      % node name and text
        {above=of E'} % node placement
        {E'}          % target
      % HEAD reference
      \gitHEAD
        {above=of master} % node placement
        {master}          % target
    \end{tikzpicture}
    \subcaption{\ldots{} and after \texttt{git rebase origin/master}}
  \end{subfigure}
  \caption{Demonstrating a typical \texttt{rebase}}
\end{figure}

\end{document}
_TEX

docker run --rm -it $(pwd):/sample cynipe/gitdags pdflatex -output-directory=/sample sample/sample.tex
```

