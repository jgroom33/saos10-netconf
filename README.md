# saos10-netconf

This repository cointains config example for provisioning services and golden configs on:
* 5170 probably
* 5164s

## Requirements

* Ansible

### Copy config files to/from devices

```bash
# Download running config
scp diag@10.92.44.150:/mnt/config/ciena-cfg.xml 5144-1.xml
# Push config file
scp 5144-1.xml diag@10.92.44.150:/home/diag/foo.xml
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<config
  xmlns:ncx="http://netconfcentral.org/ns/yuma-ncx"
  ncx:last-modified="2022-08-24T17:10:10Z" ncx:etag="8"
  xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
  <cfm-global-config xmlns="urn:ciena:params:xml:ns:yang:ciena-pn:ciena-cfm">
    <admin-state>disable</admin-state>
  </cfm-global-config>
  <classifiers xmlns="urn:ciena:params:xml:ns:yang:ciena-pn::ciena-mef-classifier">
    <classifier>
      <name>Untagged</name>
      <filter-entry>
        <filter-parameter
          xmlns:classifier="urn:ciena:params:xml:ns:yang:ciena-pn::ciena-mef-classifier">classifier:vtag-stack</filter-parameter>
        <untagged-exclude-priority-tagged>true</untagged-exclude-priority-tagged>
      </filter-entry>
    </classifier>
  </classifiers>
  <components xmlns="http://openconfig.net/yang/platform">
    <component>
```

```bash
ansible provision.xml
```
