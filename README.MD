# ESEP Grade Calculator
- This library is a simple utility to calculate your grades.

## Runtime requirements:
- Golang 1.24+

## Project Structure
- `go.mod`: Is the root configuration file for the Grade-Calculator package and gives the minimum version requirement for the package.
- `grade_calculator.go`:  The grade calculator library that contains the different classes and methods that allow the library to function.
- `grade_calculator_test.go`: The test functions that will check the functionality and validity of the grade calculator library.

## Library Structure

#### `GradeCalculator`
Represent a makeup of all grade objects based on type of grade

* **Fields:**
  * `assignments` (`[]Grade`): List of assignment entries
  * `exams` (`[]Grade`): List of exam entries
  * `essays` (`[]Grade`): List of essay entries

#### `GradeType`
Represents the category of an evaluation item (`int`)

* **Constants:**
  * `Assignment` (`0`)
  * `Exam` (`1`)
  * `Essay` (`2`)

* **Methods:**
  * `(gt GradeType) String() string`  
    Returns the string representation (`"assignment"`, `"exam"`, or `"essay"`)

#### `Grade`
Represents individual grade entry

* **Fields:**
  * `Name` (`string`): Name or description of the assignment
  * `Grade` (`int`): Numerical grade
  * `Type` (`GradeType`): Category classification

### Public Class Functions

#### `NewGradeCalculator() *GradeCalculator`
Constructor function that initializes and returns a pointer to a new `GradeCalculator` instance.

#### `(*GradeCalculator) AddGrade(name string, grade int, gradeType GradeType)`
Appends a new grade entry to the corresponding slice based on `gradeType`.

#### `(*GradeCalculator) GetFinalGrade() string`
Calculates the total weighted score and returns the corresponding letter grade (`"A"`, `"B"`, `"C"`, `"D"`, or `"F"`).

### Internal Helper Functions

#### `(*GradeCalculator) calculateNumericalGrade() int`
Private method that calculates the weighted numerical score across categories

#### `computeAverage(grades []Grade) int`
Private helper that computes the arithmetic average score for a given slice of `Grade` structs.

Run unit tests:
```
cd grade_calculator/
go test ./...
```

Run unit tests with code coverage:
```
cd grade_calculator/
go test -coverprofile=coverage.txt ./...
```