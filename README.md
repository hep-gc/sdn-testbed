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


[1]:https://github.com/hep-gc/sdn-testbed/tree/master/conf
    




