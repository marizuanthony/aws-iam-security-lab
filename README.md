## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use AWS IAM to control access and permission settings in our AWS Account. I'm doing this project to learn about cloud security from the foundation, every company thinks about access permissions and there are even entire jobs called 'IAM Engineers' focused on the skills we are about to build today.

### Tools and concepts

Services I used were Amazon EC2 and IAM  Key concepts I learnt include IAM Users.policies,roles,groups, account aliases, I also practiced how to use the Policy Simulator and how JSON works.

### Project reflection

This project took me approximately 1hour 10 minutes. The most challenging part drafting the JSON IAM policy.      It was most rewarding to access denied when the intern tried to delete our production instance but was blocked by our IAM policy

### ❤️ Thanks for doing this project!

I chose to do this project today because IAM is a key skill when working with AWS Cloud computing.

## Tags

### What I did in this step

In this step, I will launch two EC2 instances because we need to boost the companies computing power as we are expecting more users and traffic into our website this December.

### Understanding tags

Tags are organisational tools that lets us label our resources. They are helpful for grouping resources, cost allocations and applying policies for all the resources with the same tag.

### My tag configuration

The tag I’ve used on my EC2 instances is called Environment. And the value I’ve assigned for my instances are

![Tags](https://nextwork.ai/anthony-marizu/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_2e0e5a5d)

## IAM Policies

### What I did in this step

In this step, I will use IAM Policies to control the access level of a new intern because they should have access to the development environment ie the dev instance  but not the production environment.

### Understanding IAM policies

IAM Policies are like roles that determine who can do what in our AWS account.

### The policy I set up

For this project I have set up a policy using JSON. We are using policies today to control who has access to our development environment instance

### Policy effect

I’ve created a policy that regulates access to the policy holder(intern) to have permission to do anything they want to any instance tagged development. They can also see any information related for any instance but they are denied access to deleting or creating tags for any instance as well

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy means wether or not the policy is denying or accepting action (effect). What the policy holder can or cannot do(action), and the specific AWS resources that the policy relates to (resources).

## My JSON Policy

![My JSON Policy](https://nextwork.ai/anthony-marizu/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_1c864649)

## Account Alias

### What I did in this step

In this step, I will setup an account alias which is like a nickname for our AWS Account Console login, this is because an account alias makes it simpler for our users to login.

### Understanding account aliases

An account alias is a nickname for an AWS account, instead of using our Account ID we can now use our Alias.

### Setting up my account alias

Creating an account alias took me 20 seconds, its a simple configuration on the IAM dashboard. Now our new console URL using the Alias rather than our AWS Account ID

![Account Alias](https://nextwork.ai/anthony-marizu/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_0eb4439b)

## IAM Users and User Groups

### What I did in this step

In this step, I will setup two resources(IAM User and IAM User groups),this is because IAM Users are like logins for people who need access to our AWS Account while User Groups are like folder to manage users that have the same level of access.

### Understanding user groups

IAM user groups are folders that collect IAM Users so that you can apply permission settings at the group level

### Attaching policies to user groups

I attached the policy I created to this user group, which means any user created inside this group will automatically get the permissions attached to our Development policy created earlier.

### Understanding IAM users

IAM users are people or entities that have access or can login to your AWS Account.

## Logging in as an IAM User

### Sharing sign-in details

The first way is to email the sign in instructions to the person. The second way is to download the CSV File with the sign in users consent.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed that our user is already denied access to the items on the main AWS dashboard. This was because we only set up permissions to our development EC2 instance, so our intern wouldnt have access to anything else or even see anything else.

![Logging in as an IAM User](https://nextwork.ai/anthony-marizu/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_6f2ab446)

## Testing IAM Policies

### What I did in this step

In this step, I will login to our own aws account as the intern and test access to the development and production instances because we want to make sure our intern doesnt have the ability to do anything that will affect our production environment

### Testing policy actions

I tested my JSON IAM policy by attempting to stop both the development and the production instances.

### Stopping the production instance

When I tried to stop the production instance we were met with an error and this is because our production instance is tagged with the production level which is outside the scope of our permission policy, interns are only allowed to do things on the development instance

![Testing IAM Policies](https://nextwork.ai/anthony-marizu/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_0e7a9d6a)

### Stopping the development instance

Next, When I tried to stop the development instance we saw the instance state change to 'stopping' and then ultimately stopped. This was because our permission policy allows the intern ie users in the dev IAM Group to stop instances amongst everything else.

![Testing IAM Policies](https://nextwork.ai/anthony-marizu/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_1811801c)

## IAM Policy Simulator

To extend my project, I'm going to test our permission policies in a safer and more controlled way, a tool called the IAM Policy simulator. I'm doing this because having to stop instances and login to AWS Account as other users is a bit disruptive, this is a more efficient way.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a tool that lets us simulate actions and test permission settings by defining a specifc user,role,group or action we want to test for. It's useful for saving time when testing oermission settings, no more logging into another user or stopping resources

### How I used the simulator

I set up a simulation for wether our Dev user group has permissions to stop instances or delete tags, the results were denied for both so we had to adjust the scope of the EC2 instances to ones that are tagged for development, once we attached the tag, permissions was allowed

![IAM Policy Simulator](https://nextwork.ai/anthony-marizu/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_069d8a621)
