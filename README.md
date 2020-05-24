# BCAI_Min
This is a version of BCAI which only has the minimum files required to run the program and compiled binaries rather than source code to run. This version will be distributed for use.

## How to install
Do not clone the repo, just download/copy [installMinimal.bash](installMinimal.bash). Then run installMinimal.bash using:

    sudo bash installMinimal.bash

This will install all required softwares and this repository as well as the onionshare repository.

For a full list of things installed, see the comment block at the top of [installMinimal.bash](installMinimal.bash)

Also, place one or more keystore files for the account(s) you want to use in ML/localUser and ML/localWorker

## How to run provider
Providers execute ML tasks for users and are paid for their work in ether cryptocurrency.

In the main directory run ```bash startWorker.bash``` this will open two terminal tabs:

1) The CLI where you interact with the application to start providing or check things such as your rating and balance.

2) The python script for file upload and transfer. All you have to do here is input your password for sudo.

	Though no further interaction is needed, this terminal will display information on your file upload and transfer.

In the CLI you can either continue using the CLI to use the program or open the web page.

Once you start providing, no interaction is needed to continue completing tasks.

## How to create image.zip

Create a python3 script subject to the following restrictions:

* The script must be written in python3
* The script must be named execute.py
* The script must allow for a single integer command line argument:
	* If the input is 0 then the program should train the model
	* If the input is 1 then the program should evaluate the model
* Any packages must be written in the [requirements.txt](ML/createImage/Dockerfile/requirements.txt) file
	* Note this must use the pip3 file based install format
	* For example, if your script uses tensorflow, you must add a line in [requirements.txt](ML/createImage/Dockerfile/requirements.txt) that says tensorflow
	
For an example of a script that follows these conditions, see [our example script](ML/createImage/example.py)

Once you've created the script named execute.py, place it in [ML/createImage/Dockerfile](ML/createImage/Dockerfile)

Once the script is in place, back up to [ML/createImage](ML/createImage) and run

    sudo python3 genImage.py
    
This will create a task file named image.zip. Place this image inside [ML/localUser](ML/localUser) before beginning.
	
## How to run user
Users upload ML tasks to be performed by providers and pay them in ether cryptocurrency.

In ML/localUser place your docker task file named image.zip. To see how to create this task file, see the previous section.

In the main directory run ```bash startUser.bash``` this will open two terminal tabs:

1) The CLI where you interact with the application to submit your task, choose providers and validators, and finalize your request.

2) The python script for file upload and transfer. All you have to do here is input your password for sudo.

	Though no further interaction is needed, this terminal will display information on your file upload and transfer.

In the CLI you can either continue using the CLI to use the program or open the web page.

The following steps must take place for your task to be completed:

1) Submit your task with filename

2) Wait for your file to finish hosting

3) Choose a provider who will then download the task

4) Once the provider executes the task, choose a validator to validate

5) Once validation is complete you will automatically start downloading your result file

6) After receiving your result,  finalize your request, giving a rating to your provider based on the correctness and quality of the result.

## Other info
Please do not close any of the terminals or the web page until you have finished/stopped your request or providing.

If you have any issues please contact with a copy of log.txt and describe the issue.
