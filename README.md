Summary
=======

This example, users can:
    • Use multiple credentials for different server types (web, db, mid-tier) defined in the "inventory.init" file.
    • Tagging tasks in the playbook for better targeting (e.g., install, start, web, db, midtier).
    • Running playbooks with specific tags and limits to control which tasks are executed.
    
Key Points:
===========
    • Each playbook section corresponds to a group of servers: web_servers, db_servers, and midtier_servers.
    • Each playbook task is tagged according to its role (web, db, midtier) and type of action (install, start).
    • You can also include other tasks specific to your infrastructure, like configuration, updates, etc.

Run the Playbook with Specific Tags
===================================

    When you run the playbook, you can target specific tags to run only certain tasks.
**    Example 1: Run only the Web Server Install Tasks
**    
    If you want to only run the install tasks for the web servers, use the --tags option like this:

        $ ansible-playbook -i inventory.ini site.yml --tags install --limit web_servers

        This will:
            • Only run the tasks tagged as install for the web_servers group.
            • You can also use multiple tags, for example: --tags install,start if you want to install and start services.

**    Example 2: Run all Mid-Tier Tasks
**    
    If you want to run all tasks related to mid-tier servers (e.g., install Java and start the service):
    
        $ ansible-playbook -i inventory.ini site.yml --tags midtier

**    Example 3: Target Database Servers for Specific Task
**
    To run a task on the database servers, for example, just starting the MySQL service:

        $ ansible-playbook -i inventory.ini site.yml --tags start --limit db_servers

        This will:
            • Run tasks tagged as start on the db_servers group only.

**    Example 4: Run All Tasks for Specific Groups
**    
    If you want to run all tasks for a particular set of servers, use --limit to specify the server group:

        $ ansible-playbook -i inventory.ini site.yml --limit web_servers

        This will run all tasks defined under the web_servers group.
