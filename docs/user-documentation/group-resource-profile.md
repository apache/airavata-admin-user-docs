#####<h5 id="GroupResourceProfile">Add a Group Resource Profile for Comet (GRP)</h5>
1. What is a group resource profile?
    - Group resource profile is a configuration which states how a particular HPC resource (campus, national, cloud) is available for users to use. 
    - One or many HPCs can be added to a GRP and then it can be shared with the users and user groups to enable use.
    - A gateway can have multiple GRPs and a gateway user can be in one or many GRPs
    - At the time of experiment creation, user need to select which GRP to move forward to launch experiment jobs.
2.  To Create a GRP
    - Navigate to Settings &rarr; Group Resource Profile.
    - Click New Group Resource Profile +.
    - Add Name: Default Gateway Profile
    - Default SSH Credential: Select a key from the list or generate a new one.
    - Click New Compute Resource +.
    - Select the resource from the list provided.
        - In next page provide the details required for SSH communication
        - Login Username: This is the login name to use in SSH login
        - SSH Credential: Select from the list, or generate a new one
        - Allocation Project Number: this is applicable for resources which maintains an account for user allocation and usage. 
        - Scratch Location: The location for users' computational working directories
    - Provide computational queue policies
        - This section will provide details of maximum node, walltime and CPUs per HPC resource that a gateway user could use in experiment creation.
        - If you don't specify these limits, then the maximum allowed from the HPC resource will be available for users.
        - NOTE: This feature is more popular with gateways which are used in educational purposes and also for gateways where the gateway admin provides XSEDE resoruces for free via community allocations.
        - Click Save
        - Next page, click Save

##### <h5 id="Resources">Register your Compute & Storage Resources</h5><br>

<b class="lred"> NOTE:</b> Only SciGaP admins or gateway service provider can add compute resources and storage resources. <br> If the gateway and middleware is hsoted by you, You can add the Compute Resources and Storage Resource.
<br></br><b>What is a compute resource? </b><br>A compute resource is an object that represents a host, host cluster, or pool in a virtualization platform, a virtual data center, or an Amazon region on which machines can be provisioned. 
<br>Compute resource could come as national resources, campus resources or even private cluster. 
<br>NOTE:For testing purposes users (mainly gateway developers) this could even be the local machine.
<br></br><b>What is a storage resource?</b><br>A storage resource is the server that stores all user data files: application input files and output files. 
<br>Most of the time this is the same server that the gateway is deployed in. The storage resource can be either provided by the gateway provider or by you. 
<br>If the gateway service provider is providing the resource, then there will be file retention policies in place.

###### <b><u>Compute Resource Information </u></b>
Provide the information below to get your compute resource/HPC registered with Super admin portal, <a href="https://scigap.org/" target="_blank">SciGaP</a><br>
1. HPC Name (This is the name used to SSH to the resource)<br>
2. Queue details (Queue name, maximum limits of nodes, CPUs and Walltime.)<br>
3. Resource manager type (SLURM, PBS)<br>
4. Job command binary path <br>

###### <b><u>Register a XSEDE Resource </u></b>
NOTE: Please note this set of instructions are ONLY for gateways hosted by the user. If not SciGaP admins will do this configuration for you in <a href="https://scigap.org/" target="_blank">SciGaP Portal</a>. <br>
1. Navigate to Admin Dashboard &rarr; Compute Resource &rarr; Register <br>
2. Provide
    - Host Name: comet.sdsc.edu<br>
    - Host Aliases: <br>
    - IP Addresses:<br>
    - Resource Description: SDSC Comet Cluster ( Just a description)<br>
    - Create<br>
3. In Queues tab<br>
    - Click 'Add a Queue'<br>
    - Queue 1
        - Queue Name: compute ( Per resource this is a unique value. Once created cannot edit the name. If need to change, delete and create again)<br>
        - Queue Description: Used for access to regular compute nodes<br>
        - Queue Max Run Time (In Minutes): 280 (Note required for the local resource)<br>
        - Queue Max Nodes: 72 (Note required for the local resource)<br>
        - Queue Max Processors: 1728 (Note required for the local resource)<br>
        - Max Jobs in Queue: 0 (Note required for the local resource)<br>
        - Max Memory For Queue( In MB ): (Note required for the local resource)<br>
    - Queue 2
        - Queue Name: shared ( Per resource this is a unique value. Once created cannot edit the name. If need to change, delete and create again)<br>
        - Queue Description: Single-node jobs using fewer than 24 cores<br>
        - Queue Max Run Time (In Minutes): 2880 (Note required for the local resource)<br>
        - Queue Max Nodes: 1 (Note required for the local resource)<br>
        - Queue Max Processors: 24 (Note required for the local resource)<br>
        - Max Jobs in Queue: 0 (Note required for the local resource)<br>
        - Max Memory For Queue( In MB ): (Note required for the local resource)<br>
4. File System<br>
    - Nothing to add here, this is futuristic development.<br>
5. Job Submission Interface<br>
    - Click on the tab<br>
    - Add a new Job Submission Interface<br>
    - Job Submission Protocol: SSH<br>
    - Select Security Protocol: SSH_KEYS
    - SSH Port: 22
    - Select resource manager type: SLURM<br>
    - Job Manager Bin Path: /usr/bin/
    - Job Commands (SUBMISSION): sbatch<br>
    - Job Commands (JOB_MONITORING): squeue<br>
    - Job Commands (DELETION): scancel<br>
    - Parallelism Prefixes (MPI): mpiexec <br>
    - Add Job Submission Protocol<br>
6.  Data Movement Interface<br>
    - Add a new Data Submission Interface<br>
    - Data Movement Protocol: SCP<br>
    - Select Security Protocol: SSH_KEYS <br>
    - SSH Port: 22 <br>
    - Add Data Movement Protocol<br>
Now the Local resource is ready for job submissions.<br>
Comet is ready for job submissions.     

###### <b><u>Register a Campus Resource </u></b>
NOTE: Adding a campus resource is similar to adding a XSEDE resource. Same steps to follow with similar information.

