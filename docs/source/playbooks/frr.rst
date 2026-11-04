==============
Playbook - frr
==============

FRR's configuration directory is stored on the host at
``{{ edpm_frr_config_basedir }}/etc/frr`` (by default,
``/var/lib/openstack/frr/etc/frr``) and mounted read/write in the container.
Changes saved by FRR persist across container restarts. Running the role again
regenerates ``frr.conf`` from the role's variables and can overwrite changes
made by FRR. Custom ``edpm_frr_volumes`` must include this writable mount.

On an existing deployment, changes saved only inside the old container are
not present in the host configuration directory. Back up any such changes
before redeploying the role, which replaces the container with the new mount,
and reapply them afterward.

.. literalinclude:: ../../../playbooks/frr.yml
   :language: YAML
