import boto3

# Initialize a session using AWS credentials
ec2 = boto3.client('ec2', region_name='us-east-1')  # Change region if needed

# Launch an EC2 instance
response = ec2.run_instances(
    ImageId='ami-0c02fb55956c7d316',  # Example AMI ID (Amazon Linux 2)
    InstanceType='t2.micro',          # Instance type (free tier eligible)
    KeyName='your-key-pair-name',     # Replace with your key pair name
    MinCount=1,
    MaxCount=1,
    SecurityGroupIds=['sg-0abc1234def567890'],  # Replace with your security group ID
    SubnetId='subnet-0abc1234def567890',       # Replace with your subnet ID
    TagSpecifications=[
        {
            'ResourceType': 'instance',
            'Tags': [{'Key': 'Name', 'Value': 'MyEC2Instance'}]
        }
    ]
)

# Print instance details
for instance in response['Instances']:
    print(f"Instance ID: {instance['InstanceId']}")
    print(f"State: {instance['State']['Name']}")
    print(f"Private IP: {instance['PrivateIpAddress']}")
