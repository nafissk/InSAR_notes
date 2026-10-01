# Data Access Accounts

To enable the download of SAR data, metadata and other necessary products (e.g. orbit information, digital elevation models) several accounts required for automated downloading.

**One MUST do this before using notebooks from this repository** You will not be able to process any data without these accounts.

There are three essential accounts that you will need: 

1. A NASA EarthData account, for downloading data from NASA and NASA-supported facilities, such as ASF
2. An OpenTopography account, for downloading digital elevation data
3. Account setup for ERA5

These accounts are free and easy to set up. Be sure to **read the sections below and edit the code cells carefully** to ensure success.
## 1. NASA EarthData accounts
Getting data from any NASA Distributed Active Archive Center (DAAC) requires a free NASA EarthData account. We will be using data from both the Alaska Satellite Facility (ASF) DAAC and the Land Processes (LP) DAAC, so you need to register for an EarthData account to complete many parts of the course. In addition, you need to accept some license agreements to have access to Sentinel-1, ALOS, and GRFN data that is all stored at the ASF DAAC. The SRTM and NASADEM topography data do not require license agreements.

The NASA EarthData login information page is here:
https://www.earthdata.nasa.gov/eosdis/science-system-description/eosdis-components/earthdata-login

### EarthData registration
The NASA site to register (or login after registering) for an EarthData account is the EarthData User Registration Service:
https://urs.earthdata.nasa.gov/home

You will be taken to the `urs.earthdata.nasa.gov` site to login any time you try to download data from a NASA DAAC with a browser.

### ASF EarthData login

The ASF DAAC has a helpful video on YouTube about registering for an EarthData login (using a popup window that is connected to the same [NASA EarthData URS site](https://urs.earthdata.nasa.gov/home)) and using the login in the the ASF Vertex data search system. [ASF Vertex Login Video](https://www.youtube.com/watch?v=j_Db_ipKLos)

### Writing your EarthData account information to a `.netrc` file
A number of ISCE2 programs, some of the ARIA-tools programs, and other programs use a special hidden file called `.netrc` in the home directory of your account on the computer where you run them, including the OpenSARLab machines, to get a saved version of your EarthData username and password. This allows them to download data without you having to enter the EarthData login every time.

You can create the `.netrc` file by running the command below in a terminal window substituting *your* username (instead of 'myUsername') and *your* password (instead of 'myPassword'):

```bash
echo "machine urs.earthdata.nasa.gov login myUsername password myPassword" > $HOME/.netrc
```


Or you can substitute your EarthData account login name into `myUsername` and your EarthData password into `myPassword` in the next cell below, which will run the same command from the notebook.

Because the `.netrc` file has your personal password, you should change the file protections so that nobody can view it. Some programs will check the file permissions and refuse to run until you make the file not readable by anybody else.

We use the standard Linux or Unix file permission command `chmod` to change the file permissions. The permissions `600` means readable by you and nobody else. Again, you can do this in a terminal window or use the notebook cell below.

```bash
chmod 600 $HOME/.netrc
```
## 2. OpenTopography accounts

[OpenTopography](https://opentopography.org/) is a site that facilitates community access to high-resolution, Earth science-oriented, topography data, and related tools and resources, sponsored by the USA National Science Foundation (NSF). Several notebooks in this course, and related software such as ARIA-tools, use OpenTopography to get topographic data through the OpenTopography Applications Programming Interface (API) that provides network access to their dataset. 

### OpenTopography registration
Since January 2022, OpenTopography requires (free) registration for an OpenTopography account to download their data. You can register on the OpenTopography web portal: [https://portal.opentopography.org/login](https://portal.opentopography.org/login)

### OpenTopography API keys
After you register for the OpenTopography account, you need to get the API key for your account that is basically the equivalent of your username and password encoded into a long string of hexadecimal digits. When you are logged in to the OpenTopography Portal, you can get the API for your account [here](https://portal.opentopography.org/lidarAuthorizationInfo?s=api). 

It should show you your key like this:
```
API key:     7698c9963edee3
```
(I have removed half of my key to keep it private, so you will see a much longer string of hexadecimal digits.)

### Writing your OpenTopography API key to a `.topoapi` file 
Similar to the EarthData login storage, some of the programs in ARIA-tools expect that you have stored your OpenTopography API key in a special hidden file called `.topoapi` in your home directory. You should get your API key from the OpenTopography portal and use that to replace the `myAPIkey` in the following command that can be run in the terminal or this notebook.
```bash
echo "myAPIkey" > $HOME/.topoapi
```
Again, similar to the `.netrc` file this file should be protected so others can't read your key with the `chmod` command.
```bash
chmod 600 $HOME/.topoapi
```
## 3. ERA 5 Account

```bash
echo -e "url: https://cds-beta.climate.copernicus.eu/api\nkey: MyKEY" > $HOME/.cdsapirc
```

```bash
chmod 600 $HOME/.cdsapirc
```
