# NCTEC17-WDS

This is the repository for the NCTEC 17 Watson Discovery Service Hands On Session.

# Objectives

1. Set up a discovery instance
2. Have Node.js app/repository that allows for news exploration
3. Demo a Node.js app/repository that illustrates a variety of visualizations and queries

# Agenda

0. Introduction ~ 5 minutes
1. Why use Watson Discovery Service? ~ 5 minutes
2. Review Github Repo ~ 5 minutes
3. Set up of Watson Discovery ~  5 minutes
4. Example 1 - Discovery news ~ 10 minutes - https://github.com/watson-developer-cloud/discovery-starter-kit
5. Example 2 - Voice of the Customer ~ 15 minutes - https://github.ibm.com/psmoraes/voc-discovery
6. Q&A / wrap up ~ 10 minutes

# Resources

https://www.ibm.com/watson/services/discovery/
- Discovery main page (1)

https://console.bluemix.net/docs/services/watson/index.html#about 
- Getting Started with Watson and IBM Cloud (3)

https://discovery-news-demo.mybluemix.net/?cm_mc_uid=75223102214015096352970&cm_mc_sid_50200000=1510067331&cm_mc_sid_52640000=1510067331
- Demo of News Intelligence starter kit (4)

https://www.ibm.com/watson/developercloud/starter-kits.html#news-intelligence
- News Intelligence starter kit (4)

https://github.ibm.com/psmoraes/voc-discovery
- Voice of the Customer starter kit (5)

https://www.npmjs.com/package/watson-developer-cloud
- Node.js SDK

https://www.ibm.com/watson/developer-resources/
- Developer resources

# General steps to installing a new app

1. Clone the GitHub repo
2. Create your discovery service instance.
3. Connect your instance to your app.  
4. Test your app locally
5. Deploy your app to bluemix (not covered)

# Example 1 - Discovery News

Install homebrew 
- /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Clone the GitHub repo

0. Copy zip file to location on your machine
- https://github.com/watson-developer-cloud/discovery-starter-kit

Create your discovery service instance.

0. Create discovery service instance via tooling

Or…
1. Install Cloud foundry {for WDS environ set up and deployment} 
- brew install cloudfoundry/tap/cf-cli
2. Login to bluemix
- cf login -u {email} --sso
{supply the one time key to log in}
3. Create discovery service and credentials using cloud foundry
- cf create-service discovery standard Discovery-Demo
- cf create-service-key Discovery-Demo myKey
- cf service-key Discovery-Demo myKey

Connect your instance to your app.  
0. Copy the example .env to .env and modify it with your discovery service credentials using editor
{consider adding .env to get ignore if cloning to Github}

Test your app locally
1. Install X code {Mac, install from Apple app store}
2. Install Node.js 
- brew node install
3. Start server locally 
{cd to root of local directory}
- npm install
- npm start
4. Review app on port 3000

Deploy your app to bluemix (not covered)

0. Compile production app
1. Use cloud foundry to deploy app to bluemix

https://console.bluemix.net/docs/services/watson/getting-started-cf.html#cloud-foundry-command-line-interface

# Example 2 - Voice of the customer (app works best in Google Chrome)

Clone the GitHub repo

0. Copy zip file to location on your machine
- https://github.ibm.com/psmoraes/voc-discovery

Create your discovery service instance.

0. Create discovery service collection via tooling
1. Create the collection voc_config
2. Upload the configuration from the NC TEC repository.

Note: The configuration provided in the repo needs to be updated to use Natural Language Understanding.

To upload the existing configuration from the collection:
Retrieve the username and password credentials from the service details page.
Retrieve the environment id and collection id from the URL by running an empty query. Look for the hash after the environments/ to retrieve the environment id.

https://gateway.watsonplatform.net/discovery/api/v1/environments/358028e7-2263-4511-9be4-34f76bdf78ed/collections/eced038e-fc2e-464c-90c3-1dd2c52105df/query?version=2017-10-16&count=&offset=&aggregation=&filter=&passages=true&deduplicate=false&highlight=true&return=&query=

Information needed:
username
password
environment id
discovery_config2.json from the NC TEC repository (not VOC)


Open a terminal, cd to the root folder for VOC and use the curl command with the above information to upload the new configuration from the downloaded repository. Information in {} denotes variables.

    curl -X POST \
    -u "{username}":"{password}" \
    -H "Content-Type: application/json" \
    -d @discovery_config2.json "https://gateway.watsonplatform.net/discovery/api/v1/environments/{environment_id}/configurations?version=2017-10-16"

Once you have uploaded the configuration you may need to reload your browser to see the new configuration.

Apply the configuration to the collection. Add the remaining enrichments to review_text.

Note: In order to see data in visualizations for the tooling switch to the 
convert tab. Select copy add the field review_text in the first box, add text to the second box.

Once the configuration has been applied properly you can ingest your data using the tooling.

Note: In order to see data in visualizations for the tooling switch to the 
convert tab. Select copy add the field review_text in the first box, add text to the second box.

Connect your instance to your app.

To connect the node.js app to your instance you will need a .env file.

0. Copy the .env.example file to .env

Supply the following information:
username
password
environment id
collection id

Test your app locally

In the root directory of voc-disovery

npm install
npm start

Review the app in your web browser

Deploy your app to bluemix (not covered)

See the above instructions for the previous demo
