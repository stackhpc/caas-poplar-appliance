# caas-poplar-appliance

This repository contains the configuration to stand-up a Poplar instance in the Azimuth self service portal. It was forked from [caas-workstation](https://github.com/stackhpc/caas-workstation.git), which originates with StackHPC, the developers of Azimuth.

Requires the following configuration:

```
azimuth_caas_awx_extra_projects:
  - # The name of the appliance project in AWX
    name: Graphcore Poplar Applicance
    # The git URL of the appliance
    gitUrl: https://github.com/graphcore/caas-poplar-appliance.git
    # The branch, tag or commit id to use
    # For production, it is recommended to use a fixed tag or commit ID
    gitVersion: main
    # The base URL for cluster metadata files
    metadataRoot: https://raw.githubusercontent.com/graphcore/caas-poplar-appliance/{gitVersion}/ui-meta
    # List of playbooks that correspond to appliances
    playbooks: [poplar-appliance.yml]
    # Dict of extra variables for appliances
    #   The keys are the playbooks
    #   The values are maps of Ansible extra_vars for those playbooks
    #   The special key __ALL__ can be used to set common extra_vars for
    #     all playbooks in a project
    extraVars:
      __ALL__:
        # Use the ID of an Ubuntu 20.04 image that we asked azimuth-ops to upload
        # TBC:
        cluster_image: "{{ community_images_image_ids.ubuntu20.04-poplar }}"
```
