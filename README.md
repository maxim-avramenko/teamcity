TeamCity server in docker-compose
=================================

Clone repository and make teamcity bash script executable:

        git clone https://github.com/maxim-avramenko/teamcity.git \
        && cd teamcity \
        && chmod +x teamcity

Init and start TeamCity server with your own params, for example:

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

./teamcity --help
-----------------

        Usage: ./teamcity [OPTION]...
        
        Create or update .env file for TeamCity docker-compose.yml configuration.
        
        Mandatory arguments to long options are mandatory for short options too.
        
          --domain-name=teamcity.local      set up new domain-name for teamcity
                                            example: --domain-name=teamcity.local
                                            default: teamcity.local
        
          --network=teamcity                set up new network for teamcity services
                                            example: --network=teamcity
                                            default: teamcity
        
          --db-name=teamcity                set up new db name
                                            example: --db-name=teamcity
                                            default: teamcity
        
          --db-user=root                    set up new db user
                                            example: --db-user=root
                                            default: root
        
          --db-pass=TeamcitypassA1          set up new db password
                                            example: --db-pass=TeamcitypassA1
                                            default: TeamcitypassA1
        
          --timezone=Europe/Moscow          set up new timezone for db
                                            example: --timezone=Europe/Moscow
                                            default: Europe/Moscow
        
          -d, --debug                       run config in debug mode
        
          -h, --help                        display this help and exit
        
          -v, --verbose                     run config in verbose mode
        
        Example for init teamcity:
        
          ./teamcity --domain-name=teamcity.local \
                     --network=teamcity \
                     --db-name=teamcity \
                     --db-user=root \
                     --db-pass=TeamcitypassA1 \
                     -d \
                     -v \
                     init
        
