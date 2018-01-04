#!/bin/bash
#Update the package manager
#Yum in this case as it is ran on Amazon Linux
sudo yum update -y

#Install R
sudo yum install -y R

#Install RStudio-Server
#https://www.rstudio.com/products/rstudio/download-server/
wget https://download2.rstudio.org/rstudio-server-rhel-1.1.383-x86_64.rpm
sudo yum install -y --nogpgcheck rstudio-server-rhel-1.1.383-x86_64.rpm
sudo rm rstudio-server-rhel-1.1.383-x86_64.rpm

#Install shiny and shiny-server
sudo R -e "install.packages('shiny', repos='http://cran.rstudio.com/')"
wget https://download3.rstudio.org/centos5.9/x86_64/shiny-server-1.5.5.872-rh5-x86_64.rpm
sudo yum install -y --nogpgcheck shiny-server-1.5.5.872-rh5-x86_64.rpm
sudo rm shiny-server-1.5.5.872-rh5-x86_64.rpm

#add user(s)
sudo useradd username
echo username:password | sudo chpasswd

