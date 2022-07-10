## Application Catalog

- _Application Catalog_ is where you will add your gateway applications/tools/codes for gateway users to consume.
- Application/tool/code is what you create in the gateway, which will have all the configurations required to execute the actual code in the  remote resource.
- Configuring an _Application_ is a three step process. You would;
 - First add the main _Details_ of the application
 - Next its the _Interface_, where you would add all the input required to execute application and also the outputs that the gateay should bring back for the user.
 - Last is the _Deployment_, Which is the place you will add all the commands that are needed to execute the application in the remote resource.

- Gateway admins can;
    - Create new applications
    - Test the application with job submissions
    - Edit existing applications
    - Delete applications no longer needed
    
NOTE: In order to explain how an application could be added to the gateway, we would take Gaussian16 application as the example. 

#####<h5 id="Gaussianapplication">Register Gaussian16 Application</h5>

1. Settings &rarr; Application Catalog &rarr; New Application +
2. In Details tab:
    - Application Name: Gaussian16
    - Application Version: Gaussian 16 (Optional)
    - Application Description: Gaussian provides capabilities for electronic structure modeling
    - Save

<ADD>------
![Screenshot](../img/gau-app-detail-tab.png)
Image:Adding Gaussian16 Details

3. In Interface tab:
    - Set 'Enable Archiving Working Directory' to True (Why? - This is set to true when you want to bring back all the files in the remote working directory back to the gateway portal. Caution: Gateway has a size restriction on ARCHIVE. Please contact SciGaP admins for more details.)
    - Set 'Hide Queue Details' - This is your gateway preference. If you gateway users are not give the option of changing the queue properties when submitting jobs, you can hide this and have same properties set for all the users.
    - Provide Input Fields
        - Click Add Application Input
        - Name: Input-File
        - Initial Value: gaussian.com
        - Type: URI (Why? - This is the type for file uploads)
        - Application Arguments:
        - Read Only: False (Why? - this is only meaningful for String, Integer or Float inputs)
        - User Friendly Description: Gaussian16 input file specifying desired calculation type, model chemistry, molecular system and other parameters. (This is information to the user at creating job experiment. Optional)
        - Is the Input Required: True
        - Required in Commandline: True
        - Metadata:  (Why? - This is used mostly for advance string input options. Please <br>For more information refer: <a href="/user-documentation/advance-inputs" target="_blank">Advance Application Inputs</a>)
<br></br>
NOTE: For this application, only a single input, and its a file. For applications, there can be multiple inputs and different input types, such as String, Integer or many files.
    - Provide application outputs</br>
    NOTE: 4 application outputs to define. </br>
        - 1st Output
            - Add Application Output
            - Name: Gaussian-Application-Output
            - Value: *.log
            - Type: URI
            - Application Argument:
            - Is the Output required?: True
            - Required on command line?: True
            - Metadata: 
        - 2nd output
            - Add Application Output
            - Name: Gaussian_Checkpoint_File
            - Value: *.chk
            - Type: URI
            - Application Argument:
            - Data Movement: False
            - Is the Output required?: True
            - Required on command line?: True
            - Metadata:
        - For applications, STDOUT and STDERR will be automatically added for you.
![Screenshot](../img/gau-app-inputoutput1.png)
![Screenshot](../img/gau-app-inputoutput2.png)
Image: Gaussian16 Inputs and Outputs
</br></br>
4. In Deployment tab
    - New Deployment +'
        - Select Expanse
        - You can add SSH key which you would want to use to SSH to Expanse
        - Share: Add groups and users you want to have access to this deployment. Meaning, who can submit Gaussian16 jobs to Expanse
        - Application Executable Path: /home/gridchem/bin/rung09_with_chk_recovery.sh
        - Application Parallelism Type: SERIAL </br>
        - Application Deployment Description: Gaussian16 Rev A.03
        - Module Load Commands: 
            - <pre><code>#SBATCH -N 1</code></pre>
            - export MODULEPATH=/share/apps/compute/modulefiles/applications:$MODULEPATH; module load gaussian/16.B.01
        - Pre Job Commands:
            - export AIRAVATA_USERNAME=$gatewayUserName
            - export AIRAVATA_INPUTS=$inputs
            - export AIRAVATA_ExptDataDir=$experimentDataDir;
        - Default Queue Name: shared
        - Default Node Count: 1
        - Default CPU Count: 4
        - Default Walltime: 30
        - Save

![Screenshot](../img/gau-app-dep1.png)
Image: Gaussian16 Deployment

#####<h5 id="Otherappdetails">Other Application Catalog Details </h5>
1. An Application can have multiple deployment, each deployment is for each remote resource the gateway wants to submit jobs to.
2. When sharing application, deployment you would only share it with gateway user who you want to use it.
3. Tip: When you are adding a new application, you can keep it without sharing it with gateway users until you test it. Unshared applications will appear grayed out to gateway uses.


 



