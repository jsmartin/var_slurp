	inventory/
	|-- host_vars
	|   |-- myhost1
	|   `-- myhost2
	`-- hosts


	cat inventory/host_vars/myhost1 
	name: myhost1
	ip: 1.1.1.1
	
	cat inventory/host_vars/myhost2
	name: myhost2
	ip: 2.2.2.2


    ansible-playbook book.yml -i inventory/hosts -v --limit 127.0.0.1


	PLAY [localhost] ************************************************************** 
	
	TASK: [var_slurp inv_path=/Users/jmartin/work/scrap/vars/inventory] *********** 
	ok: [127.0.0.1] => {"ansible_facts": {"slurped_vars": [{"myhost1": {"ip": "1.1.1.1", "name": "myhost1"}}, {"myhost2": {"ip": "2.2.2.2", "name": "myhost2"}}]}, "changed": false}
	
	TASK: [template src=hosts.j2 dest=/tmp/hosts] ********************************* 
	changed: [127.0.0.1] => {"changed": true, "dest": "/tmp/hosts", "gid": 20, "group": "staff", "md5sum": "0a47bb6e4c59adbfdc2bf3837f76f19a", "mode": "0644", "owner": "jmartin", "size": 235, "src": "/Users/jmartin/.ansible/tmp/ansible-tmp-1395958117.18-229681095630211/source", "state": "file", "uid": 501}
	
	PLAY RECAP ******************************************************************** 
	127.0.0.1                  : ok=2    changed=1    unreachable=0    failed=0   
	
	
	cat /tmp/hosts 
	# Ansible managed: /Users/jmartin/work/scrap/vars/hosts.j2 modified on 2014-03-27 18:08:34 by jmartin on jamess-air
	127.0.0.1   localhost localhost.localdomain
	 
	# Individual private IP machine routes
	1.1.1.1  myhost1
	2.2.2.2  myhost2