# Elastic File System

### Let's see how to create Elastic File System
1) Create one security group for EFS file system and add the inbound rule by enabling the NFS port 2049 and allow the port should allow our Instance Security Group.
2) Now go to the url https://us-east-2.console.aws.amazon.com/efs and create one EFS file system by attaching the EFS security group which we have been created
3) After creating the EFS file system create Access points in the same Dashboard by attaching our EFS File system.
4) Please visit the link for mounting documentation https://docs.aws.amazon.com/efs/latest/ug/mounting-fs.html
5) Now download amazon-efs-utils by using the link https://docs.aws.amazon.com/efs/latest/ug/installing-amazon-efs-utils.html#installing-efs-utils-amzn-linux
   ```sh
   $ sudo yum install -y amazon-efs-utils
   ```
6) Now get the EFS Mount access point from this link https://docs.aws.amazon.com/efs/latest/ug/mounting-access-points.html
   To automatically mount a file system using an access point, add the following line to the /etc/fstab file on the EC2 instance.
   ```sh
   file-system-id efs-mount-point efs _netdev,tls,accesspoint=access-point-id 0 0
   ```
   ```sh
   fs-0b07906bf05579be8 /var/www/html/images efs _netdev,tls,accesspoint=fsap-03cb08a0f7658429e 0 0
   ```
7) Now open /etc/fstab and add the below line
   fs-0b07906bf05579be8 /var/www/html/images efs _netdev,tls,accesspoint=fsap-03cb08a0f7658429e 0 0
   ```sh
   vi /etc/fstab
   ```
   fs-0b07906bf05579be8 /var/www/html/images efs _netdev,tls,accesspoint=fsap-03cb08a0f7658429e 0 0

8) Now create the backup and copy the images into that directory
   To mount the EFS file system to the path please execute the command 
   ```sh
   $ mount -fav
   ```
   Now the mounting has been done. We can check the mounting by using the disk usage command
   ```sh
   df -h
   ```
