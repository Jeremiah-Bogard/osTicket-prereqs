# osTicket

Learn about a free ticketing system for helpdesk called osTicket. We will set up osTicket in our Windows 10 Virtual Machine and simulate ticket creation and account creation (agent and customer).

## Requirements

1. Microsoft Azure Subscription
    1. Windows 10 Virtual Machine
2. osTicket Installed on VM
    1. Main account created
    2. Connected to database

## Getting Started

After installing osTicket and it has been connected to a database, we will need to sign in with the account you create. You can get to the sign in page by going to http://localhost/osTicket/scp/login.php and enter the information for the main admin account you created. Now that you are logged in, we need to create several other accounts or agents. However before we can do this, we need to add several roles. Each agent in our company will be assigned a role. A role gives them certain permissions without us having to select each one every time. For example, if we create a role called "Supreme Admin" that can do everything they want, then if we assign an agent that role then they can do everything they want and we don't have to select each thing everytime. Let's create a couple roles now. First we need to go to the admin panel. If you are already on the admin panel then the button next to your name in the top right corner should say "Agent Panel". Now go to "Agents", "Roles", and "Add New Role". Create two roles called "Supreme Admin", which you will need to set the permissions to all of them, and "Basic User", which you will give only permission to open, close, and solve tickets.

![Add Agent Roles](/add-roles-location.png)

Now we can create our agents. Go to "Agents'', "Agents", and "Add Agent". You will need to create several agents. One Supreme Admin and one Basic User. It does not matter what you call them, just make sure you assign them the roles we created earlier. You will be required to assign it to a department, it can be any department you want as this is just to understand how this works. However if this was a real company we would have several departments to which we would assign that agent to the department they would be working in.

Now you can logout and login as your Supreme Admin user. Notice that you still can do everything your master account could do. That is because this agent has the Supreme Admin role which is allowed to do everything. We now have our agents, but before we can simulate ticket creation we need to set several things first, which are Help Topics and SLAs or Service Level Agreement. Help Topics are just ways to organize the tickets that are created and they also help with sending the tickets to the correct department. For this example though, we will just create some simple help topics. To do this we need to go to the "Admin Panel", "Manage", and "Help Topics''. Create the following topics:

1. Business Critical Outage
2. Personal Computer Issues
3. Equipment Request
4. Password Reset

![Creating Help Topic](/create-help-topic.png)

SLAs or Service Level Agreement are used to prioritize tickets. In other words, they are used to show which tickets are more important and the maximum amount of time it should take to fix the issue. We will create three levels called Sev-A, Sev-B, and Sev-C. We will set A to a Grace Period of 1 hour and a schedule of 24/7. This means that Sev-A will be an important issues that need to be done within an hour of the ticket being created.

| Name | Grace Period | Schedule |
|------|--------------|----------|
| Sev-A | 1 hour | 24/7 |
| Sev-B | 4 hours | 24/7 |
| Sev-C | 8 hours | Bissenous Hours (Monday-Friday) |

![Create Service Level Agreement](/create-sla.png)

## Ticket Simulation

The setup is complete. Now we can simulate ticket creation and handling. To create a ticket we can go to http://localhost/osTicket or we can go to the "Agent Panel'', "Open Tickets", "Open". You can use either method, it does not matter just create several tickets to play around with. When you create the ticket it will show up in the Open Tickets que. You can now select that ticket and respond to the customer and close the ticket. If you are logged in as the Supreme Admin then you can also assign the ticket to departments, agents, or agents with a certain role.
