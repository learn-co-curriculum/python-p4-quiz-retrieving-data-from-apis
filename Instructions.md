# Instructions for Creating Curriculum Content Using the `set-up.sh` Script

## Introduction

The `set-up.sh` script in this repo is used to:

1. create the file structure used by the Curriculum Team for writing lessons,
   labs and quizzes,
2. create a GitHub repo for the new content, and
3. create the new content on Canvas.

The script also runs the `github-to-canvas` or `github-to-canvas-quiz` gem to
set up the GitHub workflow that automatically updates the Canvas blueprint when
changes are pushed up to GitHub.

## Dependencies

### `gsed` (Mac users)

Installation using homebrew: `brew install gnu-sed`

### `github-to-canvas` and `github-to-canvas-quiz` gems

Installation: `gem install github-to-canvas && gem install github-to-canvas-quiz`

**Note**: make sure you have installed the most recent version of both gems
before proceeding.

## Usage

As the script is written, to run it you will need to navigate into the
`se-curriculum-templates` directory. It will place the directories for any new
content you create alongside the `se-curriculum-templates` directory, e.g.:

```text
└── containing-directory
     ├── se-curriculum-templates
     |   ├── canvas-quiz
     |   ├── css-lab
     |   ├── etc.
     |   ├── instructions.md
     |   ├── README.md
     |   └── set-up.sh
     ├── new-java-lesson
     ├── new-java-lab
     └── etc.
```

Run the script with `bash set-up.sh` and follow the prompts.

## Details

For all content types, 

### Lessons and Labs



### Quizzes

A quiz repo consists of a `README.md` file and a `questions` folder.

The `README.md` file contains:

- some metadata about the quiz
- the quiz title
- the student-facing general instructions for the quiz

If you look at the README file in the `canvas-quiz` folder of this repo, you will see that the values for the metadata are not filled in. When the script runs, it 

The `README.md` file in this folder can be used as a template. Here's an example
of a completed `README.md` file:

```text
---
id: 20131
course_id: 3299
repo: phase-3-quiz-arrays-and-hashes
---

# Arrays and Hashes Quiz

It's time to check your knowledge! Use this quiz to create a custom study guide.
Note any answers that were marked incorrect, so you can study the relevant
material and try this quiz again.

If you don't know the answer to a question, please do not guess. Instead, select
"I don't know". It's OK not to know everything and to admit when we're unsure.
```

### Questions Folder

The `questions` folder contains one file per question. The naming convention for
the files is: `00.md`, `01.md`, etc.

### Questions Files

Each question file contains:

- metadata about the quiz question
- The content of the question itself, including:
  - The title of the question
  - The question text
  - Correct and incorrect responses. What these look like varies according to
    the question type.

See the question files in the `questions` folder for templates to set up
the different types of questions that can be used in Canvas:

- `00.md`: [short answer][] (called "Fill in the Blank" in Canvas)
- `01.md`: [multiple choice][]
- `02.md`: [multiple answers][] (i.e., select all that apply)
- `03.md`: [true/false][]
- `04.md`: [matching][]
- `05.md`: [multiple dropdowns][]
- `06.md`: [fill in multiple blanks][]

Each of the question types listed above links to an example in GitHub.

Here's an example of the completed metadata for a question file:

```text
---
course_id: 3297
quiz_id: 22405
id: 146234
type: short_answer_question
sources:
- name: What is an Algorithm?
  url: https://learning.flatironschool.com/courses/3297/pages/what-is-an-algorithm
---
```

### Required and Optional Metadata

README: all metadata is required for quizzes that already exist in Canvas. If the
`id` (which represents the quiz id) is omitted, the gem will create the quiz and
fill in the `id` returned by Canvas.

Question files:

- `id` (the question id) is required if the question already exists in Canvas.
  If it is omitted, the question will be created and its `id` will be
  automatically populated in the `##.md` file.
- `sources` is optional

[short answer]: https://learning.flatironschool.com/courses/3297/quizzes/22405/take?preview=1
[multiple choice]: https://learning.flatironschool.com/courses/3297/quizzes/22405/take/questions/146235?preview=true
[multiple answers]: https://learning.flatironschool.com/courses/3299/quizzes/20131/take/questions/130250?preview=true
[true/false]: https://learning.flatironschool.com/courses/3297/quizzes/31701/take/questions/210218?preview=true
[matching]: https://learning.flatironschool.com/courses/3264/quizzes/18300/take/questions/124109?preview=true
[multiple dropdowns]: https://learning.flatironschool.com/courses/3299/quizzes/19086/take/questions/120510?preview=true
[fill in multiple blanks]: https://learning.flatironschool.com/courses/3299/quizzes/19094/take/questions/149618?preview=true
