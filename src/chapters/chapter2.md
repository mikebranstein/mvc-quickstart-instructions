## NuGet and Source Control

You shouldn't source control NuGet packages, but configuring this correctly in TFS can be confusing. This section shows how to do this.

### Add NuGet.config file

First, we'll need to create a nuget.config file that disabled nuget source control integration. This will go into a folder named `.nuget` in the base of your branch.

<h4 class="exercise-start">
    <b>Exercise</b>: Add a nuget.config file to your repository
</h4>

Add a `.nuget` folder to the base of your repository.

After adding the `.nuget` folder, add a file named `nuget.config` to the folder. Add the following to the file:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <solution>
    <add key="disableSourceControlIntegration" value="true" />
  </solution>
</configuration>
```

Commit this to your source control repository.

<div class="exercise-end"></div>

### Ignoring NuGet packages in source control

Next, we need to add a `.tfignore` file to the root of your branch. 

> The `.tfignore` files is a file that tells TFS which files and fodlers should be excluded from source control.

<h4 class="exercise-start">
    <b>Exercise</b>: Add a .tfingore file 
</h4>

Add a `.tfignore` file to the base of your repository.

Add the following to the file:

```
\packages
!\packages\repositories.config
```

This file tells TFS to ignore the contents of the folder named `\packages`, but to include the repositories.config file. 

The repositories.config file includes special information about your NuGet packages repositories. Not all projects need this file, but we add it to the inclusion list just in case your project needs it.

Commit this to your source control repository.

<div class="exercise-end"></div>

