SDN Testbed Files
=================

The files in this git repo can used to configure your EX4550 to work with the SDN Testbed.


Setting up users
---------------

Users can be granted access using ssh keys. To load the set of keys from the cli do the following.

    file copy http://sdnfiles.hepnetcanada.ca/sdn-testbed/conf/sdn-user-replace .
    edit
    load replace sdn-user-replace
    commit check
    commit
    

Switching controllers
----------------------

You can switch between the available configure controllers by loading any of the 
[controller replace files][1] by doing the following. For example:

    file copy http://sdnfiles.hepnetcanada.ca/sdn-testbed/conf/floodlight-controller-replace .
    edit 
    load floodlight-controller-replace
    commit check
    commit

The above example depends on the OF switch being called SDNTestbed


Automating Controller Config
----------

You can configure the switch to pull the controller config automatically from
the web whenever a change is made to [default-controller-replace][2]. In order to do this 
you establish a conjob on the switch that will and update and commit the configuration when
the config stored in github is changed. 

    start shell
    mkdir sdn-pull
    cd sdn-pull
    curl http://sdnfiles.hepnetcanada.ca/sdn-testbed/scripts/checknewcontroller.sh -o checknewcontroller.sh

now edit the contab entry to run this script every 5 minutes

    crontab -e 
    ### insert the line:
    */5 * * * * (cd /var/home/username/sdn-pull; sh checknewcontroller.sh)

make sure to replace `username`   


[1]:https://github.com/hep-gc/sdn-testbed/tree/master/conf
[2]:https://github.com/hep-gc/sdn-testbed/blob/master/conf/default-controller-replace

    




