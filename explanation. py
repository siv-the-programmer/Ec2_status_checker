# EC2 State checker 
# FULL EXPLANATION 



# Import the AWS SDK for Python

# This library allows Python to talk to AWS services

import boto3





# Create an EC2 client object

# This does NOT start or stop anything

# It simply prepares a connection to the EC2 API

ec2 = boto3.client("ec2")





# Call the EC2 API to get information about all EC2 instances

# AWS returns a large dictionary containing nested data

response = ec2.describe_instances()





# AWS groups EC2 instances into "Reservations"

# response["Reservations"] is a LIST

# We loop through each reservation one by one

for reservation in response["Reservations"]:



    # Inside each reservation is a list of EC2 instances

    # reservation["Instances"] is also a LIST

    for instance in reservation["Instances"]:



        # Each instance is a DICTIONARY

        # "InstanceId" is a key inside that dictionary

        # We store it in a variable for reuse

        instance_id = instance["InstanceId"]



        # "State" is another dictionary inside the instance

        # "Name" inside "State" holds the actual status string

        # Example values: running, stopped, terminated

        state = instance["State"]["Name"]



        # Conditional check:

        # If the instance state is exactly "running"

        if state == "running":



            # Print the instance ID and a message

            # Running instances cost money

            print(instance_id, "is RUNNING (costing money)")



        # If the instance is NOT running

        else:



            # Print the instance ID and its current state

            print(instance_id, "is", state)

