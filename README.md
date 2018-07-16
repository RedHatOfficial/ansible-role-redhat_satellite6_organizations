# Role Name

Ansible role for configuring everything about the Organizations in Satellite 6. Including but not neccisarly limited to:
* Create Organization(s)
* Upload Manfiest
* Create Lifecycle Environment Paths
* Enable Repositories
* Create Sync Plans

# Role Variables

| parameter                | required | default | comment
|--------------------------|:--------:|---------|:-------
| satellite\_api\_basion   | Yes      |         |
| satellite\_username      | Yes      |         |
| satellite\_password      | Yes      |         |
| satellite\_url           | Yes      |         |
| satellite\_organizations | Yes      |         |

## satellite\_organizations

Details about the `satellite_organizations` role variable dictionary.

| key                           | comment
|-------------------------------|:-------
| name                          |
| manifest                      |
| lifecycle\_environment\_paths |
| repositories                  |
| sync\_plans                   |

# Example Playbook

```
- name: Satellite 6 Configuration Example
  host: localhost
  vars:
    satellite_api_basion: localhost
    satellite_username: ansible-tower
    satellite_password: NAPSR0cks!
    satellite_url: https://satellite.rhc-lab.iad.redhat.com
    satellite_organizations:
    - name: IanTest
      manifest: files/manifest_IAN_TEST_20180708T164433Z.zip
      lifecycle_environment_paths:
      - environments:
        - dev
        - test
        - prod
      - environments:
        - foo
        - bar
      repositories:
      - name: Red Hat Enterprise Linux 7 Server (RPMs)
        product: Red Hat Enterprise Linux Server
        basearch: x86_64
        releasever: "7Server"
      - name: Red Hat Enterprise Linux 7 Server - Extras (RPMs)
        product: Red Hat Enterprise Linux Server
        basearch: x86_64
      - name: Red Hat Enterprise Linux 7 Server - Optional (RPMs)
        product: Red Hat Enterprise Linux Server
        basearch: x86_64
        releasever: "7Server"
      - name: Red Hat Enterprise Linux 7 Server - Supplementary (RPMs)
        product: Red Hat Enterprise Linux Server
        basearch: x86_64
        releasever: "7Server"
      - name: Red Hat Satellite Tools 6.3 - Puppet 4 (for RHEL 7 Server) (RPMs)
        product: Red Hat Enterprise Linux Server
        basearch: x86_64
      - name: Red Hat Satellite 6.3 - Puppet 4 (for RHEL 7 Server) (RPMs)
        product: Red Hat Satellite
        basearch: x86_64
      - name: Red Hat Satellite Capsule 6.3 - Puppet 4 (for RHEL 7 Server) (RPMs)
        product: Red Hat Satellite Capsule
        basearch: x86_64
      - name: Red Hat OpenShift Container Platform 3.9 (RPMs)
        product: Red Hat OpenShift Container Platform
        basearch: x86_64
      - name: Red Hat CloudForms Management Engine 5.9 (RPMs)
        product: Red Hat CloudForms
        basearch: x86_64
      - name: Red Hat Ansible Engine 2.6 RPMs for Red Hat Enterprise Linux 7 Server
        product: Red Hat Ansible Engine
        basearch: x86_64
      sync_plans:
      - name: All - Nightly
        sync_date: '00:00'
        interval: daily
        products:
        - Red Hat Enterprise Linux Server
        - Red Hat Satellite
        - Red Hat OpenShift Container Platform
        - Red Hat CloudForms
        - Red Hat Ansible Engine
  roles:
  - redhat_satellite6_organizations
```
