# Terraform Inventory
Terraform Inventory is a tool that generate an Ansible inventory based on a Terraform deployment.

### Installation from binary
You can download the released [binaries](https://github.com/rasta-rocket/terraform-inventory/releases) and put it in your system PATH.

```
$ wget https://github.com/rasta-rocket/terraform-inventory/releases/download/<LATEST_VERSION>/terraform-inventory_linux_x64.tar.gz
$ tar -xzf terraform-inventory_linux_x64.tar.gz
$ sudo cp terraform-inventory /opt
$ export PATH=$PATH:/opt
$ terraform-inventory --help
```

### Installation from source
[Go](https://golang.org/) and [dep](https://github.com/golang/dep) are required to build this tool.
Then install terraform-inventory from github sources.

```
$ cd $GOPATH/src
$ git clone https://github.com/rasta-rocket/terraform-inventory github.com/rasta-rocket/terraform-inventory
$ cd github.com/rasta-rocket/terraform-inventory
$ dep ensure
$ go install
```

### Usage
Basic usage:
```
$ terraform apply
$ terraform-inventory -u <ssh_user> -k <ssh_key>
? Choose a bastion :
❯ e1b52c07-8a75-4527-b43f-850aaec4c3ef     bastion_0                      172.16.1.23
Inventory file is configured with 172.16.1.23 as bastion (ssh-proxy)
$ cat hosts
$ ansible -m ping all
```
You can also force the bastion IP you want to use:
```
$ terraform apply
$ terraform-inventory -u <ssh_user> -k <ssh_key> --bastion 172.16.1.25
Inventory file is configured with 172.16.1.25 as bastion (ssh-proxy)
$ cat hosts
$ ansible -m ping all
```
