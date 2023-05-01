# Composite action: python script execution

This GitHub composite action executes a given python script. The script is executed in a virtual environment with the given python version. Dependencies may be installed from a `requirements.txt` file and (if needed) a `constraints.txt` file. A list may be as well provided instead of a file (typically in a workflow yaml file). The virtual environment is cached between runs.

## Choices
* The script output is defined as action output in case the user might want to use it for whatever reason in its workflow.
* There is some piece of bash to deal with the possibilities of giving a file path or directly a list of dependencies.
   * The `constraints` are always put into another temporary file to be used as a parameter for `pip install`.
   * If the `requirements` are given as a list, each package will be installed with the `constraints` given as an argument.