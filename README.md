# NCTEC17-WDS

This is the repository for the NCTEC 17 Watson Discovery Service Hands On Session.

# Objectives

1. Set up a discovery instance
2. Have app/repository that allows for news exploration
3. Have app/repository that demonstrates relevancy training

# Agenda

0. Introduction ~ 5 minutes
1. Why use Watson Discovery Service? ~ 5 minutes
2. Review Github Repo ~ 5 minutes
3. Set up of Watson Discovery ~  5 minutes
4. Example 1 - Discovery news ~ 10 minutes - https://github.com/watson-developer-cloud/discovery-starter-kit
5. Example 2 - Knowledge Based Search ~ 15 minutes - https://github.com/watson-developer-cloud/discovery-starter-kit
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

https://knowledge-base-search.mybluemix.net/
- Demo of Knowledge Base search (5)

https://github.com/watson-developer-cloud/discovery-starter-kit
- Knowledge Base Search starter kit (5)

https://www.npmjs.com/package/watson-developer-cloud
- Node.js SDK

https://www.ibm.com/watson/developer-resources/
- Developer resources

# General steps to installing a new app

1. Clone the GitHub repo
2. Create your discovery service instance.
3. Connect your instance to your app.  
4. Test your app locally
5. Deploy your app to bluemix

# Example 1 - Discovery News

Install homebrew 
- /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Clone the GitHub repo

0. Copy zip file to location on your machine

Create your discovery service instance.

0. Create discovery service instance via tooling

Or…
1. Install Cloud foundry {for WDS environ set up and deployment} 
- brew install cloudfoundry/tap/cf-cli
2. Login to bluemix
- cf login -u rtbrown@us.ibm --sso 
3. Create discovery service and credentials using cloud foundry
- cf create-service discovery standard Discovery-Demo
- cf create-service-key Discovery-Demo myKey
- cf service-key Discovery-Demo myKey

Connect your instance to your app.  
0. Copy the example .env to .env and modify it with your discovery service credentials using editor

Test your app locally
1. Install X code {Mac, install from Apple app store}
2. Install Node.js 
- brew node install
3. Start server
[cd to root of local directory]
- npm install
- npm start

Deploy your app to bluemix (not covered)
0. Compile production app
1. Use cloud foundry to deploy app to bluemix

