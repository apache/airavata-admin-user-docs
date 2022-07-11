## Group Resource Profile (GRP)

##### <h5 id="Resources">Register your Compute & Storage Resources</h5><br>

<b class="lred"> NOTE:</b> Only SciGaP admins or gateway service provider can add compute resources and storage resources. <br> 
<br></br><b>What is a compute resource? </b><br>A compute resource is an object that represents a host, host cluster, or pool in a virtualization platform, a virtual data center, or an Amazon region on which machines can be provisioned. 
<br>Compute resource could come as national resources, campus resources or even a private cluster. 
<br>NOTE:For testing purposes, users (mainly gateway developers) this could even be the local machine.
<br></br><b>What is a storage resource?</b><br>A storage resource is the server that stores all user data files: application input files and output files. 
<br>Most of the time this is the same server that the gateway is deployed in. The storage resource can be either provided by the gateway provider or by you. 
<br>If the gateway service provider is providing the resource, then there will be file retention policies in place.

###### <b><u>Compute Resource Information </u></b>
Provide the information below to get your compute resource/HPC registered with Super admin portal, <a href="https://scigap.org/" target="_blank">SciGaP</a><br>
1. HPC Name (This is the name used to SSH to the resource)<br>
2. Queue details (Queue name, maximum limits of nodes, CPUs and Walltime.)<br>
3. Resource manager type (SLURM, PBS)<br>
4. Job command binary path <br>


