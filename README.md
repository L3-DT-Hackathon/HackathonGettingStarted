# Hackathon: Getting Started

Would you like to learn how to hack on [GoCD](http://www.go.cd) by
[Thoughtworks](http://www.thoughtworks.com/products/go-continuous-delivery/resources)?

Are you a current GoCD user and you feel it is missing that one special
plugin?

If so, join us for our hackathon!

# Date/Location

The event is on Saturday, December 13, 2014 from 9:00 AM to
5:00 PM. We will have snacks, catered Chipotle and swag/prizes. The address:
 
L-3 Data Tactics  
7901 Jones Branch Dr  
Suite 700  
McLean, VA 22102  

To sign up:

[https://www.eventbrite.com/e/l-3-data-tactics-hackathon-tickets-14501573597](https://www.eventbrite.com/e/l-3-data-tactics-hackathon-tickets-14501573597)

## But It's Too Late For Me To Sign Up!

No worries! Call me and we'll make it happen! 571-766-8167

# Intro

* Bring a laptop
* Have a [Github account](http://github.com)
* Join [the L3-DT-Hackathon dev team](https://github.com/orgs/L3-DT-Hackathon/teams/devs)

## More

* Read the [code contribution
process](http://www.go.cd/contribute/contribution-guide.html#code-contribution-process)
* Read the [Go "geeknight" handout](geeknight_handout.doc)
* Read the [Go "geeknight" presentation](geeknight.pptx)

# How

## Plugin Ideas

Here is a list of optional plugin ideas to get you started. Remember
"optional": everything that has been set up is only there as a
convenience. **Nothing is set in stone!**

In no particular order, here are the ideas:

* XMPP/Jabber server integration
* Build status buttons (green "passing", red "failing", etc)
* Integration with github pull requests (thank you Mr Belden)
* Value stream un-blocker
* **your idea here :)**

## Team GoCD servers

We have set up GoCD servers that your team can use (optional, remember?)
The Vagrant definition for this server is hosted on our [Vagrant GoCD
repo fork and
branch](https://github.com/L3-DT-Hackathon/ansible-gocd/tree/hackathon).
Be aware that we have manually loaded in a customized `config.xml` which
includes a lot of hackathon-friendly pre-configuration. If you want to
try manually loading that file into your GoCD server, you can find it
[here](https://github.com/L3-DT-Hackathon/ansible-gocd/blob/hackathon/files/config.xml).

## Team Repositories

We have set up Github repositories and linked them to value streams in
your team's GoCD servers. Remember that word "optional"? That applies to
these repositories too!

As an example, team Gambit has the following Github repositories:

* https://github.com/L3-DT-Hackathon/Gambit-Apple
* https://github.com/L3-DT-Hackathon/Gambit-Banana
* https://github.com/L3-DT-Hackathon/Gambit-Loon
* https://github.com/L3-DT-Hackathon/Gambit-Mink
* https://github.com/L3-DT-Hackathon/Gambit-Newt
* https://github.com/L3-DT-Hackathon/Gambit-Yttrium
* https://github.com/L3-DT-Hackathon/Gambit-Zinc

# 24pullrequests

GoCD is one of the projects at
[24pullrequests](http://24pullrequests.com). So, if you or someone else
wants to become a part of the giving back during the hackathon, that's
cool too. Your name and commits get mentioned on their site.


# Installing a plugin
* Clone the gocd repo 
https://github.com/gocd/gocd  

* Get The Plugins Jar 
http://www.go.cd/documentation/user/current/resources/go-plugin-api-current.jar   
Run the following command in the directory that you saved the jar:
```
mvn install:install-file -Dfile=go-plugin-api-current.jar -DgroupId=com.thoughtworks.go -DartifactId=go-plugin-api 
```
-Dversion=14.4.0 -Dpackaging=jar

* Build the sample plugin
```
cd plugin-infra/sample-plugins/curl-plugin-old-api-based/ 
mvn clean install  
```

* SCP the plugin jar to the gocd box
scp -P 2222 /<path-to-.m2>/.m2/repository/com/thoughtworks/go/curl-plugin-old-api-based/1.0/curl-plugin-old-api-based-1.0.jar vagrant@<hostname>:.

* Move to the plugins directory
cp ~/curl-plugin-old-api-based-1.0.jar /var/lib/go-server/plugins/external

* Restart the server
service go-server restart

