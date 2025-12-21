# `emuser`: a painless LaTeX resume template

> Yes, it's a play on Erewhon. (I recently learned `reverse("nowhere") != "erewhon"`, but `reverse("resume") == "emuser"`.)

<img src="images/emuser.png" width="512">

_Your resume could look like this! See [the PDF](out/emuser.pdf)._

## Why `emuser`?

> The last LaTeX template we'll ever need (hopefully).

[LaTeX](https://www.latex-project.org/)'s been the standard for technical/scientific typesetting, becoming the popular choice for software engineers, etc. thanks to [Jake's template](https://github.com/jakegut/resume). `emuser` attempts to strike the right balance of LaTeX's benefits and downsides, i.e. $emuser = \text{argmax}(\text{benefit}(t)) - \lambda \cdot \text{pain}(t))$. This means:

- **Worry about content, not formatting.** LaTeX forgivingly handles sizing, spacing, etc. for you.
- **Human-readable formatting.** What does `l@{\extracolsep{\fill}}` do? IDK either.
- **Set-and-forget configurations.** Pick a font and margin size, and that's all you probably ever need.
- **Looks great!**

# Start now

Clone this repo or open [this Overleaf template](https://www.overleaf.com/read/ffngfqgdydmt#8f1610)! 

Functionally, you need **both** [`emuser.tex`](emuser.tex) and [`emuserutils.sty`](emuserutils.sty) in the same directory level, but you only need to **edit** [`emuser.tex`](emuser.tex). Only touch [`emuserutils.sty`](emuserutils.sty) if you're unsatisfied with the default options and are feeling dangerous.

### Main Header

For your name and contact information, `lrHeader` is a left-right table requiring 2 values. E.g.

```latex
\lrHeader
{First Last}
{(012) 345-6789 $\vert$ myprofessional@email.com}
```

![Main header of "First Last" with phone number and email](images/lrHeader.png)

### Section Lists

For organizing your education, experience, etc., `sectionList` is a title with items. E.g.

```latex
\begin{sectionList}{Title}
  \item \lr{Item 1}{}
  \item \lr{Item 2}{}
\end{sectionList}
```

![Section list of "Title" with "Item 1" and "Item 2"](images/sectionList.png)

## Section Items

For showing individual experiences, projects, etc., section items are usually **an `item` in a `sectionList`**.

### Headers

- `lr` is a left-right table, requiring 2-6 values via 2 `{}` and 0-4 `[]` (order matters). E.g.

  ```latex
  \lr{Project}{Dates}
  ```

  ![Left-right table of "Project" and "Dates"](images/lrProject.png)

  ```latex
  \lr{Company}{Location}  % Top-right value is italicized
  [Position][Dates]
  ```

  ![Left-right table of "Company" and "Location" with "Position" and "Dates](images/lrCompany.png)

  ```latex
  \lr{University}{}  % Omits location
  [Degree 2][Dates]
  [Degree 1][Dates]
  ```

  ![Left-right table of "University" with "Degree 2," "Degree 1," and two "Dates"](images/lrUniversity.png)

- Alternatively, `lcr` is a left-center-right table, requring 3 values. E.g.
  ```latex
  \lcr{Company}{Position}{Dates}
  ```
  ![Left-center-right table of "Company," "Position," and "Dates"](images/lcr.png)

### Lists

For detailing individual experiences, summarizing skills, etc.: `bullets` and `nobullets`.

- `bullets` take the default set by `setBulletStyle`. E.g.

  ```latex
  \setBulletStyle{$\sharp$}

  \begin{bullets}
      \item I'm a musician!
      \item These bullets are too fancy.
  \end{bullets}
  ```

  ![Bulleted list of two sharp bullets](images/bullets.png)

- Reserve `nobullets` for single-line project details, single-item `sectionList`s, etc. E.g.

  ```latex
  \begin{sectionList}{Skills}
      \item \begin{nobullets}
          \item Skill issue
      \end{nobullets}
  \end{sectionList}
  ```

  ![Section list of "Skills" with "Skill issue"](images/nobullets.png)

- `labeled` is usually **an `item` in a `nobullets`**, requiring 2 values. E.g.
  ```latex
  \labeled{Label}{Content}
  ```
  ![Labeled item of "Label" with "Content](images/labeled.png)

## Spacing

LaTeX automatically handles most spacing, but there are two parameters for you to adjust so your resume fits one page:

- `setBulletsSpacing` affects items in `bullets` and `nobullets`
- `setSectionSpacing` affects titles and items in `sectionList`

If that's not enough, adjust the global font size via `documentclass` and margins via `geometry`.
