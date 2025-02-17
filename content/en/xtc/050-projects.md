---
title: "Projects"

weight: 50
type: docs

description: >
    Projects in XTC, how they work, how to create them and change project members.
---

Organizations are containers for projects, which in turn are the containers for any kind of test run in XTC. 

## XTC Project Types

Projects can either be of type [monitoring]({{< relref "monitoring" >}}) or [load test]({{< relref "loadtesting" >}}). They have a different set of properties depending on their nature. 

In short, **Load Test Projects** are used to perform a number of load/performance tests, each of which can be configured individually (e.g. for gradually increasing the load applied to the system). XTC will save the results and generate performance reports for each load test it runs, so you have test management and evaluation conveniently available in one place.

**Monitoring Projects** contain a number of test scenarios that are repeated periodically to monitor the reliability and performance of an app over a longer time period including but not limited to functional monitoring of production environments. You may define criteria which will be validated during the scenario execution (runtime limits, error thresholds etc.) - violation of these causes notifications to be sent (you may define how and to whom).

The project type will be indicated in the project tile:

{{< image src="xtc/organizations_monitoringProject.png" >}}
A monitoring project on the dashboard of the _Xceptance_ organization.
{{< /image >}}

The project menu on the left side will look a bit different depending on whether you are currently viewing a [load test project]({{< relref "loadtesting" >}}) or a [monitoring project]({{< relref "monitoring" >}}):

{{< image src="xtc/project_menus.png" >}}
The menu of a monitoring project (left) and a load testing project (right).
{{< /image >}}

Every project can be [assigned its own set of members]({{< relref "#adding-and-removing-project-members" >}}) and [configured]({{< relref "060-project-configuration" >}}) independently of any other project in the organization. 

## Creating a New Project

{{% permission role="organization administrator" action="create new projects" %}}

To create a new project within an organization, navigate to this organization and select _Projects_ in the menu on the left. 

You will be shown a list of the projects in this organization:

{{< image src="xtc/ui_projectsInOrg.png" >}}
A list of projects in an organization, as seen by the organization administrator.
{{< /image >}}

By clicking the `+` button top right, you will see a popup menu to add either a [Monitoring Project]({{< relref "monitoring" >}}) or a [Load Testing Project]({{< relref "loadtesting" >}}). The project nature can not be changed once the project was created. 

{{< image src="xtc/ui_newProject.png" >}}
Adding a new project
{{< /image >}}

On **creating a new project**, you will then be prompted to enter a name and a short name for the new project. The short name must be unique within the organization, must start with a lower-case letter, followed by at most 39 lower-case letters, digits and hyphens, and must not end with a hyphen.

All information but the short name can be updated using the context menu on the right of the project name in the project list, selecting _Edit_. 

You can also create new projects by selecting _Duplicate_ in the context menu of any existing project - this way, you can easily apply the configuration of an obsolete project to a new one.

On **duplicating a project** you will have to update at least the short name to be unique across the organization. The duplicated project will then be copied including its entire configuration. Please note that the duplicated project will need to be activated explicitly though (by clicking _Edit_ in the new project's context menu you can change the state from _Locked_ to _Active_). 

## User Roles Within a Project 

A project's creator is automatically an administrator in this project, and as such can add additional user accounts as members of project. These do not necessarily need to be members of the organization already, but will implicitly be added as guest members to the organization when added to the project (independent of their project role). 

Project members can have one of the following roles (which are not necessarily identical to these users' organization role): 
* a **guest** has only permission to view the project dashboard, 
* a **reviewer** can view load tests and load test details (for load tests) or results and history (in monitoring),
* a **tester** may create, configure and run load tests or view logs and configuration of monitoring projects,
* a **test manager** is additionally allowed to edit most of the project configuration for load test projects as well as monitoring projects, and
* a **project administrator** has the complete set of permissions, including editing the project members.

(Permissions increase in order of the list, i.e. a tester has the same permissions as a reviewer plus some in addition to that.)

If you are logged in and are currently viewing a project, your project role will be displayed at the bottom right in the footer:

{{< image src="xtc/ui_projectRole.png" >}}
Footer displaying the user's role in the project.
{{< /image >}}

## Adding and Removing Project Members

{{% permission type="project" role="project administrator" %}}

To **add new members to the project**, navigate to the project and select _Members_ in the menu on the left. You will see the list of project members, and by clicking the `+` sign in the top right, you can add new members by typing the name (mail address) of their user account and assigning one of the roles from above. The user you want to add needs to be signed up with this e-mail address already. 

If you want to add multiple users at once, simply paste a list of e-mail addresses (separated by comma, newline or space). All users will be assigned the same role.

To **update a user's role** within a project, go to the project members list and click the context menu right of the user name, then select _Edit_. You can then pick a new membership role. 

To **remove members** from a project, go to the project members list and click the context menu right of the user name, then select _Remove_ (you will be prompted to confirm the deletion).

{{% note notitle %}}
Please note that after removing members from the project, they are not automatically deleted from the organization as well, but will remain there until you explicitly remove them from the organization.
{{% /note %}}

