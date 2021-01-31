- name: print some facts                   
  hosts: all                          
  connection: local                        
  tasks:                                   
   - debug: var=ansible_proc_cmdline.BOOT_IMAGE

   - debug: var=ansible_env.SHELL
   - debug: var=ansible_env.PWD
   - debug: var=ansible_env.USER

   - debug: var=ansible_default_ipv4.address

   - command: cat /etc/os-release
     register: out
   - debug: var=out.stdout
     when: ansible_distribution == 'Ubuntu'

   - command: echo "hello"
     register: out
   - debug: var=out.stdout
     when: ansible_distribution == 'Redhat'
