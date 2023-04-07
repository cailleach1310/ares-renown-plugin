# Ares Renown Plugin
A plugin for handling renown - useful in games where renown/glory points are awarded. 

## Credits
Lyanna @ AresCentral

## Overview
Wherever progress is awarded based on IC achievements, be it for the individual character or the family or organisation they are part of, game staff may award points and review them at certain times to decide an improvement or worsening of their situation. This system is based on the idea of seasons, meaning that renown points will be reset with the start of each new season.

The respective amounts for awarded renown points are up to admin, but within this system it is possible to define certain standard types that come with default amount suggestions. Even if visibility of renown details can be triggered through a setting within the renown.yml config file, I'd recommend visibility for the sake of transparency.

### What this plugin covers
* Admin: Awarding points, viewing current renown, resetting renown of all characters. Both from the game client and the webportal.
* Players: View their current renown status, their renown entries and respective points, both from the game client and the webportal.
* Webportal: Renown Management route, where admin can view character points and family/org points, add entries, reset points.
* Webportal: Renown top ranking lists route.
* Game client: renown/top command to view top ranking lists on game.

## Screenshots
tbd.

## Installation
In the game, run: plugin/install https://github.com/cailleach1310/ares-renown-plugin

### Updating Custom Profile Files
If you do not have any existing edits to these custom files, you can use the files in the custom_files folder of this repository as-is. If you do, then you may use them as templates to add the lines of code needed for the renown plugin.

#### aresmush/plugins/profile/custom_char_fields.rb
Update with: custom_files/custom_char_fields.rb

### Updating Custom Web Portal Profile Files
If you don't have any existing edits to these custom files, you can use the files in the custom_files folder of this repository as-is. If you do, then you may use them as templates to add the lines of code needed for the renown plugin.

#### ares-webportal/app/custom-routes.js
Update with: custom_files/custom-routes.js

#### ares-webportal/app/templates/components/profile-custom.hbs
Update with: custom_files/profile-custom.hbs

#### ares-webportal/app/templates/components/profile-custom-tabs.hbs
Update with: custom_files/profile-custom-tabs.hbs

## Configuration

### Other plugins

#### /aresmush/game/config/website.yml
Add a route to the top bar menu for the admin management page. This route is limited to admin and coder roles. 
Add a route for the renown top rankings. This route is limited to logged in players and admins.

For example:

      top_navbar:
    (...)
    - title: System
      menu:
        - title: Renown - Rankings
          route: renown-top
        - title: Manage Renown
          route: renown-management
    (...)

### renown.yml 
You don't have to modify the renown.yml for the plugin to work, but you can make adjustments here. The keys in the yaml are explained below.

#### achievements
The plugin comes with two predefined achievements. More can be added here.

#### renown_fields
These fields will be shown in the webportal renown management route.

#### renown_group
Define here the group that will as family/organisation benefit from their members' renown. For example "house" or "family".

#### renown_members
Here you can define which kinds of characters are considered in the renown system. Entries will be "group" and "value", for instance "faction" and "Noble". If you change this to "{}", all approved characters will be considered.

     renown_members:
     - group: faction
       value: Noble

#### shortcuts
Here is a space where you can define shortcuts for the commands.

#### standard_types
Here you can define various standard types for renown entries. Use "type" for the name, and you can set points to positive or negative values.

     standard_types:
     - type: Freeform
       points: 0

#### visible
Set this to "false", if you don't want renown to be visible to other players. Default is "true".

## Uninstallation
Removing the plugin requires some code fiddling. See [Uninstalling Plugins](https://www.aresmush.com/tutorials/code/extras.html#uninstalling-plugins).

## License
Same as [AresMUSH](https://aresmush.com/license).
