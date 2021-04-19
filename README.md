# localsubnetsetd

localsubnetsetd maintains [nftables](https://nftables.org/) sets for all subnets
directly attached to the current machine. The original use case for
localsubnetsetd was to give special access to traffic on an IPv6 subnet with an
unpredictable network number (as is common with prefix delegations from consumer
ISPs). More generally, localsubnetsetd allows you to treat local network traffic
specially without involving a border firewall.

## Dependencies

localsubnetsetd is written in Python 3 and requires the nftables and pyroute2
libraries. On Debian, you want the `python3`, `python3-nftables`, and
`python3-pyroute2` packages.

## Setup

localsubnetsetd requires that `local_subnets4` and `local_subnets6` sets exist
in the `inet filter` table. Create them with

    nft add set inet filter local_subnets4 { type ipv4_addr; flags interval; }
    nft add set inet filter local_subnets6 { type ipv6_addr; flags interval; }

---

This is not an official Google product.
