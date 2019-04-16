# vagrant


##  销毁并清理虚拟机

```
vagrant destroy -f && rm -rf .vagrant
```

## ssh key

### Linux

```
config.ssh.insert_key = false
config.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']
  
```



```
config.ssh.insert_key = false
  config.ssh.private_key_path = ["keys/private", "~/.vagrant.d/insecure_private_key"]
  config.vm.provision "file", source: "keys/public", destination: "~/.ssh/authorized_keys"
```

### Win


```
config.ssh.insert_key = false
config.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']



C:\\Users\wei\\.vagrant.d\\insecure_private_key
  
```



# Vagrant指定 SSH key

## Linux

```
Vagrant.configure("2") do |config|
  config.ssh.private_key_path = "~/.ssh/id_rsa"
  config.ssh.forward_agent = true
end

```
## Win

```
  config.ssh.private_key_path = "C:\\Users\\grgbanking\\ssh\\vgrantKEYpass"
```


#  SSH端口写死

```

  config.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", disabled: "true"
  config.vm.network "forwarded_port", guest: 22, host: 3333
```


# vagrant box 带版本号的添加方案

## 把box文件和metadata.json文件放到一个目录，以bionic-server-cloudimg-amd64-vagrant.box为例：

metadata.json
```
{
    "name": "ubuntu/bionic64",
    "versions": [{
        "version": "20190322",
        "providers": [{
            "name": "virtualbox",
            "url": "./bionic-server-cloudimg-amd64-vagrant.box"
        }]
    }]
}

```

然后：

```
vagrant box add metadata.json
```

查看：

```
 vagrant box list

```


# box 镜像搜索

https://app.vagrantup.com/boxes/search



# Ubuntu 下载地址  

https://cloud-images.ubuntu.com/bionic/


# vagrant add box offline
```
vagrant box add box_Name xxx.box
```


##  Vagrant virtualbox 的一个可能的 BUG ！！！ 

###  设置 pulic-network bridge 的正确模式

```
 config.vm.network "public_network", :bridge => "eno1", auto_config: false
 
```


```
vagrant global-status

vboxmanage list vms

```

#### 查看虚拟机并删除之
```
vboxmanage list vms
VBoxManage unregistervm xxx-id --delete
```

## 另外一个 坑！！！   用vagrant global-status查看总是还有虚拟机入口

执行
```
 vagrant global-status --prune
```
把虚拟机入口彻底清除


## vagrant基础教程

https://www.cnblogs.com/davenkin/p/vagrant-virtualbox.html   



##  Vagrant 基础全面解析

https://www.cnblogs.com/kelsen/archive/2017/01/04/6247005.html    


##  离线安装centos镜像：


###  官网地址：     

https://app.vagrantup.com/centos/boxes/7    



###  镜像下载地址：         
https://cloud.centos.org/centos/7/vagrant/x86_64/images/     



##  注意

Ubuntu vagrant Installed Version: 1.8.1  只能和 virtaulbox 4.0, 4.1, 4.2, 4.3, 5.0 这些版本兼容   



# vagrant install k8s cluster

https://github.com/rootsongjc/kubernetes-vagrant-centos-cluster/blob/master/README-cn.md    




virtualbox download:

https://download.virtualbox.org/virtualbox   




#  vagrant video

## Vagrant Configuration
https://www.youtube.com/watch?list=PL2vfKi8eN0j72pmf3IjXhTXMXhm2LYlgz&time_continue=2&v=d3wrp2BEvuE



