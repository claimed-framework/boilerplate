# CLAIMED Boilerplate
A boilerplate project to get started with your own operators, workflows and CI/CD pipelines

If you like CLAIMED, just give us a [star](https://github.com/claimed-framework/component-library) on our [main project](https://github.com/claimed-framework/component-library).

## Installation
Ideally [fork](https://github.com/claimed-framework/boilerplate/fork) this repository to get started with your own code immediately. Otherwise, just [clone](https://github.com/claimed-framework/boilerplate.git) it. 

## Setup
CLAIMED runs best in a python virtual environment. So once you've cloned or forked the project and opened it in your favourite IDE, please create a virtual environment by running the following commands in the root directory of your forked/cloned project:

`python -m venv .venv`

`source ./.venv/bin/activate`

`pip install claimed cwltool`

CLAIMED also relies on DOCKER (we are working on a containerless target runtime for the C3 compiler, but for now you need it). So please install DOCKER according the instructions for your operating system.

This (and love) is all you need.

## Create your first operator

To make life simple, we've provided boilerplate operator code. Change into the `operators` directory:

`cd operators`

Then execute the following command:

`c3_create_operator --test_mode -r anything example_operator.py`

As long as you are in `--test_mode`, you can set the repositiry to a dummy value with `-r anything` as the resulting image is not pushed to the container registry.

## Test your first operator in local mode using CWL (Common Workflow Language)

You will see some artifacts created. YAML files (e.g., kubeflow pipeline component, kubernetes job definition) and a example_operator.cwl. You can now execute this task using:

`cwltool example_operator.cwl --num_values 23`

You should see some output like this:

`
2023-11-23 21:06:21,102 - root - INFO - Random values: [0.46335395 0.16080613 0.29429919 0.82020681 0.72263968 0.13268649
 0.14216825 0.97550455 0.23171864 0.82288426 0.82183549 0.46068025
 0.46725788 0.56821123 0.62938518 0.7982786  0.52429601 0.13117852
 0.66231392 0.48726925 0.69951924 0.13506377 0.35280975]
`

## Congratulations, let's turn this into a locally executable workflow.

Change to the `workflows` folder:

`cd ../workflows`

There you've find a file called example_workflow.cwl, consiting of two steps, both calling the operator you've just created.

Start this workflow with:

`cwltool example_workflow.cwl`

If everything is correct, you should see the same output from before, but twice.

Congratulations. Now it is up to you to add additional operators, call them in the workflow and add other workflows to this project.

This concludes this boilerplate. If you have questions or problems, please create an [issue](https://github.com/claimed-framework/boilerplate/issues). You can also find more [examples](https://github.com/claimed-framework/c3/tree/main/examples).