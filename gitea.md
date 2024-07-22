Install Gitea Using Docker
You can install Gitea using Docker by following the instructions in this link.

Ubuntu on VirtualBox in Background
To automatically start your VirtualBox VM in headless mode when Windows 10 boots up, you can create a task in Task Scheduler. Here’s how you can do it:

Open Task Scheduler:
Press Win + R, type taskschd.msc, and press Enter.
Create a New Task:
In the Task Scheduler window, click on “Create Task” in the right-hand pane.
General Settings:
Give your task a name (e.g., “Start Ubuntu VM”).
Select “Run whether user is logged on or not”.
Check “Run with highest privileges”.
Trigger:
Go to the “Triggers” tab and click “New”.
In the “Begin the task” dropdown, select “At startup”.
Click “OK”.
Action:
Go to the “Actions” tab and click “New”.
In the “Action” dropdown, select “Start a program”.
In the “Program/script” field, enter the path to VBoxManage.exe (e.g., C:\Program Files\Oracle\VirtualBox\VBoxManage.exe).
In the “Add arguments” field, enter:
startvm "Your_VM_Name" --type headless

Click “OK”.
Conditions:
Go to the “Conditions” tab and uncheck “Start the task only if the computer is on AC power” if you want the VM to start even when on battery.
Settings:
Go to the “Settings” tab and ensure “Allow task to be run on demand” is checked.
Click “OK” to save the task.
Enter Credentials:
You may be prompted to enter your user credentials to create the task.
Example:

Action: "C:\Program Files\Oracle\VirtualBox\VirtualBoxVM.exe"
Add arguments: --startvm "{284145fb-3dfc-4c34-bc81-964e31c56147}" --type "headless"
