# Recon-ng
***

Recon-ng is an OSINT automation framework that streamlines open-source intelligence tasks. It leverages modules contributed by different authors. Certain modules necessitate access keys for functionality, enabling the module to interact with the relevant online APIs.

## Usage
### Workplace
```
# Creating Workspace
recon-ng
workspaces create test

# Start recon-ng wiht specific workspace
recon-ng -w test
```

### Database
```
# Seeding the database
# List the database tables
db schema

# Insert target domain test into domains table
recon-ng -w test
db insert domains
```

### Marketplace
```
# Search for available modules with keyword.
marketplace search KEYWORD 
# Provide information about the module in question.
marketplace info MODULE 
# Install the specified module into Recon-ng.
marketplace install MODULE
# Uninstall the specified module.
marketplace remove MODULE 
```

### Modules
```
# Get a list of all the installed modules
modules search
# Load a specific module to memory
modules load MODULE
# List the options that we can set for the loaded module.
options list
# Set the value of the option.
options set <option> <value>
# Run a module
run
# Unload a module
ctrl + c
```

### Keys
Certain modules are dependent on service-specific API keys for their operation. The "K" symbolizes the requirement of supplying the pertinent service key to enable the use of the particular module.
```
# Lists the keys
keys list
# Adds a key
keys add KE_NAME KEY_VALUE
# Removes a key
keys remove KEY_NAME
```
