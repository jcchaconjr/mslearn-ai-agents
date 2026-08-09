# Develop AI Agents in Azure

The exercises in this repo are designed to provide you with a hands-on learning experience in which you'll explore common tasks that developers perform when building AI agents on Microsoft Azure.

> **Note**: To complete the exercises, you'll need an Azure subscription in which you have sufficient permissions and quota to provision the necessary Azure resources and generative AI models. If you don't already have one, you can sign up for an [Azure account](https://azure.microsoft.com/free). There's a free trial option for new users that includes credits for the first 30 days.

View the exercises in the [GitHub Pages site for this repo](https://go.microsoft.com/fwlink/?linkid=2310820).

> **Note**: While you can complete these exercises on their own, they're designed to complement modules on [Microsoft Learn](https://learn.microsoft.com/training/paths/develop-ai-agents-azure/); in which you'll find a deeper dive into some of the underlying concepts on which these exercises are based.

If you choose to run the code from applications in this repository locally, it will require Python 3.12+.

## Reporting issues

If you encounter any problems in the exercises, please report them as **issues** in this repo.

## Personal Notes

**DISCLAIMER:** This is a personal fork of the Microsoft provided lab resources indicated above, with my personal notes indicating what I have updated in the project. If you'd like to work with the original Repo as provided by MSLearn, you can clone it yourself from the link provided above, or below in the Lab Notes.

## VS Code Environment Requirements

 To properly set up the VS Code development environment in Windows 11, I set up the following:

 - Python 3.13 (Download from the Microsoft Store app in Windows)
 - The Python Language Support extension from Microsoft
 - Ensure that Python is set up to use env files (hit CTRL + the comma key to open Settings) - enter python.envfile.useenvfile in the Settings search bar to see the property - make sure it is checked.
 - Use the Windows Package Manager to load the Azure CLI (PowerShell command: *winget install -e --id Microsoft.AzureCLI*)
 - After the CLI is installed, to ensure that Azure login authenticates via web browser, enter the following PowerShell command: *az config set core.allow_broker=false*
 - The OpenAI endpoint in the project's .env file **MUST** be updated with the OpenAI endpoint generated after creating a project resource as indicated in the Lab 3 instructions. 

 In this case, I used the lab credentials locally after setting up the code and environment on my local machine. With the models deployed via the Skillable session, the model resource is accessible externally, as long as you have the model requirements (OpenAI endpoint, Model Deployment name) set up locally. All Lab exercises expect a Resource Group to place the project in. The Lab examples use "ResourceGroup1", which is typically already created in the Lab environments. If your subscription space doesn't have one, you should create a RG specifically for this exercises, as it calls for deleting the group afterward to ensure proper cleanup of resources. 

## Lab 6

**Lab 6** from the **Skillable Lab series** for **AI-103 certification**, focuses on Exercise 2 in this Repository. The instructions for building the chat agent in Microsoft Foundry, along with the code details that were added to the generic code sample, can be found in:
.\Instructions\Exercises\02-agent-cusomt-tools.md

Some notes to successfully complete this exercise:

- As in my case, you might get an error creating the 'labenv' environment, as indicated in Step 9 of the section, **CLone the starter code repository**, where youa re asked to create the environment and install the packages listed in requiremets.txt.
- To work around this issue, I entered "Python: Create Environment" from the command prompt entry at the top (CTRL+SHIFT+P), selected venv, Python 3.13, then installed the package list for the requirements.txt file that is in the Labfiles folder for exercise 2.
- When running the agent.py script, you MIGHT encounter an unhandled "Rate Limit Exceeded" error message. This of course depends on the Azure accout being used, not to mention the token limitations configured in the model when launched. If running from a Skillable provided account, you will in all likelyhood encounter this. THe workaround is tro basically wait about 10 minutes before submitting the follow up prompt after the first one as indicated in the instructions (Step 3 of "Run the agent applaication).

The script provided here in this exercise was successfully run outside of the Sillable provided VM, using the lab crednetials supplied.

## Lab 8

**Lab 8** from the Skillables Lab series for **AI-103** certification focuses on Exercise 3 in this repository. The instructions for building the Foundry resources via the Microsoft Foundry Extension, along with the code added to the sample app can be found in:
.\Instructions\Exercises\03-mcp-integration

Some notes to successfully complete this exercise:

- Again, if you have a global Python installation, building the Labenv as suggested in the instrcutions might generate warnings and leave the environemnt in a state where it can't properly load the packages. Just as in the last exercise, it's better to build a .venv environment to isolate execution.
- To work around this issue, enter "Python: Create Environment" from the command prompt entry at the top (CTRL+SHIFT+P), selected venv, Python 3.13, then installed the package list for the requirements.txt file that is in the Labfiles folder for exercise 3.
- There is a minor note to be aware of when editing the server.py file. In the sections indicated for steps 4 and 5, The example code implies that more than just one line should be added to the code. In these steps, you should ONLY add the line , "@mcp.tool()" to the code where indicated. This isn't an issue if you use the completed code as provided here, but just something to note if you are followingf along with the instructions.
- When prompted to run the Agent.py script, the script will begin to build the agent, but will not complete in the lab environment (if using one) due to a "Rate Limit Exceeded error". THis shouldn't happen in your own environment, but know that limitations on your account could exist that could also cause this error.
- Regardless of the error above, when instrcuted to run the Client.py script, it should run as expected.


## Cleanup

Also as noted, DON"T FORGET to clean up any and all Azure resources after you complete a lab! As the labs typically As you to Create the lab projects inside of a Resource Group named "ResourceGroup1", the fastest way to clean up is by going into the Azure portal site (portal.azure.com) then deleting that resource group after bringing up the Resource Groups list. Just select the Resource Group, then from teh detail view for the Group, select "Delete Resource group" from the top, and follow the instructions. It should take about a minute to clean them up.

