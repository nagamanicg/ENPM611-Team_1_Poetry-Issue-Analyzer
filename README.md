# ENPM611 Project Application Template
This project involves developing an application that analyzes GitHub issues from the Poetry open-source project to generate meaningful insights. The application retrieves data from a JSON file (poetry_issues.json) and performs detailed analyses to identify trends, highlight key contributors, and categorize issue types—providing a comprehensive view of the project’s ongoing activity and user engagement.

The application includes several core modules:

`data_loader.py` – A utility that loads issues from the provided data file and returns them in a structured runtime format (e.g., as Python objects).

`model.py` – Defines the data model into which the JSON file is loaded, allowing convenient access to issue attributes through object fields.

`config.py` – Handles configuration parameters for the application using the config.json file. Additional configuration options can be added as needed.

`run.py` – The main entry point for running the application. Based on the --feature command-line argument, it executes one of the implemented analyses. This module can be extended to integrate additional analytical features.

An example analysis is provided in `example_analysis.py`, which demonstrates how to use the utility modules and how to generate analytical outputs.

## Setup

To get started, your team should create a fork of this repository. Then, every team member should clone your repository to their local computer. 


### Install dependencies

In the root directory of the application, create a virtual environment, activate that environment, and install the dependencies like so:

```
pip install -r requirements.txt
```

### Download and configure the data file

Download the data file (in `json` format) from the project assignment in Canvas and update the `config.json` with the path to the file. Note, you can also specify an environment variable by the same name as the config setting (`ENPM611_PROJECT_DATA_PATH`) to avoid committing your personal path to the repository.


### Run an analysis

With everything set up, you should be able to run the existing example analysis:

```
python run.py --feature 0
```

That will output basic information about the issues to the command line.

## Feature 4 - Resolution Time Analyser

This feature analyzes how specific GitHub issue events such as labeling and assignment influence the overall resolution time of issues.
The goal is to identify patterns that reveal which early actions help close issues faster and which may introduce delays.

Insights:
1. A negative trendline slope indicates that earlier labeling or assignment correlates with faster resolution.
2. If the slope is flat or positive, it suggests that these events may not strongly influence closure speed.
3. This analysis helps maintainers prioritize when to apply labels or assign owners to improve triage efficiency.
### Run feature 4
```
python run.py --feature 4
```

#### Sample outputs:
### Figure 1 – Impact of Labeling Time on Issue 
![Impact of Labeling Time](images/feature4/AssigmentTimevsResolutiontime.png)

Each point represents an issue. The x-axis shows how many days after creation it was labeled, and the y-axis shows how long the issue took to resolve.
A negative slope in the trendline indicates that issues labeled earlier tend to close faster, suggesting that early triage improves efficiency.

### Figure 2 – Impact of Labeling Time on Issue 
![Impact of Labeling Time](images/feature4/labellingTimevsResolutiontime.png)

This plot compares the time to first assignment with total resolution time.
A visible downward trend suggests that assigning an issue to a developer sooner often correlates with shorter resolution durations, emphasizing the importance of prompt ownership.


## VSCode run configuration

To make the application easier to debug, runtime configurations are provided to run each of the analyses you are implementing. When you click on the run button in the left-hand side toolbar, you can select to run one of the three analyses or run the file you are currently viewing. That makes debugging a little easier. This run configuration is specified in the `.vscode/launch.json` if you want to modify it.

The `.vscode/settings.json` also customizes the VSCode user interface sligthly to make navigation and debugging easier. But that is a matter of preference and can be turned off by removing the appropriate settings.
