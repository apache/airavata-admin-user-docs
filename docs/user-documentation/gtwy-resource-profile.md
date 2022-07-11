## Gateway Resource Profile 

###### <h6 id="StoreR"><b><u>Register Storage Resource</u></b></h6>
NOTE: SciGaP admins will do this configuration for you in <a href="https://scigap.org/" target="_blank">SciGaP Portal</a>. <br>    
    
    
##### <h5 id="StorePreference">Gateway Resource Profile </h5>
1. NOTE: This is the section to configure the storage resource for the gateway. Storage resource is the place to hold all gateway user data: inputs and outputs from computations.<br>
2. Navigate to Settings &rarr; Gateway Resource Profile.
3. Select a SSH key from the list or generate  new one and assign it.
4. Click: New Storage Preference +.
5. Select Storage Resource: This is the storage resource for the user files and generally its the same server that holds the Django portal. If the gateway is deployed for you, this part would be taken cared by the SciGaP team. If the gateway is self-deployed select the host name of the server you deployed the gateway.
6. Login Username: pga (This is the username which uses to ssh to the storage resource)
7. File System Root Location: /var/www/portals/gateway-user-data/seagrid (The path which stores all user files, input files and output files)
8. Resource Specific Credential Store Token: Select a token from the list. (Public key of this token need to be added to authorized_keys in your storage resource 'pga' login)
9. Save.

