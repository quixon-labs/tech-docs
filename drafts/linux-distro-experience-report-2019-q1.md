# Experience Report: Linux distributions

## Current Bias: Ubuntu LTS

### Background

RHEL/CentOS and Ubuntu arguably hold the largest Linux market. Here are some of observations from using them as both production system as well as daily driver dev systems, across different companies. There's also openSUSE/SLES, however it's experience is largely similar to the RH family these days, and while YaST and zypper are fantastic, it's simpler to stick to RH track record and market share.

While dev systems and production server need not be on the same base, there is a definite productivity boost being so, avoiding another cognitive switch and captializing on in-depth experience and exposure surface in dealing with corner cases.

### CentOS/RHEL + Fedora

- More thoughtful architecture, and polished experience as expected from the RedHat family of products (Eg: systemd, selinux, firewalld, consistent profile.d scripts and bash startup sequencing, semantic vte patches etc)
- Fedora leads innovation with the most recent packages.
Stays closer to upstream, and has a reputation of working with upstream rather than patching source with controversial behaviour.
- dnf is a great package manger with better transactions, history, delta rpms, plugin architecture etc, coupled with rpm's finer packaging details like checksums, modification checks, with single command "rpm -Va", etc.
- Tries to do the right thing vs. easy. (firewalld, selinux, to minor packing details like docker default config etc)
- Doesn't provide a great arm story on dev systems. - Doesn't have a great multi-arch story in general with FHS3.0, as opposed to Debian's multi-arch.
- Doesn't have a specific IoT strategy. 
- RHEL8 has interesting changes deprecating KDE, OpenLDAP, etc which raises questions. 
- IBM acquisition and questionable OSS direction.
fedora-devel and contributing back is great with standard git based workflows, pagure, bodhi, copr, etc.
- In the last decade, Fedora's plymouth is the only implementation that I've seen work as intended providing a polished boot experience including minor details like dropping off branding on it's grub2 config keeping it minimal. This speaks of RedHat's quality finish and attention to detail, where Ubuntu/Debian has always been filled with flickery boots, buggy plymouth and superfluous branding elements.

### Ubuntu

- Debian goodness.
- apparmor: While selinux is arguably more secure with more granular control, apparmour's simplicity and selective targeting in practise results in good opt-in security with higher productivity. I've also never liked selinux context labels. 
- Debian testing (LTS)/unstable base. Great scale-able multi-arch story inheriting Debian's multi-arch (/lib/${arch-triplet} architecture).
- Has a good arm dev story with dpkg multi architecture. A simple "dpkg --add-architecture armhf/aarch64" should do the trick for arm (eg: android) targeting
- snapd - while snapd started with controversial development and flatpak providing a better desktop packaging story - snap is just fantastic for the IoT space. 
- With IoT as a part of our core strategy, Ubuntu Core with snaps seem to be a good overall strategy. Other options like RancherOS, CoreOS still only focuses on server specific workloads.
- Desktop focus on Ubuntu is arguably better. However Fedora has caught up, if not even more polished off late. But small little things like better wireless printing out of the box, default swap file rationale, udev rules integration, apparmor, etc makes it a little nicer for desktop than it's counterparts.  
- Canonical simply doesn't have the end-to-end expertise equivalent to RedHat who does the largest kernel dev, and leads the linux innovation space, with far better architecture and design perspective across multiple domains.
- Thankfully, a great deal of the Linux ecosystem has converged under systemd and gnome-shell desktop environments, mitigating Canonical's shortcomings above.
Ubuntu has the largest mind-share, and more often than not has easier access to dev packages, thanks to Debian repositories, and Canonical's marketing and targeted partnerships.
- Canonical has had a reputation of just patching instead of working with upstream. However, it's worth mentioning there are some indications of this improving off late.
- Ubuntu tends to have subtle, non-obvious modifications to upstream behaviour that in many instances causes more caveats to be aware of, making it more tedious than solving problems with upstream solutions.
- ubuntu-dev and contributing back is inconvenient with bazaar and launchpad, instead of standard git based workflows that simplify learning curves.

### Debian

- Debian provides most of the goodness that Ubuntu sits on top of, without some of Ubuntu's disadvantages. 
- On IoT, Ubuntu Core with snap offers the best off the shelf solution providing security updates for kernel and hardware support as snaps independent of the application, cognitively similar to container based layers. So, Ubuntu is a natural fit.
- On desktop environments, Debian Stable is not an option. While Debian Testing fares better, it suffers from long period of being stale during the testing branch freeze period in it's lifecycle. Ubuntu mitigates this by picking from unstable for non-LTS, and testing for LTS. And it's always nice to have parity among dev and production environments.
- On server environments, Debian is arguably a better option when compared against Ubuntu, but since we dockerize everything, and the docker base can be Debian, picking Ubuntu here makes sense as well, since it has the option of commercial support and the base packages are more up-to-date just as long as we stick to Canonical supported  repositories (i.e, Main repository only for the most part). This let's us achieve the best of both worlds.

## Inference

First, since all our services are dockerized anyway, we might as well do RancherOS or CoreOS at a later point for server environments. If at all needed, we have LXC for clean OS based workloads without complete virtualization. So, with docker and LXC combo, we never need to worry about the base OS there.

With that in mind, using Ubuntu LTS as the base system today for server workloads with a mix of Debian and Alpine based docker containers for server workloads and Ubuntu Core for IoT, and the latest (not only LTS) Ubuntu for dev systems seem to be a good overall balance, with it's negative aspects manageable. 
