#Course: Essential Google Cloud Infrastructure: Foundation 

##Lab: Console and Cloud Shell 

#Objectives: 

    In this la, you are going to perform the following task:
 
    *Get access to Google Cloud.

    *Create a Cloud Storage bucket using the Cloud Console.

    *Create a Cloud Storage bucket using Cloud Shell.

    *Become familiar with Cloud Shell features.


#Task 1: Create two buckets using Cloud Shell
    Step 1:
	
        -Use the gsutil command to create first bucket.  Replace <BUCKET_NAME> with a globally unique name:
		
		    gsutil mb gs://mybucket-ad583dcd
		
	Step 2:
	
        -Use the gsutil command to create another bucket.  Replace <BUCKET_NAME> with a globally unique name:
		
		    gsutil mb gs://secondbucket-ad583dcd
		
    			
#Task 2: Explore more Cloud Shell features

    Step 1:

        -type ls to confirm that file media.txt was uploaded:	
        
            ls
			
			   -Result:
			       media.txt

    Step 2:
	
	    -Copy the file into one of the buckets you created earlier in the lab. Replace [MY_FILE] with the file you uploaded and [BUCKET_NAME] with one of your bucket names:
	
			gsutil cp media.txt gs://mybucket-ad583dcd
			
#Task 3: Create a persistent state in Cloud Shell	

    Step 1:

        -To list available regions, execute the following command:

            gcloud compute regions list		

	Step 2:
	
	    -Select a region from the list and note the value in any text editor. Type 14 to select us-central1:
		
		    14
	
	#Create and verify an environment variable
	
	Step 1:
	
	    -Create an environment variable and replace [YOUR_REGION] with the region you selected in the previous step:
		
		    INFRACLASS_REGION=us-central1
			 
	Step 2:
	
	    -Verify it with echo:
		
		    echo $INFRACLASS_REGION
	 
	#Append the environment variable to a file
	
	Step 1:
	
	    -Create a subdirectory for materials used in this class:
		
		    mkdir infraclass
			 
	Step 2:
	   
	    -Create a file called config in the infraclass directory:
		
		    touch infraclass/config
			
	Step 3:
	
	    -Append the value of your Region environment variable to the config file:
		
		    echo INFRACLASS_REGION=$INFRACLASS_REGION >> ~/infraclass/config
			
	Step 4:
	
		-Create a second environment variable for your Project ID, replacing [YOUR_PROJECT_ID] with your Project ID.
		
		    INFRACLASS_PROJECT_ID=qwiklabs-gcp-00-ad583dcd4b0f
			
	Step 5:
	
		-Append the value of your Project ID environment variable to the config file:
		
		    echo INFRACLASS_PROJECT_ID=$INFRACLASS_PROJECT_ID >> ~/infraclass/config
			
	Step 6:
	
	    -Use the source command to set the environment variables, and use the echo command to verify that the project variable was set:
		
		    source infraclass/config
            
			echo $INFRACLASS_PROJECT_ID
			
	Step 7:
	
	    -Close and re-open Cloud Shell. Then issue the echo command again:
		
		    echo $INFRACLASS_PROJECT_ID
			
	#Modify the bash profile and create persistence
	
	Step 1:
	
	    -Edit the shell profile with the following command:
		
		    nano .profile
			
	Step 2:
	
	    -Add the following line to the end of the file:
		
		    source infraclass/config
			
	Step 3:Press Ctrl+O, ENTER to save the file, and then press Ctrl+X to exit nano.
	
	Step 4:
	
	    -Use the echo command to verify that the variable is still set:
		
		    echo $INFRACLASS_PROJECT_ID
	
	            -Result:
				      You should now see the expected value that you set in the config file.
