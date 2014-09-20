---
title: How to Start or Stop a AWS ec2 instance in php
layout: post
---
### 1). Installation of AWS-php sdk

* Download the latest aws php sdk with all the dependencies in a 
zip from here
[https://github.com/aws/aws-sdk-php/releases](https://github.com/aws/aws-sdk-php/releases)

* Require sdk's autoloader in php file.

There is a autoload file that's capable of autoloading all of the classes in any of the libraries of aws. To use it, just add the following line to your code's bootstrap process.

`require '/path/to/aws-autoloader.php';`

### 2).  Starting an Ec2 Instance
 {% highlight php %}
    <?php
    require '/path/to/aws-autoloader.php';

    use Aws\Ec2\Ec2Client;


    //Initiating 
    $client = Ec2Client::factory(array(
        'key'    => 'YOUR_AWS_ACCESS_KEY_ID',
        'secret' => 'YOUR_AWS_SECRET_ACCESS_KEY',
        // OR: 'profile' => 'my_profile',
        'region' => 'YOUR_EC2_INSTANCE_REGION'
    ));

    //Starting
    $result = $client->startInstances(array(
        // InstanceId is required
        'InstanceIds' => array('YOUR_INSTANCE_ID')        
    ));
    ?>
 {% endhighlight %}

### 3). Stopping an Ec2 Instance  
 {% highlight php %}

    <?php
    require '/path/to/aws-autoloader.php';

    use Aws\Ec2\Ec2Client;


    //Initiating 
    $client = Ec2Client::factory(array(
        'key'    => 'YOUR_AWS_ACCESS_KEY_ID',
        'secret' => 'YOUR_AWS_SECRET_ACCESS_KEY',
        // OR: 'profile' => 'my_profile',
        'region' => 'YOUR_EC2_INSTANCE_REGION'
    ));

    //Stopping
    $result = $client->stopInstances(array(
        // InstanceIds is required
        'InstanceIds' => array('YOUR_INSTANCE_ID')        
    ));
    ?>
 {% endhighlight %}