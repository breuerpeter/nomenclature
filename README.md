# nomenclature

### How to use

1. Add this repo to your project by cloning its contents to the project root dir

    ```
    git clone https://github.com/breuerpeter/nomenclature.git PROJECT_ROOT_DIR
    ```

2. Include the config file in your project's main `.tex` file `PROJECT_MAIN.tex` by adding the following line to the preamble

    ```
    \input{nomenclature/config.tex}
    ```

3. Include the desired nomenclature topics in your project's main `.tex` file by adding the following line to the preamble for each topic `XXX`

    ```
    \input{nomenclature/topics/XXX/glossary.tex}
    ```

4. (Optional) include the [notation section](notation/README.md)

4. Insert glossary entries in your project using the following syntax

    | Syntax        | Function                       |
    | ------------- | ------------------------------ |
    | `\gls{KEY}`   | print in lowercase             |
    | `\glspl{KEY}` | print plural form in lowercase |
    | `\Gls{KEY}`   | print in uppercase             |
    | `\Glspl{KEY}` | print plural form in uppercase |

    Note: see [below](#key-naming-convention) for key conventions
    
5. Include the file that prints the nomenclature in your project's main `.tex` file by adding the following line in the desired location

    ```
    \input{nomenclature/print.tex}
    ```

6. Make sure your project has all the packages listed at the top of `config.tex`


7. Build your project

    ```
    pdflatex PROJECT_MAIN
    bib2gls -g PROJECT_MAIN
    pdflatex PROJECT_MAIN
    pdflatex PROJECT_MAIN
    ```

## Key naming convention

Note: components are separated by an underscore `_`

### Symbols

#### 1. Quantity descriptor

| Prefix       | Meaning          |
| ------------ | ---------------- |
| (none)       | scalar           |
| `pt`         | point            |
| `vec`        | vector           |
| `mat`        | matrix           |
| `fr`         | frame            |
| `set`        | set              |
| `no`         | number of        |
| `fn`         | function         |
| `pr`         | probability      |
| `rv`         | random variable  |

Note: the prefix is followed by the name of the quantity (in a lowerCamelCase fashion)

#### 2. (If applicable) reference frame

Syntax: `frXXX` to indicate reference frame `XXX`

#### 3. (Optional) quantity details

| Abbreviation | Meaning                           |
| ------------ | --------------------------------- |
| `compXXX`    | `XXX` component of quantity       |
| `hom`        | homogeneous coordinates           |
| `norm`       | normalized coordinates            |

### Terms

1. `DEF`
2. Term in lowerCamelCase

## TODO

Adding abbreviation subtitles (e.g. "Intialism") via `@indexplural{initialism,text={Initialism},topic={abbreviation}}` in `abbreviations.bib` is causing problems.