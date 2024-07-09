# openmrs_lib
nedd jdk installed
To install Apache Tomcat 8.5.100 on Ubuntu, follow these steps:
Extract the Tomcat tarball:
bash
tar -xvf apache-tomcat-8.5.100.tar.gz

Move the extracted directory to the /opt directory:
bash
sudo mv apache-tomcat-8.5.100 /opt/

Create a symbolic link for easier management:
bash
sudo ln -s /opt/apache-tomcat-8.5.100 /opt/tomcat

Set the correct permissions:
bash
sudo chown -R root:root /opt/tomcat
sudo chmod -R 755 /opt/tomcat

Create a systemd service file:
bash
sudo nano /etc/systemd/system/tomcat.service

Add the following content:
[Unit]
Description=Apache Tomcat Web Application Container
After=network.target

[Service]
Type=forking

Environment=JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre
Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid
Environment=CATALINA_HOME=/opt/tomcat
Environment=CATALINA_BASE=/opt/tomcat
Environment='CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC'
Environment='JAVA_OPTS=-Djava.awt.headless=true -Djava.security.eg=file:/dev/./urandom'

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

User=root
Group=root

[Install]
WantedBy=multi-user.target

Reload systemd and start Tomcat:
bash
sudo systemctl daemon-reload
sudo systemctl start tomcat

Enable Tomcat to start automatically on system boot:
bash
sudo systemctl enable tomcat





///
Okay, let's install the required packages first before proceeding with MySQL installation.
Install the required packages:
bash
sudo apt install ./libaio1_0.3.113-4_amd64.deb ./libtinfo5_6.4-2_amd64.deb ./libncurses5_6.4-2_amd64.deb

This will install the libaio1, libtinfo5, and libncurses5 packages from the provided .deb files.
