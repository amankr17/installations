# cloudwatch agent installation commands

### attach iam role for ec2 having permissions: ssmaccess, CloudWatchAgentServerPolicy


*cloudwatch-agent install*

- centos: wget https://s3.amazonaws.com/amazoncloudwatch-agent/amazon_linux/amd64/latest/amazon-cloudwatch-agent.rpm
- ubuntu: wget https://s3.amazonaws.com/amazoncloudwatch-agent/ubuntu/amd64/latest/amazon-cloudwatch-agent.deb
- windows:cd /Downloads
- Invoke-WebRequest -Uri https://s3.amazonaws.com/amazoncloudwatch-agent/windows/amd64/latest/amazon-cloudwatch-agent.msi -outFile amazon-cloudwatch-agent.msi

*install*
- centos:sudo rpm -U ./amazon-cloudwatch-agent.rpm
- ubuntu:sudo dpkg -i -E ./amazon-cloudwatch-agent.deb
- windows: msiexec /i amazon-cloudwatch-agent.msi

*agent configuration*
- Linux: sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
- windows:cd "C:\Program Files\Amazon\AmazonCloudWatchAgent" .\amazon-cloudwatch-agent-config-wizard.exe

*starting of cloudwatch agent*
- Linux: sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json -s
- windows: & "C:\Program Files\Amazon\AmazonCloudWatchAgent\amazon-cloudwatch-agent-ctl.ps1" -a fetch-config -m ec2 -c file:configuration-file-path -s

*verify*
- linux: sudo systemctl status amazon-cloudwatch-agent
or sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -m ec2 -a status
- windows:& "C:\Program Files\Amazon\AmazonCloudWatchAgent\amazon-cloudwatch-agent-ctl.ps1" -m ec2 -a status

*Start service if required in linux*
- sudo systemctl start amazon-cloudwatch-agent

*Auto start after boot*
- sudo systemctl enable amazon-cloudwatch-agent

*you might have to install conllectd*
- sudo apt update
- sudo apt install collectd

*verify installation*
- collectd -h





