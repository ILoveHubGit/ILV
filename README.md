# Integrated Landscape Visualization (Version 0.4.2)
<img src="resources/public/img/ilv-logo.svg" width="20%" align="left"/>

Are you tired of trying to understand the complex web of connections between the various systems in your organization? Do you struggle to keep track of how each system fits into the bigger picture?

This tool is here to help! It takes in information about the links between the various systems in your organization through a simple API interface, and automatically generates a visually appealing graph that clearly illustrates the relationships between the different systems. No more sifting through confusing spreadsheets or trying to make sense of disorganized documentation - the graph provides a simple and intuitive way to understand the landscape of your organization's systems.

And that's not all - this tool also gives you the ability to export the landscape in table format to a PDF, making it easy to share with your colleagues or keep a record of the relationships between the systems. Plus, with the API interface, it's easy to integrate my tool into your existing workflow and keep your system landscape up to date.

This tool is easy to use and requires no technical expertise to understand. Simply input your information through the API interface and let the tool do the rest. You'll be able to clearly see the relationships between the different systems, giving you a better understanding of how they all fit together.

Don't waste any more time trying to piece together the puzzle of your organization's system landscape, send me a message through [my LinkedIn account][1] and I will help you setting it up. Try this tool today and see the difference for yourself!

Want to read more information on how you can use this tool, see [Info on Integrated Landscape Visualization][2]. For a live version of this tool, with which you can play, use [Integrated Landscape Visualization][3].

Below an impression of the GUI
![GUI][screen-graph]


This useful information can be integrated with your existing workflow by using these API calls.
![Swagger page][screen-swagger]

## Prerequisites
Have Java version 11 or above installed

## Running
Request a zip-file via [my LinkedIn account][1]
 - Unzip the file in any folder
 - Open the file config.edn
   - You can now change the port number or leave it at 3000
   - Choose what kind of database you want to use and remove the ;; before these lines and configure the line with the name and server
     - Make sure that you do this for both lines starting with :database-url and :migration-dir belonging to one database format

Currently three databases are supported:
 - H2 (database is created if it does not exist)
 - MS-SQL (Database needs to be created before running migration command)
 - MariaDB (Database needs to be created before running migration command)


If you run this application for the first time you need to run the following command to create the database structure:

    java -Dconf=config.edn -jar ilv.jar migrate

After this the application can be started with the following command:

    java -Dconf=config.edn -jar ilv.jar

Then open your browser and goto http://localhost:port and you should see the application. Configure your network settings in such a way that the server you installed this tool on can be reach via HTTP with the port number you configured. Open necessary ports in your firewall and make sure that the server is reachable from the outside by using a DNS name.

## Releases

### Version 0.4.3
- It's now possible to remove a link through the GUI
- The description that is shown on hover in the GUI is now multiline
### Version 0.4.2
- Added database support for MS-SQL
- Added database support for MariaDB
- Some small bug fixes

### Version 0.4.1
- Added functionality to the GUI to add links based on unused interfaces
- Increased the line thickness for better visibility
- Changed log configuration so old logfile are automaticaly compressed
- Improved layout of the GUI and PDF report

### Version 0.4.0
**REMARK**: This version is not compatible with the previous version
- Renamed application to Integrated Landscape Visualization
- Changed the color scheme
- Changed the database structure
- Added some new calls to the API and removed some obsolete calls
### Version 0.3.0
- Graph is now available
### Version 0.2.0

- Bug fixes
- Export to PDF added
- New icon for Links (stream, queue, real-time, realtime)
- Extra information in Swagger page

### Version 0.1.6

- Bug Fixes

### Version 0.1.5

- Bug fixes
- Added tests

### Version 0.1.4

- Added optional query parameter "keepVersions" also to Add SubNodes
- Added a logo

### Version 0.1.3

- Changed get-links query to be able to show links with multiple nodes
- Added an optional query parameter "keepVersions" to Add Nodes and Add Links
  - Possible values are:
    - None - This will inactivate all existing items
    - Last - This will inactivate all existing items except the last one
    - AllButOldest - This will keep all existing items active except the oldest one
    - All - This will keep all existing items active
  - If this parameter is used the new item will be linked the all node(s) or link that needs to stay active

### Version 0.1.2

- Prepared Graph View
- Added support for MS-SQL database

### Version 0.1.0

- Initial version included table view of interfaces

## License
Copyright © 2021 ILoveHubGit

[1]: https://www.linkedin.com/in/jverschuuren/ "LinkedIn"
[2]: http://jeroenverschuuren.nl/about-ilv.html "My homepage"
[3]: http://ilv.jeroenverschuuren.nl/ "ILV"

[screen-graph]: resources/public/img/ILV_animated.gif "GUI Impression"
[screen-swagger]: resources/public/img/ilv-swagger-0.4.0.png "Swagger view"
[VT-image]: resources/public/img/ilv-logo.svg "Logo"
