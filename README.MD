# ESEP Grade Calculator

A small Go library that computes a student's final letter grade from three kinds of graded work: assignments, exams, and essays. It averages each category, combines the averages using category weights, and maps the result to a letter grade.

## Project layout

```
.
-- README.MD
  -- grade-calculator/
    -- go.mod                    # Go module definition (module esep/grade-calculator, Go 1.24)
    -- grade_calculator.go       # Library code: GradeCalculator, Grade, GradeType
    -- grade_calculator_test.go  # Unit tests (Go's built-in testing package)
```

## Usage

- NewGradeCalculator(passFail bool) creates an empty calculator. Pass true to get Pass/Fail results instead of letter grades.
- AddGrade(name string, grade int, gradeType GradeType) records a grade. gradeType is Assignment, Exam, or Essay.
- GetFinalGrade() returns the final grade.

## Grading rules

The final score is a weighted average of each category's average:

Categories:
Assignments - 50%
Exams - 35%
Essays - 15%

Letters:
A - >= 90
B - >= 80
C - >= 70
D - >= 60
F - < 60

In Pass/Fail mode, a C or better (>= 70) is Pass; anything lower is Fail. A category with no grades averages to 0.

## Running the tests

All commands are run from the grade-calculator directory.

Run the unit tests:
```
cd grade-calculator/
go test ./...
```

Shows each test by name:
```
go test -v ./...
```

Run a single test:
```
go test -run TestGetGradeA ./...
```

## Code coverage

Print the coverage percentage:
```
go test -cover ./...
```

The HTML report highlights covered lines in green and uncovered lines in red.
