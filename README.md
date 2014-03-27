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
	ok: [127.0.0.1] => {"ansible_facts": {"slurped_vars": [{"ip": "1.1.1.1", "name": "myhost1"}, {"ip": "2.2.2.2", "name": "myhost2"}]}, "changed": false}
	
	PLAY RECAP ******************************************************************** 
	127.0.0.1                  : ok=1    changed=0    unreachable=0    failed=0   