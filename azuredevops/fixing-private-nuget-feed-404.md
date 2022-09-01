# Fixing Private NuGet Feed Throwing 404

Here's some backstory - our team had created a new pipeline with a dependency to one of our private nuget feeds. We have many pipelines like this one and have never experienced any issues. However, this time around, NuGet restore decided to fail. And keep on failing. 

Initially we used a .Net Core build step. The error we received was something along the lines of : `error NU1301: Unable to load the service index for source`.

We decided to switch the .Net Core build step to a NuGet restore build step, which explained the error in more detail. Essentially, NuGet was throwing a 404 due to a permission issue.

Weirdly, this permission issue wasn't present in any other pipeline. Creating a completely new pipeline from scratch resulted in the same problem.

The feed was in *"Project A"* in Azure Devops and we needed access to it in *"Project B"*. Our Build Service user was added as a contributor already, so this wasn't the issue. It turns out that the fix was to go to *Project Settings*, then to *Permissions*. Here, we needed to add our *Build Service user* as a member of the *Build Administrators* group, with _"View project-level information"_ set to allow. After this change, the build pipeline ran and restore no longer failed.

[source](https://developercommunity.visualstudio.com/t/error-vs800075-when-downloading-artifact-from-anot/1146258)