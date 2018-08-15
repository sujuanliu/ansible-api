# ansible-api
使用python3调用ansible API去执行ad-hoc command和playbook

# 如何调用接口去执行ansible AD-HOC command
    ansible = ansible_Runner('/etc/ansible/hosts')
    ansible.run('all', 'setup', "filter='ansible_mounts'")
    result=ansible.get_result()
    
    结果：
    {
	'success': {
		'localhost': {
			'invocation': {
				'module_args': {
					'filter': 'ansible_mounts',
					'gather_subset': ['all'],
					'fact_path': '/etc/ansible/facts.d',
					'gather_timeout': 10
				}
			},
			'ansible_facts': {
				'ansible_mounts': [{
					'block_used': 2196338,
					'uuid': '1ae5f12f-79c1-47d4-bed7-941ab9385396',
					'size_total': 42139451392,
					'block_total': 10287952,
					'mount': '/',
					'block_available': 8091614,
					'size_available': 33143250944,
					'fstype': 'ext4',
					'inode_total': 2621440,
					'options': 'rw',
					'device': '/dev/vda1',
					'inode_used': 109646,
					'block_size': 4096,
					'inode_available': 2511794
				}]
			},
			'_ansible_parsed': True,
			'_ansible_verbose_override': True,
			'_ansible_no_log': False,
			'changed': False
		}
	},
	'failed': {},
	'unreachable': {}
}
    
 # 如何调用接口执行ansible playbook
    ansible.run_playbook("xxx.yml")
    result = ansible.get_result()
    print(result)
    
    结果：
    {
	'success': {
		'localhost': {
			'changed': True,
			'end': '2018-08-15 14:28:03.239975',
			'stdout': 'iZj6cc1phkw1g99vsy7wdnZ',
			'cmd': ['hostname'],
			'rc': 0,
			'start': '2018-08-15 14:28:03.231402',
			'stderr': '',
			'delta': '0:00:00.008573',
			'invocation': {
				'module_args': {
					'creates': None,
					'executable': None,
					'_uses_shell': False,
					'_raw_params': 'hostname',
					'removes': None,
					'argv': None,
					'warn': False,
					'chdir': None,
					'stdin': None
				}
			},
			'_ansible_parsed': True,
			'stdout_lines': ['iZj6cc1phkw1g99vsy7wdnZ'],
			'stderr_lines': [],
			'_ansible_no_log': False
		}
	},
	'failed': {},
	'unreachable': {}
}
