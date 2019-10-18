# Chef Utils gem

**Umbrella Project**: [Chef Infra](https://github.com/chef/chef-oss-practices/blob/master/projects/chef-infra.md)

**Project State**: [Active](https://github.com/chef/chef-oss-practices/blob/master/repo-management/repo-states.md#active)

**Issues [Response Time Maximum](https://github.com/chef/chef-oss-practices/blob/master/repo-management/repo-states.md)**: 14 days

**Pull Request [Response Time Maximum](https://github.com/chef/chef-oss-practices/blob/master/repo-management/repo-states.md)**: 14 days

## Getting Started

Chef Utils gem is common code and mixins for the core Chef Infra ruby gems.

### Platform Helpers

Individual platforms for when code MUST be different on a case-by-case basis.  It is generally encouraged to not use these and to use
the `platform_family` helpers unless it is known that code must be special cased for individual platforms.

* `centos?`
* `clearos?`
* `linuxmint?`
* `nexentacore?`
* `omnios?`
* `openindiana?`
* `opensolaris?`
* `opensuse?`
* `oracle?`
* `raspbian?`
* `redhat?`
* `scientific?`
* `ubuntu?`

For when there is a namespace collision between a platform and a platform family, the platform helper gains a `_platform?` suffix (which encourages
the use of the shorter form of the platform family helper).  So the debian platform family is `debian?` while the debian platform is `debian_platform?`
here.  Many of these are included for API consistency and completeness where the difference between `amazon?` and `amazon_platform?` does not matter
because there is only one platform in the platform family so the results are the same.  Users are highly encouraged to use the shorter platform family
style over the platform-specific ones here.

* `aix_platform?`
* `amazon_platform?`
* `arch_platform?`
* `debian_platform?`
* `dragonfly_platform?`
* `fedora_platform?`
* `freebsd_platform?`
* `gentoo_platform?`
* `mac_os_x_platform?`
* `netbsd_platform?`
* `openbsd_platform?`
* `slackware_platform?`
* `smartos_platform?`
* `solaris2_platform?`
* `suse_platform?`
* `windows_platform?`

### Platform Family Helpers

These should be the most commonly used helpers to identify the type of node which group somewhat similar or nearly identical types of platforms.
There are helpers here which are also meta-families which group together multiple types into supertypes.

* `aix?`
* `amazon?`
* `arch?`
* `debian?`
* `dragonflybsd?`
* `fedora?`
* `freebsd?`
* `gentoo?`
* `mac_os_x?`
* `netbsd?`
* `openbsd?`
* `rhel?`
* `smartos?`
* `solaris2?`
* `suse?`
* `windows?`

Super Families:

* `redhat_based?` - rhel, fedora and derivaties (including pidora, but not including amazon)
* `fedora_derived?` - `redhat_based` systems and including amazon, anything of fedora lineage
* `rpm_based?`- all `fedora_derived` systems and anything using RPM (although excluding AIX)
* `solaris_based?`- all solaris-derived systems (opensolaris, nexentacore, omnios, smartos, etc)
* `bsd_based?`- all bsd-derived systems (freebsd, netbsd, openbsd, dragonflybsd).

### OS Helpers

OS helpers are only provided for OS types that contain multiple platform families ("linux"), or for unique OS values ("darwin").  Users should
use the Platform Family helper level instead.

* linux?
* darwin?

### Architecture Helpers

* `_64_bit?`
* `_32_bit?`
* `i386?`
* `intel?`
* `sparc?`
* `ppc64?`
* `ppc64le?`
* `powerpc?`
* `armhf?`
* `s390x?`
* `s390?`

### Train Helpers

* `file_exist?`
* `file_open`

### Introspection Helpers

* `docker?` - if the node is running inside of docker
* `systemd?` - if the init system is systemd
* `kitchen?` - if ENV['TEST_KITCHEN'] is set
* `ci?` - if ENV['CI'] is set

### Service Helpers

* `debianrcd?` - if the `update-rc.d` binary is present
* `invokercd?` - if the `invoke-rc.d` binary is present
* `upstart?` - if the `initctl` binary is present
* `insserv?` - if the `insserv` binary is present
* `redhatrcd?` - if the `chkconfig` binary is present

* `service_script_exist?(type, service)`

### Which/Where Helpers

### Path Sanity Helpers

## Getting Involved

We'd love to have your help developing Chef Infra. See our [Contributing Document](./CONTRIBUTING.md) for more information on getting started.

## License and Copyright

Copyright 2008-2019, Chef Software, Inc.

```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
