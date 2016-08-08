# PIAScript

Small Python script which enables port forwarding for a PIA VPN and prints the forwarded port.

Now finished but not perfect, personal project, etc.

I do not use this for illegal downloading. I don't condone that, don't do that, etc.

Usage
- -h, --help: Show help.
- -debug, --debug: Show debugging print statements
- credentialsfile: Mandatory argument, file that contains PIA API credentials (see below).

Credentials File:
- See: https://www.privateinternetaccess.com/forum/discussion/180/port-forwarding-without-the-application-advanced-users to create a client id and for API documentation.
- Expected file format:
- 
    Line 1: [PIA username]

    Line 2: [PIA password]
    
    Line 3: [PIA client id]
    
Dependancies
- Python 3
- The Python 3 netifaces library (look for a package for your distribution or use Python's easy_install).

This script will:
- Check if the VPN is connected (tun0 interface is active).
- Read PIA API credentials from a file (path provided as a command line parameter).
- Post to the PIA API endpoint in order to forward a port.
- Parse the response and print it (port number or error message)

Notes and issues:
- This is my first Python program, made in my spare time.
- This script will not work for other VPN providers as is.
- Exception handling with file I/O could be better but I had issues with "with using" and "try/catch/finally".
- The PIA API sometimes returns a port that is closed if you have been reconnecting a lot. Try waiting a few minutes and trying again.
- I removed ufw firewall and transmission functionality to simplify the script's purpose and because I don't use them anymore.
- This script should be portable now that I changed the network querying to use the netifaces library and removed the use of GNU/Linux command line tools.

Downloading and Usage

1. Download the entire repository as .zip

2. Make sure piascript.py is executable

3. Create your API credentials file (see above)

4. Execute the script and provide the path to the file

Other steps:
- You will have to update the INTERFACE variable if your VPN is using an interface other than tun0 (OpenVPN and the official PIA appplication (OpenVPN backend) both use tun0 by default).

