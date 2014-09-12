SonarQube on OpenShift
============================

This repository will help you install [SonarQube](http://www.sonarqube.org) in a self contained jvm using Openshift. It is designed to download the
zip distribution from a link. The sonar zip url is configurable within the app.conf file.

Create a DIY app on OpenShift
----------------------------

Create an account at http://openshift.redhat.com, don't forget to create a namespace and install client tools as well.

Create a DIY application

    rhc app create -t diy-0.1 -a sonar

Get SonarQube running
----------------------------
Use these quickstart commands to install SonarQube

    cd sonar
    git remote add sonar git://github.com/ajagnanan/openshift-sonar.git
    git rm -r diy .openshift misc README.md
    git pull -s recursive -X theirs sonar master

At this point, it is recommended to configure sonar to your needs. Check out these two files

    sonar.v4.properties
    wrapper.v4.conf

Once finished with configuration, push sonar up to Openshift with

    git push

That's it, you can now checkout your sonar at:

    http://sonar-$yournamespace.rhcloud.com

The default sonar user is admin/admin
A database migration might be needed. If a maintenance paged is is shown, go to this url for setup

    http://sonar-$yournamespace.rhcloud.com/setup