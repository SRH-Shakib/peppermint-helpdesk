<p align="center">
<img src="https://i.imgur.com/f4oEdvT.png"  height="10%" width="40%" alt="peppermint logo"/>
</p>

<h1>Host Your Own Helpdesk at Home Using Spare Hardware and Peppermint.sh</h1>
This guide will show you how to turn an old laptop or spare PC into a fully functional, self-hosted helpdesk system using Peppermint OS and Docker. You can set it up at home for your family and friends, so if they ever run into problems — with tech, chores, or anything else — they can easily submit a ticket. Whether it's for personal use, a small business, or just for fun, this lightweight and open-source solution puts you in control.<br />

<section>
  <section>
 <section>
  <h2>Environment and Technology Used</h2>
  <ul>
    <li><strong>Host System:</strong> Spare laptop or PC running any modern Linux distribution</li>
    <li><strong>Docker:</strong> Used to containerize the helpdesk software for easy deployment</li>
    <li><strong>Docker Compose:</strong> Manages multiple containers and services as a single unit</li>
    <li><strong>Peppermint Help Desk:</strong> A self-hosted helpdesk system using open-source ticketing software</li>
    <li><strong>Web Browser:</strong> Interface to access and manage the helpdesk</li>
    <li><strong>Local Network:</strong> Allows other household devices to connect to the helpdesk service</li>
  </ul>
</section>


  <h2>Prerequisites</h2>
  <p>Before you begin, make sure you have everything in place:</p>
  <ul>
    <li>🖥️ A spare laptop or PC with at least 2GB RAM (4GB recommended)</li>
    <li>🌐 Internet connection to download Docker and other dependencies</li>
    <li>🛠️ Basic familiarity with Linux terminal commands</li>
    <li>🐳 Docker and Docker Compose (I’ll walk you through installing them below)</li>
  </ul>
  <p>If you need help setting up a Linux system, feel free to use any popular Linux distro like Ubuntu, Fedora, or Debian.</p>
</section>

</section>

<section>
  <h2>Installing Docker and Docker Compose</h2>
  <p>We’ll now install Docker and Docker Compose so we can run the helpdesk system in containers.</p>

  <h3>Step 1: Update your system</h3>
  <pre><code>sudo apt update && sudo apt upgrade -y</code></pre>

  <h3>Step 2: Install Docker & Docker compose</h3>

 <pre><code>sudo apt install docker.io docker-compose -y </code></pre>
  
  <h3>Step 4: Verify Installation</h3>
  <pre><code>docker --version
docker-compose --version</code></pre>

  <p>If you see version numbers, Docker and Compose are ready to use.</p>
</section>

<p align="center">
<img src="https://i.imgur.com/ytHwqxV.png"  height="80%" width="80%" alt="peppermint logo"/>
</p>
<section>
 <section>
  <h2>Setting Up the Project Folder</h2>
  <p>Let’s now create a working directory for the Peppermint Help Desk and add the Docker configuration file.</p>

  <h3>Step 1: Create the Project Folder</h3>
  <pre><code>mkdir peppermint
cd peppermint</code></pre>

  <h3>Step 2: Create the <code>docker-compose.yml</code> File</h3>
  <p>Inside the <code>peppermint</code> folder, create a file named <code>docker-compose.yml</code>:</p>
  <p align="center">
<img src="https://i.imgur.com/OHYctl3.png"  height="80%" width="80%" alt="peppermint logo"/>
</p>
  <pre><code>nano docker-compose.yml</code></pre>

  <h3>Step 3: Paste the Configuration</h3>
  <p>Copy the contents of the file from the official GitHub repository:</p>
  <p><a href="https://github.com/Peppermint-Lab/peppermint/blob/main/docker-compose.yml">https://github.com/Peppermint-Lab/peppermint/blob/main/docker-compose.yml</a></p>

  <p>Paste the contents into the file, then save and exit (in nano: <code>Ctrl+O</code>, <code>Enter</code>, then <code>Ctrl+X</code>).</p>
</section>

<p align="center">
<img src="https://i.imgur.com/hfzvMT3.png"  height="80%" width="80%" alt="peppermint logo"/>
</p>

<section>
  <h2>Start the Peppermint Help Desk</h2>
  <p>With the <code>docker-compose.yml</code> file in place, you can now start the helpdesk application using Docker Compose.</p>

  <h3>Run the following command to start the containers:</h3>
  <pre><code>sudo docker-compose up -d</code></pre>

  <p>This command tells Docker Compose to start all the services defined in the file in the background (detached mode).</p>
  <p align="center">
<img src="https://i.imgur.com/HLOISgc.png"  height="80%" width="80%" alt="peppermint logo"/>
</p>

  <h3>Verify That It's Running</h3>
  <p>To check the status of the containers and find out which port the helpdesk is running on, use:</p>
  <pre><code>sudo docker ps</code></pre>

  <p>This will display a list of running containers. Look under the <strong>PORTS</strong> column to find the port number mapped to the helpdesk web interface (typically something like <code>0.0.0.0:3000-&gt;3000/tcp</code>).</p>
</section>

<p align="center">
<img src="https://i.imgur.com/0S3HhIt.png"  height="80%" width="80%" alt="peppermint logo"/>
</p>
<section>
  <h2>Accessing the Peppermint Help Desk</h2>
  <p>Once the containers are running, you can access the Peppermint Help Desk interface from any web browser on your local network.</p>

  <h3>Step 1: Find Your Computer’s Local IP Address</h3>
  <p>Run the following command to find your local IP address:</p>
  <pre><code>hostname -I</code></pre>
  <p>You'll see something like <code>192.168.1.42</code> — that's the address you’ll use to access the helpdesk.</p>

  <h3>Step 2: Open the Help Desk in a Browser</h3>
  <p>Open your browser and visit the address below, replacing the IP and port if different:</p>
  <pre><code>http://192.168.1.42:3000</code></pre>

  <p>If everything is working correctly, you should see the Peppermint Help Desk login or setup screen.</p>

  <h3>Troubleshooting Tips</h3>
  <ul>
    <li>Make sure your firewall is not blocking the port</li>
    <li>Ensure Docker is still running: <code>sudo docker ps</code></li>
    <li>Check logs with <code>sudo docker-compose logs</code> if the page doesn't load</li>
  </ul>
</section>
<p align="center">
<img src="https://i.imgur.com/MCS02PY.png"  height="80%" width="80%" alt="peppermint logo"/>
</p>
<section>
  <h2>Welcome to Peppermint Help Desk</h2>
  <p>After accessing the Peppermint Help Desk interface in your browser, you'll see the login screen where you can enter the credentials to get started.</p>

  <h3>Step 1: Login Screen</h3>
  <p>The login page will prompt you to enter an email address and a password.</p>
  
  <p>By default, the login credentials are:</p>
  <ul>
    <li><strong>Email:</strong> admin@admin.com</li>
    <li><strong>Password:</strong> 1234</li>
  </ul>
  
  <p>Enter these credentials, and you’ll be logged into the Peppermint Help Desk dashboard, where you can start managing tickets and settings!</p>

  <p>Once logged in, you will have access to the full range of help desk features, including ticket management, user settings, and more.</p>
</section>

<p align="center">
<img src="https://i.imgur.com/f4oEdvT.png"  height="10%" width="40%" alt="peppermint logo"/>
</p> 
 <h3>Step 2: Dashboard</h3>
  <p>Once logged in, you will have access to the full range of help desk features, including ticket management, user settings, and more.</p>
  <p>You will see a dashboard that looks similar to the one shown below:</p>
  
  <!-- Image of the Dashboard -->
  
<p align="center">
<img src="https://i.imgur.com/qOCHcLQ.png"  height="10%" width="40%" alt="peppermint logo"/>
</p> 
  <h3>Step 3: Creating a Ticket</h3>
  <p>To create a new ticket, click on the "Create Ticket" button. Here’s what the creation process looks like:</p>

  <!-- Image of Ticket Creation -->
  
<p align="center">
<img src="https://i.imgur.com/4Dx2Z3S.png"  height="10%" width="40%" alt="peppermint logo"/>
</p> 
  <h3>Step 4: Viewing the Ticket</h3>
  <p>Once the ticket is created, you will be able to view it in the dashboard. Here’s what it looks like once it's created:</p>

  <!-- Image of Ticket View -->
<p align="center">
<img src="https://i.imgur.com/pvz9zgf.png"  height="10%" width="40%" alt="peppermint logo"/>
</p> 
</section>
<section>
  <h2>Managing Users and Tickets in Peppermint Help Desk</h2>
  <p>As an admin, you can create as many users as you want, either as admins or general users. The following steps will guide you through creating users, logging in as a different user, and managing tickets.</p>

  <h3>Step 1: Creating a User</h3>
  <p>As an admin, you can create new users and assign them roles (admin or general user). Below is an example showing how to create a user:</p>

  <!-- Image of User Creation -->
 <p align="center">
<img src="https://i.imgur.com/RNH0KRP.png"  height="10%" width="40%" alt="peppermint logo"/>
</p> 
<p align="center">
<img src="https://i.imgur.com/CfsPR0H.png"  height="10%" width="40%" alt="peppermint logo"/>
</p> 

  <h3>Step 2: Logging in as a Different User</h3>
  <p>If you want to log in as a different user, simply enter their credentials on the login screen. Here’s an example showing how to log in as a different user:</p>

  <!-- Image of Login as Different User -->
<p align="center">
<img src="https://i.imgur.com/pHAoE53.png"  height="10%" width="40%" alt="peppermint logo"/>
</p> 
  <h3>Step 3: Reading and Closing a Ticket</h3>
  <p>Once you’ve logged in, you can read and manage tickets. Below is an example showing how to view a ticket and close it once it has been resolved:</p>

  <!-- Image of Reading and Closing a Ticket -->
 <p align="center">
<img src="https://i.imgur.com/ORBGs0t.png"  height="10%" width="40%" alt="peppermint logo"/>
</p> 
</section>
<section>
  <h2>Conclusion</h2>
  <p>Congratulations! You've successfully deployed the <strong>Peppermint Help Desk</strong> — a powerful, self-hosted support system tailored for homes, small teams, or local networks. You’ve set up Docker, configured your environment, launched the application, and even explored how to manage users and support tickets.</p>

  <p>By leveraging open-source technologies and containerization, you've built a scalable, flexible, and fully private help desk system — all running right from your own machine.</p>

  <h3>What's Next?</h3>
  <ul>
    <li>🛡️ <strong>Secure Your Instance</strong> – Change the default admin credentials and consider using HTTPS (via a reverse proxy like Nginx + Let's Encrypt).</li>
    <li>👥 <strong>Invite More Users</strong> – Add team members or family members to participate in the help desk workflow.</li>
    <li>⚙️ <strong>Customize It</strong> – Explore the settings panel to change the branding, ticket categories, and notification preferences.</li>
    <li>📦 <strong>Back It Up</strong> – Set up regular backups of your Docker volumes or use tools like <code>docker cp</code> and <code>rsync</code> to back up data.</li>
    <li>📘 <strong>Build a knowledge base</strong> to help users help themselves.</li>
 
  </ul>

  <p>Your Peppermint Help Desk is now ready to streamline support and communication — whether it's for IT tasks at home, organizing household help requests, or managing client interactions in a small business.</p>


</section>

  
  
  </ul>


</section>
