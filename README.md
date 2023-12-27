# emuser

> Yes, it's a poke at Erewhon.

A pretty decent LaTeX resume template. Try it for yourself!

![out/**emuser**.pdf](images/emuser.png)

## Usage

Clone this repoistory or copy [this Overleaf template](hahaha). You only need to work in `emuser.tex` but you may edit `emuserutils.sty` if you're feeling dangerous. The TeX file is self-documenting/instructional, but here's the overview:

- The majority of this resume is structured as `sectionList`s: a section title with section items (don't forget to start each item with `\item`). E.g.
  ![Section list of "Title" with "Item 1" and "Item 2"](images/sectionList.png)

  ```latex
  \begin{sectionList}{Title}
    \item \lr{Item 1}{}
    \item \lr{Item 2}{}
  \end{sectionList}
  ```

- `setBulletsSpacing` affects items within `bullets` and `nobullets`
- `setSectionSpacing` affects items within and across `sectionList`

- `lr` is a section item left-right columns, requiring 2-6 values via 2 `{}` and 0-4 `[]` (order matters). E.g.

  ![Left-right columns of "Company" and "Location" with "Position" and "Dates](images/lrCompany.png)

  ```latex
  \lr{Company}{Location}
  [Position][Dates]
  ```

  ![Left-right columns of "University" with "Degree 2," "Degree 1," and two "Dates"](images/lrUniversity.png)

  ```latex
  \lr{University}{}  % Omits location
  [Degree 2][Dates]
  [Degree 1][Dates]
  ```

  ![Left-right columns of "Project" and "Dates"](images/lrProject.png)

  ```latex
  \lr{Project}{Dates}  % Right-column is non-italicized if there are only two values
  ```

- `lcr` is an alternative section item of a left-center-right columns, requring 3 values via `{}`. E.g.
  ![Left-center-right columns of "Left," "Center," and "Right"](images/lcr.png)
  ```latex
  \lcr{Left}{Center}{Right}
  ```
