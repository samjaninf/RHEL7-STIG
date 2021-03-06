RHEL 7 DISA STIG
================

**This role is still under active development.**

Configure a RHEL 7 system to be DISA STIG compliant. CAT I findings will be corrected and audited by default. CAT II and III findings can be enabled by setting the appropriate variables to `yes`.


This role is based on RHEL 7 DISA STIG: [Version 1, Rel 1 released on March 13, 2017](http://iase.disa.mil/stigs/os/unix-linux/Pages/index.aspx).


Requirements
------------

RHEL 7. Other versions are not supported.

Role Variables
--------------

| Name              | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `rhel7stig_cat1_audit` | `yes` | Audit for CAT I findings      |
| `rhel7stig_cat2_audit` | `no`  | Audit for CAT II findings     |
| `rhel7stig_cat3_audit` | `no`  | Audit for CAT III findings    |
| `rhel7stig_cat1_patch` | `yes` | Correct CAT I findings        |
| `rhel7stig_cat2_patch` | `no`  | Correct CAT II findings       |
| `rhel7stig_cat3_patch` | `no`  | Correct CAT III findings      |
| `rhel7stig_gui` | `no` | Whether or not to run tasks related to auditing/patching the desktop environment |
| `rhel7stig_av_package` | `no` | Anti-virus package(s) to install and service to start and enable. |
| `rhel7stig_antivirus_required` | `no` | Weather or not an antivirus must be installed |
| `rhel7stig_time_service` | `chronyd` | Set to `ntpd` or `chronyd`. |
| `rhel7stig_lftpd_required` | `no` | If set to `no`, remove `lftpd`. |
| `rhel7stig_tftp_required` | `no` | If set to `no`, remove `tftp` client and server packages. |
| `rhel7stig_snmp_community` | `Endgam3Ladyb0g` | SNMP community string that will replace `public` and `private` in `snmpd.conf`. |
| `rhel7stig_bootloader_password` | `Boot1tUp!` | GRUB2 bootloader password. This should be stored in an Ansible Vault. |

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
        - role: rhel7-stig
          when:
            - ansible_os_family == 'RedHat'
            - ansible_distribution_major_version | version_compare('7', '=')

License
-------

MIT
