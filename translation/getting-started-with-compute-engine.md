# Course: Google cloud fundamental: Core Infrastruture

#Lab: Getting started with Compute Engine

#Objectives: 

    In this la, you are going to perform the following task:
 
    *In this lab, you will learn how to perform the following tasks:

    *Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

    *Create a Compute Engine virtual machine using the gcloud command-line interface.

    *Connect between the two instances.

	
#Task 1: Create two virtual machines
    Step 1:
	
        -Create the first vm:
 
           gcloud compute instances create "my-vm-1" \
		   --machine-type "n1-standard-1" \
		   --image-project "debian-cloud" \
		   --image "debian-9-stretch-v20200910" \
		   --subnet "default" --tags http --zone us-central1-a
		
	Step 2:
	
	    -Create a firewall rule to allow http traffic to the vm:
        
		   gcloud compute firewall-rules create allow-http --action=ALLOW --destination=INGRESS --rules=http:80 --target-tags=http 
		
    Step 3:
	
        -Create the second vm:
 
           gcloud compute instances create "my-vm-2" \
		   --machine-type "n1-standard-1" \
		   --image-project "debian-cloud" \
		   --image "debian-9-stretch-v20200910" \
		   --subnet "default" --tags http --zone us-central1-b
 
     Step 4:
	  
	    -Create a firewall rule to allow http traffic to the vm:
 
           gcloud compute firewall-rules create allow-http --action=ALLOW --destination=INGRESS --rules=http:80 --target-tags=http 

#Task 2: Connect between VM instances
        
	Step 1: Use the ping command to confirm that my-vm-2 can reach my-vm-1 over the network:
	  
	       -Connect to my-vm-2:
		       
			   gcloud compute ssh my-vm-2
			   
		   -Ping my-vm-1 from my-vm-2:
		   
		       ping -c 3 my-vm-1
			   
		   -Use ssh command to open a command prompt on my-vm-1 from my-vm-2:
		        
			   ssh my-vm-1
			   
		   -At the command prompt on my-vm-1, install the Nginx web server:
		   
		       sudo apt-get install nginx-light -y
			
		   -Use the nano text editor to add a custom message to the home page of the web server:
		   
		       sudo nano /var/www/html/index.nginx-debian.html
			   
		   -Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace YOUR_NAME with your name:
		    
			   Hi from Olalekan Olusanya
			   
		   -Exit editor and confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command:
			   
			   curl http://localhost/
			   
			    - Result:
				
				        The response will again be the HTML source of the web server's home page, including your line of custom text.
						
		   -To exit the command prompt on my-vm-1, execute this command:
		   
		        exit
				
		   *To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command:
		   
		        curl http://my-vm-1/
				
		        - Result:
				
				        The response will again be the HTML source of the web server's home page, including your line of custom text.
						
	Step 2: Now get the external ip address of the my-vm-1 instance from this command:
	   
             	gcloud compute instances list --zone us-central1-a
		
	Step 3: Copy the External IP address for my-vm-1 and paste it into the address bar of a new browser tab.
	   
	            - Result:
				
				        You will see your web server's home page, including your custom text.
