Sure, here are the instructions to install Docker on Linux Mint.

Before proceeding with Docker installation, make sure to update your existing list of packages:

bash
Copy code
sudo apt-get update
Next, install a few prerequisite packages which let apt use packages over HTTPS:

bash
Copy code
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
Then add the GPG key for the official Docker repository to your system:

bash
Copy code
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
Add the Docker repository to APT sources:

bash
Copy code
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
Update the package database with the Docker packages from the newly added repo:

bash
Copy code
sudo apt-get update
Finally, install Docker:

bash
Copy code
sudo apt-get install docker-ce
Now Docker should be installed, the daemon started, and the process enabled to start on boot. Check that it's running:

bash
Copy code
sudo systemctl status docker
This will display a lot of output, including the lines:

bash
Copy code
● docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2021-11-23 11:00:00 UTC; 1min 20s ago
     Docs: https://docs.docker.com
If it doesn't say active (running), use this command to start it:

bash
Copy code
sudo systemctl start docker
And to enable it to start at boot:

bash
Copy code
sudo systemctl enable docker
Once Docker is installed, it's recommended to add your user to the Docker group so you can execute Docker commands without needing to use sudo:

bash
Copy code
sudo usermod -aG docker ${USER}
After running the above command, log out and log back in so that your group membership is refreshed.

You can verify that Docker has been correctly installed and that you've been added to the Docker group by running:

bash
Copy code
docker run hello-world
This command will download a test image and run it in a container. When the container runs, it prints an informational message and exits. If you can see the welcome message, you're now ready to start exploring Docker!