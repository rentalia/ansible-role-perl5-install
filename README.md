Ansible role: perl5-install
=========
Perl 5 build and install from source. Also it installs cpanm and cpm for perl modules management, and GNU stow for path management at OS level.

Requirements
------------
None.

Role Variables
--------------
Main vars to configure at inventory/playbook/group_vars/host_vars:

- stow_dir: directory where install perl binaries and libs stow_dir. Default value: /usr/local/stow
- perl5_version: default value: "5.24.0"
- perl5_local_path: the path where links to binaries, lib... will be created. Default value: /usr/local

Other configurable vars at defaults/main.yml: 
- src_dir: directory where download, unpackage and build the sources. Default value: /usr/src
- stow_opts: options for running stow. Default value "--ignore=man"
- perl5_name: default value: "perl-{{ perl5_version }}"
- perl5_package: default value: "{{ perl5_name }}.tar.bz2"
- perl5_url: default value: "http://www.cpan.org/src/5.0/{{ perl5_package }}"
- perl5_real_path: "{{ stow_dir }}/{{ perl5_name }}"
- perl5_build_opts: "-des"
- cpm_install: install cpm package manager. Default value: False

Vars at vars/*os family*.yml
- perl5_build_dependencies: list of package names needed to build perl.

Dependencies
------------
None.

Example Playbook
----------------

    - hosts: servers
      roles:
         - rentalia.perl5-install
      vars:
        perl5_version: "5.26.0"
        cpm_install: True
        stow_dir: /opt/stow

License
-------
This project is licensed under the GPLv3 license - see the LICENSE file for details.

Author Information
------------------
This role was created in 2017 by [Francisco J. Tsao Santín](https://gattaca.es), devops engineer at [Rentalia](https://www.rentalia.com) 
