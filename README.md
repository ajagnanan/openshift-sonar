Sonar on OpenShift
============================

This repository will help you install [Nexus](http://www.sonatype.org/nexus) on Apache Tomcat using Openshift. It is designed to download the
latest war from the sonatype website. The nexus war url is configurable within the app.conf file.

Create a DIY app on OpenShift
----------------------------

Create an account at http://openshift.redhat.com, don't forget to create a namespace and install client tools as well.

Create a DIY application

    rhc app create -t diy-0.1 -a sonar

Get Nexus running
----------------------------
Use these quickstart commands to install nexus

    cd sonar
    git remote add sonar git://github.com/ajagnanan/openshift-sonar.git
    git rm -r diy .openshift misc README.md
    git pull -s recursive -X theirs sonar master
    update sonar.v4.properties and wrapper.v4.conf with your configuration
    git push

That's it, you can now checkout your nexus at:

    http://nexus-$yournamespace.rhcloud.com/nexus

The default nexus user is admin/admin123