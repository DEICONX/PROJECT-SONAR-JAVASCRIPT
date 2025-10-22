# AWS-SERVER CONFIGURATION

> Give a name for instance and select image ubuntu

![](Screenshot%202025-10-21%20151155.png)

------

> Here while selecting instance type sonarqube needs minimum of 2 cpus and 4gb memory 

![](Screenshot%202025-10-21%20151221.png)

----

> Add inbound rule i.e default port number of sonarqube is 9000

![](Screenshot%202025-10-21%20151251.png)

-----

> SSH into terminal 
>
> sonarqube needs java so update and install java as shown in the image use
>
> `sudo apt -y update && sudo apt install openjdk-17-jre-headless -y`

![](Screenshot%202025-10-21%20152552.png)

------

> Update and install latest node js and npm version using
>
> `curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -`
>
> and now install nodejs using `sudo apt install -y nodejs` we will get the latest versions
>
> explanation:
>
> This specific URL (`https://deb.nodesource.com/setup_lts.x`) downloads a **setup script** from **NodeSource**, a trusted provider that distributes official Node.js binaries for Linux.
>
> The script automatically:
>
> - Detects your Ubuntu/Debian version.
> - Adds the **NodeSource APT repository** to `/etc/apt/sources.list.d/`.
> - Imports the GPG key to verify Node.js packages.
>
> ###  `| sudo -E bash -`
>
> - The **pipe (`|`)** sends the downloaded script directly to the **bash** shell.
> - **`sudo`** runs it with root privileges (required to modify apt sources).
> - **`-E`** preserves your environment variables (for safe sudo usage).
> - The trailing **`-`** tells bash to read from standard input (the script from curl).
> - It **runs the setup script immediately after downloading it**, instead of saving it to a file.

![](Screenshot%202025-10-21%20181429.png)

----

> Clone the code from git hub using `git clone <URL>`  

​     now install angular/cli using `sudo npm install -g @angular/cli`

![](Screenshot%202025-10-21%20181921.png)

-------

> Now change directory to code folder and there create a file "sonar-project.properties"
>
> using `sudo  nano sonar-project.properties` 

![](Screenshot%202025-10-22%20092942.png)

-------

> Now write the below file by giving your public ip and token key

    # Project identification
    sonar.projectKey=JavaScriptTest
    sonar.projectName=JavaScriptTest
    sonar.projectVersion=1.0

    # Source files location
    sonar.sources=.

    # Optional: Exclude files/folders if needed
    # sonar.exclusions=node_modules/**,dist/**,coverage/**

    # Language
    sonar.language=js

    # Encoding
    sonar.sourceEncoding=UTF-8

    # Server URL
    sonar.host.url=http://<YOUR_SONARQUBE_SERVER_IP>:9000

    # Authentication token
    sonar.login=<YOUR_GENERATED_TOKEN>

![](Screenshot%202025-10-22%20100500.png)

------

> Go to home ~ and download sonar-scanner using 
>
> `wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-5.0.1.3006-linux.zip`  
>
> A zip file is created and unzip it by installing unzip `sudo apt install unzip -y` and to unzip use
>
> `sudo unzip <name>` 

![](Screenshot%202025-10-22%20093625.png)

-------

> now we have to configure sonar-scanner.properties file and 
>
> `cd conf` 
>
> `sudo nano sonar-scanner.properties`

![](Screenshot%202025-10-22%20094104.png)

------

> In that add your url and token key 

    sonar.host.url=http://44.222.229.104:9000
    sonar.login=squ_f07f413acf99fff40f16d40e801a02bfa605dc9b

![](Screenshot%202025-10-22%20101527.png)

----

> Now go to your code folder and run
>
> `sonar-scanner`

![](Screenshot%202025-10-22%20094325.png)

------

> The execution is success and now go to sonarqube website which you have to run using your ip:portnumber
>
> Note: For sonarqube configuration refer to project-java-sonar git hub url is https://github.com/DEICONX/PROJECT-SONAR-JAVA.git

![](Screenshot%202025-10-22%20094807.png)

------

> Now in sonarqube dashboard our test analysis is ready in the below image you can see our code repo name Angularcalculator open the file

![](Screenshot%202025-10-22%20094831.png)

------

> Test is passed and successful and you can view detailed bugs in issues dashboard

![](Screenshot%202025-10-22%20095015.png)

-----

> Detailed issues are shown 

![](Screenshot%202025-10-22%20095026.png)
