# aws_ansible_integration
Deals primarily with the compute cloud instances <br/>

It basically goes like in the following manner:<br/>
<b>I.</b> It checks the number of running instances in the compute cloud environment<br/>
<b>II.</b>  If that's equal to 1 in number, then it launches one more instance for HA purpose<br/>
<b>III.</b>  It holds till the additional instance is made available in the desired state, which is obviousy in Running state<br/>
<b>IV.</b>  Now if II and III conditions prove to be true, then it performs subsequent steps with the help of HANDLERS in ansible<br/>
<b>V.</b>  It would be deploying a newer version of same old image or a new image itself for the instances, just like we've in k8s for updating the deployment, where we may follow strategies like Recreate, Rolling Update, etc into account<br/>
<b>VI.</b>  Here we're going to follow the recreate strategy, even though it's not a recommended one due to downtime issue<br/>
<b>VII.</b>  After the deployment/modifications by us are stable, we're good to return back to original instance count, thus terminating the additional instance.<br/>
