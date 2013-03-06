# Chef Cookbook for AWS Developer Tools

## Description
Setup AWS Developer Tools for easier AWS server management. http://aws.amazon.com/developertools

API and AutoScaling Tools require java; by default, OpenJDK is installed. See the [java cookbook](https://github.com/opscode-cookbooks/java) for information on how to install Oracle's JDK.

## Requirements
* Ruby 1.9+
* Java
* Tested on Ubuntu 10.04

## Attributes
```ruby
default['aws_developer_tools']['install_java?'] = true  # set to `false` if you'd rather install java yourself
default['aws_developer_tools']['install_ruby?'] = true  # set to `false` if you'd rather install ruby yourself

default['aws_developer_tools']['aws_access_key'] = 'Your Access Key'  # you must set this if installing the API tools.
default['aws_developer_tools']['aws_secret_key'] = 'Your Secret Key'  # you must set this if installing the API tools.

## EC2 Tools ##
default['aws_developer_tools']['ec2_tools_target'] = '/usr/local/share/ec2_tools'

default['aws_developer_tools']['api']['source'] = 'http://s3.amazonaws.com/ec2-downloads/ec2-api-tools.zip'
default['aws_developer_tools']['api']['install_target'] = node['aws_developer_tools']['install_target']

default['aws_developer_tools']['ami']['source'] = 'http://s3.amazonaws.com/ec2-downloads/ec2-ami-tools.zip'
default['aws_developer_tools']['ami']['install_target'] = node['aws_developer_tools']['install_target']
###############

## AWS Tools ##
default['aws_developer_tools']['aws_tools_target'] = '/usr/local/share/aws_tools'

default['aws_developer_tools']['auto_scaling']['source'] = 'http://ec2-downloads.s3.amazonaws.com/AutoScaling-2011-01-01.zip'
default['aws_developer_tools']['auto_scaling']['install_target'] = "#{default['aws_developer_tools']['aws_tools_target']}/auto_scaling"

default['aws_developer_tools']['cloudwatch']['source'] = 'http://ec2-downloads.s3.amazonaws.com/CloudWatch-2010-08-01.zip'
default['aws_developer_tools']['cloudwatch']['install_target'] = "#{default['aws_developer_tools']['aws_tools_target']}/cloudwatch"
###############
```

See [Setting Attributes (Examples)](http://wiki.opscode.com/pages/viewpage.action?pageId=8257848).

## Recipes
* `aws_developer_tools` - sets up all of the below tools
* `aws_developer_tools::ami` - [AMI tools](http://aws.amazon.com/developertools/368). Requires Ruby
* `aws_developer_tools::api` - [API tools](http://aws.amazon.com/developertools/351). Requires Java
* `aws_developer_tools::auto_scaling` - [Auto Scaling tools](http://aws.amazon.com/developertools/2535). Requires Java
* `aws_developer_tools::cloudwatch` - [CloudWatch tools](http://aws.amazon.com/developertools/2534). Requires Java


Written by [Anuj Biyani](https://github.com/anujbiyani) for [Lytro](https://github.com/lytro)
