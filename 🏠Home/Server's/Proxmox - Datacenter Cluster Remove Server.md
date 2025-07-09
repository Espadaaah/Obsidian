# 1. default way
	pvecm nodes
	pvecm delnode pve02 <-> "pve u want to remove"
# 2. Manual remove
	nano /etc/pve/corosync.cond
		(remove the config of pve u want to remove)
	systemctl restart corosync
