MaizeSNPDB
========

The genotypes of 1210 maize lines at 35,370,939 SNP sites are stored using Sparse Matrices in R.  

*****

#	Use MaizeSNPDB online

MaizeSNPDB is deployed at <a href="https://venyao.xyz/MaizeSNPDB/" target="_blank">https://venyao.xyz/MaizeSNPDB/</a> for online use.  
MaizeSNPDB is idle until you activate it by accessing the URL. So it may take some time when you access this URL for the first time. Once it was activated, MaizeSNPDB could be used smoothly and easily.  

*****

#	Launch MaizeSNPDB directly from R and GitHub

User can choose to run MaizeSNPDB installed locally for a more preferable experience.

**Step 1: Install R and RStudio**

Before running the app you will need to have R and RStudio installed (tested with R 3.4.4 and RStudio 1.1.442).  
Please check CRAN (<a href="https://cran.r-project.org/" target="_blank">https://cran.r-project.org/</a>) for the installation of R.  
Please check <a href="https://www.rstudio.com/" target="_blank">https://www.rstudio.com/</a> for the installation of RStudio.  

**Step 2: Install the R Shiny package and other packages required by MaizeSNPDB**

Start an R session using RStudio and run these lines:  
```
# try an http CRAN mirror if https CRAN mirror doesn't work  
install.packages("shiny")  
install.packages("shinyBS")  
install.packages("shinythemes")  
install.packages("shinycssloaders")  
install.packages("plotly")  
install.packages("foreach")  
install.packages("ape")  
install.packages("pegas")  
install.packages("plyr")  
install.packages("dplyr")  
install.packages("tidyr")  
install.packages("gridExtra")  
install.packages("genetics")  
install.packages("BiocManager")    
BiocManager::install("IRanges")
BiocManager::install("snpStats")
BiocManager::install("chopsticks")  
BiocManager::install("ggtree")  
# try an http CRAN mirror if https CRAN mirror doesn't work  
install.packages("LDheatmap")
# install shinysky  
install.packages("devtools")  
devtools::install_github("venyao/ShinySky", force=TRUE)  
```

**Step 3: Start the app**  

Start an R session using RStudio and run these lines:  
```
library(shiny)  
runGitHub("MaizeSNPDB", "venyao", launch.browser = TRUE)  
```
This command will download the code of MaizeSNPDB from GitHub to a temporary directory of your computer and then launch the MaizeSNPDB app in the web browser. Once the web browser was closed, the downloaded code of MaizeSNPDB would be deleted from your computer. Next time when you run this command in RStudio, it will download the source code of MaizeSNPDB from GitHub to a temporary directory again. This process is frustrating since it takes some time to download the code of MaizeSNPDB from GitHub.  

Users are suggested to download the source code of MaizeSNPDB from Jianguoyun (https://www.jianguoyun.com/p/Dby8fCUQzqnhBRiv64UB) or GitHub (https://github.com/venyao/MaizeSNPDB) to a fixed directory of your computer, such as 'E:\apps' on Windows. Following the procedure illustrated in the following figure, a zip file named 'MaizeSNPDB-master.zip' (GitHub) or 'MaizeSNPDB.zip' (Jianguoyun) would be downloaded to the disk of your computer. Move this file to 'E:\apps' and unzip this file. Then a directory named 'MaizeSNPDB-master' or 'MaizeSNPDB' would be generated in 'E:\apps'. The scripts 'server.R' and 'ui.R' could be found in 'E:\apps\MaizeSNPDB-master' or 'E:\apps\MaizeSNPDB'.  
<br>
<img src="MaizeSNPDB.png" width="890"/>  
<br>

Then start an R session using RStudio and run these lines:  
```
library(shiny)  
runApp("E:/apps/MaizeSNPDB-master", launch.browser = TRUE)  # from GitHub
runApp("E:/apps/MaizeSNPDB", launch.browser = TRUE)   # from Jianguoyun
# The first parameter of runApp should be the directory that contains the scripts server.R and ui.R of MaizeSNPDB.  
```

Your web browser will open the app.

*****

#	Deploy MaizeSNPDB on local or web Linux server

**Step 1: Install R**  

Please check CRAN (<a href="https://cran.r-project.org/" target="_blank">https://cran.r-project.org/</a>) for the installation of R.

**Step 2: Install the R Shiny package and other packages required by MaizeSNPDB**  

Start an R session and run these lines in R:  
```
# try an http CRAN mirror if https CRAN mirror doesn't work  
install.packages("shiny")  
install.packages("shinyBS")  
install.packages("shinythemes")  
install.packages("shinycssloaders")  
install.packages("plotly")  
install.packages("foreach")  
install.packages("ape")  
install.packages("pegas")  
install.packages("plyr")  
install.packages("dplyr")  
install.packages("tidyr")  
install.packages("gridExtra")  
install.packages("genetics")  
install.packages("BiocManager")    
BiocManager::install("IRanges")
BiocManager::install("snpStats")
BiocManager::install("chopsticks")  
BiocManager::install("ggtree")  
# try an http CRAN mirror if https CRAN mirror doesn't work  
install.packages("LDheatmap")
# install shinysky  
install.packages("devtools")  
devtools::install_github("venyao/ShinySky", force=TRUE)  
```

For more information, please check the following pages:  
<a href="https://cran.r-project.org/web/packages/shiny/index.html" target="_blank">https://cran.r-project.org/web/packages/shiny/index.html</a>  
<a href="https://github.com/rstudio/shiny" target="_blank">https://github.com/rstudio/shiny</a>  
<a href="https://shiny.rstudio.com/" target="_blank">https://shiny.rstudio.com/</a>  

**Step 3: Install Shiny-Server**

Please check the following pages for the installation of shiny-server.  
<a href="https://www.rstudio.com/products/shiny/download-server/" target="_blank">https://www.rstudio.com/products/shiny/download-server/</a>  
<a href="https://github.com/rstudio/shiny-server/wiki/Building-Shiny-Server-from-Source" target="_blank">https://github.com/rstudio/shiny-server/wiki/Building-Shiny-Server-from-Source</a>  

**Step 4: Upload files of MaizeSNPDB**

Put the directory containing the code and data of MaizeSNPDB to /srv/shiny-server.  

**Step 5: Configure shiny server (/etc/shiny-server/shiny-server.conf)**

```
# Define the user to spawn R Shiny processes
run_as shiny;

# Define a top-level server which will listen on a port
server {  
  # Use port 3838  
  listen 3838;  
  # Define the location available at the base URL  
  location /maizesnp {  
    # Directory containing the code and data of MaizeSNPDB  
    app_dir /srv/shiny-server/MaizeSNPDB;  
    # Directory to store the log files  
    log_dir /var/log/shiny-server;  
  }  
}  
```

**Step 6: Change the owner of the MaizeSNPDB directory**

```
$ chown -R shiny /srv/shiny-server/MaizeSNPDB  
```

**Step 7: Start Shiny-Server**

```
$ start shiny-server  
```

Now, the MaizeSNPDB app is available at http://IPAddressOfTheServer:3838/MaizeSNPDB/.  


