# Cowrie SSH Honeypot Setup on AWS EC2
## 1. Launch EC2 Instance
- Type: t2.micro
- OS: Ubuntu Server 22.04
- Open **port 22** only in the security group
## 2. Install Dependencies
sudo apt update && sudo apt install git python3 python3-virtualenv libssl-dev
libffi-dev build-essential libpython3-dev -y ```

## 3. Clone Cowrie
git clone https://github.com/cowrie/cowrie.git
cd cowrie
cp cowrie.cfg.dist cowrie.cfg

4. Configure Cowrie
Change listen port to 22 in cowrie.cfg
Enable SSH

5. Start Cowrie
./bin/cowrie start

6. (Optional) Set up Systemd Autostart
sudo cp etc/systemd/cowrie.service /etc/systemd/system/
sudo systemctl daemon-reexec
sudo systemctl enable cowrie
sudo systemctl start cowrie
### `cloudwatch-logging.md`
markdown
# CloudWatch Agent Configuration for Cowrie
## 1. Install CloudWatch Agent
bash
sudo apt install amazon-cloudwatch-agent -y

7. Create Config File /opt/aws/amazon-cloudwatch-agent/etc/
config.json
{
"logs": {
"logs_collected": {
"files": {
"collect_list": [
{
"file_path": "/home/ubuntu/cowrie/var/log/cowrie.log",
"log_group_name": "cowrie-logs",
"log_stream_name": "cowrie-instance1"
}
]
}
}
}
}

8. Start Agent
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
-a start -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/etc/config.json -s
### `guardduty-setup.md`
markdown
# Enable GuardDuty on AWS
1. Navigate to the GuardDuty service in the AWS Console.
2. Click **Enable GuardDuty**.
3. Review and confirm region-wide monitoring.
4. GuardDuty will begin monitoring VPC flow logs, CloudTrail, and DNS activity.
5. Check alerts under **Findings**.

