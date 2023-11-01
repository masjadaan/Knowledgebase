## WPScan
***

The WPScan framework boasts the ability to comprehensively identify and investigate various security vulnerabilities that may be lurking within WordPress websites. 
WPScan relies on a local database as its primary source of information when searching for themes and plugins during enumeration. It is strongly advised to keep this database up to date prior to conducting any scans.

## Installation
```
sudo apt install wpscan
wpscan --update
```

## Usage
```
# Enumerate for installed themes
wpscan --url http://IP --enumerate t

# numerate for installed plugins (located in /wp-content/plugins/pluginname)
wpscan --url http://IP --enumerate p
	
# Increase the aggressivness 
wpscan --url http://IP --enumerate p --plugins-detection aggressive
	
# Enumerate users
wpscan --url http://IP --enumerate u
	
# Check for vulnerability in plugin use vp
wpscan --url http://IP --enumerate vp
# Note:  **that this requires setting up WPScan to use the WPVulnDB API**
	
# Brute force on the 'admin' username
wpscan --url www.example.com --passwords rockyou.txt --usernames admin
```

	
