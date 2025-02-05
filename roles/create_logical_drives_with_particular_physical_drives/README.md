Create Logical Drives With Particulatr Physical Drives
=========

Creates logical drives with particular physical drives specified by raid_details in a given server


Role Variables
--------------
```
  baseuri:
    required: true
    description:
      - iLO IP of the server
    type: str
  username:
    required: true
    description:
      - Username of the server for authentication
    type: str
  password:
    required: true
    description:
      - Password of the server for authentication
    type: str
  raid_details:
    description:
      - List of RAID details that need to be configured in the given server.
    type: list
    elements: dict
    suboptions:
      LogicalDriveName:
        required: true
        description:
          - Logical drive name that needs to be configured in the given server
        type: str
      Raid:
        required: true
        description:
          - Type of RAID
        type: str
      DataDrives:
        required: true
        description:
          - Specifies the particular data drives
        type: list
      CapacityGB:
        required: true
        description:
          - Minimum size required in the physical drive
        type: int
  http_schema:
    required: false
    description:
      - 'http' or 'https' Protocol
    default: https
    type: str
```    

Dependencies
------------

No dependency on other modules.

Example Playbook
----------------

An example of how to use the role:

``` 
- hosts: servers
  vars:
    raid_details: 
      - LogicalDriveName: "LD1"
        Raid: "Raid1"
        CapacityGB: 1200
        DataDrives: ["1I:1:1", "1I:1:2"]
  roles:
     - create_logical_drives_with_particular_physical_drives
```
License
-------

BSD

Author Information
------------------

Varini HP (@varini-hp) Hewlett Packard Enterprise 2021 
