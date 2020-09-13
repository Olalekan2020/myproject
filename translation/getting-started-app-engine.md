# Course: Google Cloud Plaform Fundamental:  Core Infrastructure

#Lab: Getting started with app engine

#Objectives: 

    In this la, you are going to perform the following task:
 
    *Initialize App Engine.

    *Preview an App Engine application running locally in Cloud Shell.

    *Deploy an App Engine application, so that others can reach it.

    *Disable an App Engine application, when you no longer want it to be visible.

#Task 1: Initialize App Engine
    Step 1:
	
        -Initialize your App Engine app with your project and choose its region:
		
		    gcloud app create --project=$DEVSHELL_PROJECT_ID
		
	Step 2:
	
	    -Clone the source code repository for a sample application in the hello_world directory:
        
		    git clone https://github.com/GoogleCloudPlatform/python-docs-samples
		
    Step 3:
	    
		-Navigate to the source directory:
		
		    cd python-docs-samples/appengine/standard_python3/hello_world
			
#Task 2: Run Hello World application locally

    Step 1:

        -Execute the following command to download and update the packages list:	
        
            sudo apt-get update
			
    Step 2:
	
	    -Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system:
		
		    sudo apt-get install virtualenv
			
			virtualenv -p python3 venv
			
	Step 3:
	
	    -Activate the virtual environment:
	
	        source venv/bin/activate
			
	Step 4:		
			
		-Navigate to your project directory and install dependencies
		
		    pip install  -r requirements.txt
	
	Step 5:

        -Run the application:

            python main.py

		-To end the test, return to Cloud Shell and press Ctrl+C to abort the deployed service.	
		
#Task 3: Deploy and run Hello World on App Engine

    Step 1:
	
	    -Navigate to the source directory:
		
		    cd ~/python-docs-samples/appengine/standard_python3/hello_world
			 
	Step 2:
	 
	    -Deploy your Hello World application:
		 
		    gcloud app deploy
			
	Step 3:
	
	    -Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com:
		
		    gcloud app browse
		    