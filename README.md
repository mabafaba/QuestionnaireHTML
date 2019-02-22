# QuestionnaireHTML
## Download and load the QuestionnaireHTML library
* To download the library from Guithub:  

`remotes::install_github("hedibmustapha/QuestionnaireHTML",build_opts = c())`  
* To load the library:  
`library("QuestionnaireHTML")`

## Your inputs
Place your survey and choices csv files under the file `input`. Please note that if you are using multiple languages for your form, you need to move the column label of your desired output language before the others in your *survey file*.  
**Example 1** : If we want our output to be an *English*

| type  | name | label::English | label::Arabic |
| ---|---|---|---|
|   |   || |
|   |   || |
  
**Example 2** : If we want our output to be an *Arabic*  

| type  | name | label::Arabic | label::English |
| ---|---|---|---|
|   |   || |
|   |   || |

## Quick start
1. **Load your parameters with the function load_parameters()**  
`load_parameters(title,survey.file,choices.file,choices.label,survey.label,right.to.left,special.characters)`  
- `title` Name of your questionnaire as character.  
- `survey.file` Path to your questionnaire csv file as character.  
- `choices.file` Path to your choices csv file as character.  
- `choices.label` Choices label column to be used as character.  
- `survey.label` questionnaire label column to be used as character.
- `right.to.left` Type of the questionnaire writing system (TRUE/FALSE).
- `special.characters` If the text contains non latin characters, specify the language used.  
  
  
**Example 1**  
`list_parameters <- load_parameters("Area Based Assessment 2019", "questionnaire_file.csv", "choices_file.csv", "label::Arabic",label::Arabic", TRUE, "arabic")`  
  
  
**Example 2**  
`list_parameters <- load_parameters("JMMI January round", "questionnaire_file.csv", "choices_file.csv", "label","label", FALSE, "")`    

2. **Run the function xlsfrom_to_html()**  
`xlsfrom_to_html(x, dir, filename)`  
- `x` list of parameters (created with initialize_parameters)  
- `dir` the directory in which to save the output file (absolute path or relative to current working directory)  
- `filename` the name of the file. must end in ".html"  
  
**Example**:  
`xlsform_to_html(list_parameters, "./output", "questionnaire.html")`