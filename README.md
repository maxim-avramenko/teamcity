TeamCity server in docker-compose
=================================

Clone repository:

        git clone https://github.com/maxim-avramenko/teamcity.git && cd teamcity

To init and start TeamCity server use command:

        ./teamcity --domain-name=teamcity.local \
                   --network=teamcity \
                   --db-name=teamcity \
                   --db-user=root \
                   --db-pass=TeamcitypassA1 \
                   --timezone=Europe/Moscow \
                   init \
                   start \
                   status

Don't forget to set StrongTeamCityDatabasePassword and teamcity.local domain name to your own password and domain name 

`Don't forget to add your domain.local to your system 'hosts' file.`

Example for linux (you must be in sudoers group):

        echo "127.0.0.1    teamcity.local" | sudo tee -a /etc/hosts

Open teamcity.local in your favorite browser to set up TeamCity application.

Example for google-chrome browser:

        google-chrome http://teamcity.local


Database credentials:
---------------------

        Database name: teamcity
        Database username: root
        Database password: TeamcitypassA1

All together in one string:
---------------------------

        git clone https://github.com/maxim-avramenko/teamcity.git \
        && cd teamcity \
        && echo "127.0.0.1    teamcity.local" | sudo tee -a /etc/hosts \
        && ./teamcity --domain-name=teamcity.local \
                      --network=teamcity \
                      --db-name=teamcity \
                      --db-user=root \
                      --db-pass=TeamcitypassA1 \
                      --timezone=Europe/Moscow \
                      init \
                      start \
                      status \
        && google-chrome http://teamcity.local


This command clone repo, init TeamCity with my teamcity.local domain name and DB password, adds teamcity.local to /etc/hosts and open it in my google-chrome