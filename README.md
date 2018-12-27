TeamCity server in docker-compose
=================================

Clone repository:

        git clone https://github.com/maxim-avramenko/teamcity.git && cd teamcity

To init and start TeamCity server use command:

        ./init <database password> <TeamCity server domain name>

        ./init StrongTeamCityDatabasePassword teamcity.local

Don't forget to change StrongTeamCityDatabasePassword and teamcity.local to your own domain name and password and add domain to your system 'hosts' file

Example for linux (you must be in sudoers group):

        echo "127.0.0.1    teamcity.local" | sudo tee -a /etc/hosts

Open teamcity.local in your favorite browser to set up TeamCity application.
Example for google-chrome browser:

        google-chrome http://teamcity.local


Database credentials:
---------------------

        Database name: teamcity
        Database username: root
        Database password: <StrongTeamCityDatabasePassword>

All together in one string:
---------------------------

        git clone https://github.com/maxim-avramenko/teamcity.git \
        && cd teamcity \
        && echo "127.0.0.1    teamcity.local" | sudo tee -a /etc/hosts \
        && ./init StrongTeamCityDatabasePassword teamcity.local \
        && docker ps --format "table {{.Names}}\t{{.Status}}" \
        && google-chrome http://teamcity.local


This command clone repo, init TeamCity with my teamcity.local domain name and DB password, adds teamcity.local to /etc/hosts and open it in my google-chrome
