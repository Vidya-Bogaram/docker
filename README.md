Docker

Step 1: Install docker compose

Using Homebrew: 

Users running macOS High Sierra, Sierra, El Capitan, or earlier, run:
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
Users running Catalina, Mojave, or Big Sur, run:
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

brew install docker-compose

Step 2: Install Docker UI
Step 3: Create docker-compose.yml file

mkdir ~/newFolderName
cd ~/newFolderName
vi docker-compose.yml

version: "3.9"

services: 
  jira: 
    container_name: JIRA
    image: atlassian/jira-software
    ports: 
      - "8080:8080"
  mule: 
    container_name: MULE
    image: "wslph/mule:4.4.0-ee"
    ports: 
      - "8001:8001"
      - "3000:3000"
  splunk: 
    container_name: SPLUNK
    environment: 
      - SPLUNK_START_ARGS=--accept-license
      - SPLUNK_PASSWORD=<password>
    image: splunk/splunk
    ports: 
      - "8000:8000"


Step 4: Run Commands

To run docker: docker-compose up -d
To shut down: docker-compose down

Links:
https://mac.install.guide/homebrew/3.html
https://hub.docker.com/


Possible Errors:

Issue: no matching manifest for linux/arm64/v8 in the manifest list entries
Cause: Using docker on Apple M1 chip
solution: https://devcoops.com/no-matching-manifest-for-linux-arm64-v8/ 


Issue: services.mule Additional property container-name is not allowed
Cause: hidden specials characters
solution:https://stackoverflow.com/questions/69801527/docker-compose-error-services-additional-property-is-not-allowed


