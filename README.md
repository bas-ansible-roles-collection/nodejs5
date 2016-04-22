# NodeJS 5 (`nodejs5`)

Master: [![Build Status](https://semaphoreci.com/api/v1/bas-ansible-roles-collection/nodejs5/branches/master/badge.svg)](https://semaphoreci.com/bas-ansible-roles-collection/nodejs5)
Develop: [![Build Status](https://semaphoreci.com/api/v1/bas-ansible-roles-collection/nodejs5/branches/develop/badge.svg)](https://semaphoreci.com/bas-ansible-roles-collection/nodejs5)

Installs NodeJS 5 runtime and Node Package Manager (NPM)

**Part of the BAS Ansible Role Collection (BARC)**

**This role uses version 0.2.0 of the BARC flavour of the BAS Base Project - Pristine**.

## Overview

* Installs NodeJS and Node Package Manager (NPM)

## Quality Assurance

This role uses manual and automated testing to ensure its features work as advertised. 
See [here](tests/README.md) for more information.

## Dependencies

* None

More information on role dependencies is available in the 
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Role-dependencies)

## Requirements

* None

More information on role requirements is available in the 
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Role-requirements)

## Limitations

* The NodeJS and NPM version varies depending on which operating system is used and if non-system package sources are 
permitted

As the package policy varies between system and non-system package sources, and between operating systems, the version 
of NodeJS installed is variable between supported operating systems.

For both Ubuntu and CentOS, a non-system package repository is installed resulting in more recent versions of NodeJS to 
be installed. The exact version installed is not pinned by this role, and therefore cannot be relied upon to result in
a specific minor or patch release being installed.

It is a convention of BARC roles to use the latest version of packages. Where a suitable non-system package source is 
available it will be used. Otherwise system packages will be used. Suitable non-system packages require a reputable,
maintainer, typically a company or well respected individual. Where non-system packages are used, the variable 
*BARC_use_non_system_package_sources* can be set to `false` to always use system packages if this is needed.

_This limitation is **NOT** considered to be significant. Solutions will **NOT** be actively pursued._ 
_Pull requests addressing this limitation will be considered.*_

See [BARC-121](https://jira.ceh.ac.uk/browse/BARC-121) for further details.

More information on role limitations is available in the 
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Role-limitations)

## Usage

### BARC Manifest

By default, BARC roles will record that they have been applied to a system, this is termed the BAS Manifest.
The specific local facts set for this role are:

* `ansible_local.barc_nodejs5.general.role_applied` - (boolean) records whether a role has been applied
* `ansible_local.barc_nodejs5.general.role_version` - (string) records the version of the role that was applied

Note: You **SHOULD** use this feature to determine whether this role has been applied to a system.
If you do not want these facts to be set by this role, you **MUST** skip the **BARC_SET_MANIFEST** tag.

More information is available in the 
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Role-Manifest)

### NodeJS / NPM version

Depending on the operating system used, the version of NodeJS and NPM installed will differ, though it will be at 
least NodeJS *5.0*. The table below hopes to clarify the version you can expect:

| Operating System | Non-System Package Sources Permitted | Ruby Version | Notes  |
| ---------------- | ------------------------------------ | ------------ | ------ |
| Ubuntu           | Yes                                  | *5.x*        | [1]    |
| CentOS           | N/A                                  | *5.x*        | [1]    |

Because the exact version installed cannot be guaranteed by this role, you should be careful if using depending on this 
role in another role or a project that relies on NodeJS. If any version of NodeJS 5 is acceptable this role is suitable,
however where you depend on some feature added to minor releases (e.g. *5.1*) this role is unsuitable.

This ambiguity is considered a limitation. See the *limitations* section for more information.

[1]  There is no system-only source available for which has a up-to-date enough version of NodeJS. Therefore the 
non-system packages are used in all circumstances.

### Typical playbook

```yaml
---
 
- name: ...
  hosts: all
  become: yes
  vars: []
  roles:
    - bas-ansible-roles-collection.nodejs5
```

### Tags

BARC roles use standardised tags to control which aspects of an environment are changed by roles.
Tasks in this role will 'tag' themselves with these tags as appropriate, typically in `tasks/main.yml`.

More information is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Appendix-B---BARC-Standardised)

### Variables

#### *nodejs5_barc_role_name*

* **MUST NOT** be specified
* Specifies the name of this role within the BAS Ansible Roles Collection (BARC) used for setting local facts
* See the *BARC roles manifest* section for more information
* Example: `nodejs5` 

#### *nodejs5_barc_role_version*

* **MUST NOT** be specified
* Specifies the name of this role within the BAS Ansible Roles Collection (BARC) used for setting local facts
* See the *BARC roles manifest* section for more information
* Example: `2.0.0` 

## Developing

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the 
[BAS Ansible Roles Collection](https://jira.ceh.ac.uk/projects/BARC) (BARC) project on Jira.

This service is currently only available to BAS or NERC staff, although external collaborators can be added on request.
See our contributing policy for more information.

More information is also available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Issue-Tracking)

### Source code

All changes should be committed, via pull request, to the canonical repository:

`ssh://git@stash.ceh.ac.uk:7999/barc/nodejs5.git` 

A read-only mirror of this repository is maintained on GitHub:

`git@github.com:bas-ansible-roles-collection/nodejs5.git`

More information is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Source-Code)

### Contributing policy

This project welcomes contributions, see `CONTRIBUTING.md` for our general policy.

### Release procedure

The general release procedure for BARC roles is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Release-procedures)

## Licence

Copyright 2016 NERC BAS.

Unless stated otherwise, all documentation is licensed under the Open Government License - version 3.
All code is licensed under the MIT license.

Copies of these licenses are included within this project.
