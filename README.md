# aws-ec2-cli-cheatsheet

### Instance data info
```bash
# get token for curl calls to http://169.254.169.254
TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"`

# Get instance metadata (requires setting of $TOKEN, as above) endpoints
curl -v -H "X-aws-ec2-metadata-token: $TOKEN" http://169.254.169.254/latest/meta-data/
# Get specific piece of metadata, example of internal ipv4 address
curl -v -H "X-aws-ec2-metadata-token: $TOKEN" http://169.254.169.254/latest/meta-data/local-ipv4 

# Get instance user data (scripts run at instance startup)
curl -v -H "X-aws-ec2-metadata-token: $TOKEN" http://169.254.169.254/latest/user-data
