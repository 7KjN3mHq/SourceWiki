# pssh && pdsh

## pssh

pssh��һ��python��д�����ڶ�̨��������ִ������Ĺ��ߣ�ͬʱ֧�ֿ����ļ�����ͬ�๤���кܳ�ɫ�ģ�����pdsh ��Ϊ���������ʹ��ǰ���ڸ��������������ú���Կ��֤���ʡ���Ŀ��ַ: [parallel-ssh](https://code.google.com/p/parallel-ssh/)

### ��װ

``` bash
wget http://parallel-ssh.googlecode.com/files/pssh-2.3.1.tar.gz
tar zxvf pssh-2.3.1.tar.gz
cd pssh-2.3.1/
python setup.py install
```

### pssh��ز���

* pssh�ڶ�������ϲ��е���������
   * -h ִ�������Զ�������б�,�ļ����ݸ�ʽ[user@]host[:port]
   		* �� test@172.16.10.10:229
   * -H ִ������������������ʽ user@ip:port 
   * -l Զ�̻������û���
   * -p һ����������������
   * -P ִ��ʱ���ִ����Ϣ
   * -o ��������ض���һ���ļ�
   * -e ִ�д����ض���һ���ļ�
   * -t ��������ִ�г�ʱʱ��
   * -A ��ʾ�������벢�Ұ����봫�ݸ�ssh(���˽ԿҲ������Ҳ���������)
   * -O ����sshһЩѡ��
   * -x ����ssh�����һЩ���������Զ������ͬ������ո�ֿ�
   * -X ͬ-x,����ֻ������һ������
   * -i ��ʾ��׼����ͱ�׼������ÿ̨hostִ����Ϻ�

### ���ӹ���

*	pscp �����ļ������hosts������scp
	* pscp -h hosts.txt -l irb2 foo.txt /home/irb2/foo.txt
*	pslurp �Ӷ�̨Զ�̻��������ļ�������
*	pnuke ������Զ������ɱ����
	* pnuke -h hosts.txt -l irb2 java
*	prsync ʹ��rsyncЭ��ӱ��ؼ����ͬ����Զ������
	* prsync -r -h hosts.txt -l irb2 foo /home/irb2/foo

### ʹ��ʵ��

д���������ļ��У��﷨Ϊ`�û���@����ip`

``` bash
$ cat host.txt 
root@192.168.230.128
wul@10.0.0.8
```

�Ƽ�ʹ��`-i`ѡ�������Ϣ������`-P`ѡ�`-h`ָ������������

``` bash
$ pssh -i -h host.txt 'date'
[1] 16:32:38 [SUCCESS] root@192.168.230.128
Mon Aug 12 16:32:38 CST 2013
[2] 16:32:38 [SUCCESS] wul@10.0.0.8
Mon Aug 12 16:32:38 CST 2013
```

`-x`ѡ�ָ��ssh��һЩ����ѡ��

``` bash
$ pssh -x '-t -t -o StrictHostKeyChecking=no' -i -h host.txt date
[1] 17:20:01 [SUCCESS] root@192.168.230.128
Mon Aug 12 17:20:01 CST 2013
Stderr: Connection to 192.168.230.128 closed.
[2] 17:20:01 [SUCCESS] wul@10.0.0.8
Mon Aug 12 17:20:01 CST 2013
Stderr: Connection to 10.0.0.8 closed.
```

`-H`ѡ�ָ����������

``` bash
$ pssh -x '-t -t -o StrictHostKeyChecking=no' -i -H 192.168.230.128 -H wul@10.0.0.8 date
[1] 17:22:58 [SUCCESS] 192.168.230.128
Mon Aug 12 17:22:58 CST 2013
Stderr: Connection to 192.168.230.128 closed.
[2] 17:22:58 [SUCCESS] wul@10.0.0.8
Mon Aug 12 17:22:58 CST 2013
Stderr: Connection to 10.0.0.8 closed.
```

### �ο��ĵ�

* [pssh](http://linux.die.net/man/1/pssh) 
* [pssh-howto](http://www.theether.org/pssh/docs/0.2.3/pssh-HOWTO.html)

## pdsh 

pdsh(Parallel Distributed SHell)�ɲ��е�ִ�ж�Ŀ�������Ĳ�������������ִ������ͷַ������кܴ�İ�������ʹ��ǰ��Ҫ����ssh�������¼��[�������](http://sourceforge.net/projects/pdsh/)


### pdsh�����÷�

``` bash
 pdsh -h
Usage: pdsh [-options] command ...
-S                return largest of remote command return values
-h                output usage menu and quit                ��ȡ����
-V                output version information and quit       �鿴�汾
-q                list the option settings and quit         �г�pdshִ�е�һЩ��Ϣ
-b                disable ^C status feature (batch mode)
-d                enable extra debug information from ^C status
-l user           execute remote commands as user           ָ��Զ��ʹ�õ��û�
-t seconds        set connect timeout (default is 10 sec)   ָ����ʱʱ��
-u seconds        set command timeout (no default)          ����-t
-f n              use fanout of n nodes                     ����ͬʱ���ӵ�Ŀ�������ĸ���
-w host,host,...  set target node list on command line      ָ��������host������������Ҳ������ip
-x host,host,...  set node exclusion list on command line   �ų�ĳЩ����ĳ������
-R name           set rcmd module to name                   ָ��rcmd��ģ������Ĭ��ʹ��ssh
-N                disable hostname: labels on output lines  �������ʾ����������ip
-L                list info on all loaded modules and exit  �г�pdsh���ص�ģ����Ϣ
-a                target all nodes                          ָ�����еĽڵ�
-g groupname      target hosts in dsh group "groupname"     ָ��dsh����
-X groupname      exclude hosts in dsh group "groupname"    �ų��飬һ���-a����
available rcmd modules: exec,xcpu,ssh (default: ssh)        ���õ�ִ������ģ�飬Ĭ��Ϊssh
```

### ʹ��ʵ��

#### ������������

``` bash
$ pdsh -w 192.168.0.231 -l root uptime
192.168.0.231:  16:16:11 up 32 days, 22:14, ? users,  load average: 0.10, 0.14, 0.16
```

#### �����������

``` bash
$ pdsh -w 192.168.0.[231-233] -l root uptime
192.168.0.233:  16:17:05 up 32 days, 22:17, ? users,  load average: 0.13, 0.12, 0.10
192.168.0.232:  16:17:05 up 32 days, 22:17, ? users,  load average: 0.45, 0.34, 0.27
192.168.0.231:  16:17:06 up 32 days, 22:15, ? users,  load average: 0.09, 0.13, 0.15
```

#### ���ŷָ�����

``` bash
$ pdsh -w 192.168.0.231,192.168.0.234 -l root uptime
192.168.0.234:  16:19:44 up 32 days, 22:19, ? users,  load average: 0.17, 0.21, 0.20
192.168.0.231:  16:19:44 up 32 days, 22:17, ? users,  load average: 0.29, 0.18, 0.16
```

#### `-x`�ų�ĳ������

``` bash
$ pdsh -w 192.168.0.[231-233] -x 192.168.0.232 -l root uptime
192.168.0.233:  16:18:24 up 32 days, 22:19, ? users,  load average: 0.11, 0.12, 0.09
192.168.0.231:  16:18:25 up 32 days, 22:16, ? users,  load average: 0.11, 0.13, 0.15
```

#### ������
  
����-g�飬�Ѷ�Ӧ������д�뵽`/etc/dsh/group/`��`~/.dsh/group/`Ŀ¼�µ��ļ��м��ɣ��ļ������Ƕ�Ӧ����

``` bash
$ cat ~/.dsh/group/dsh-test 
192.168.0.231
192.168.0.232
192.168.0.233
192.168.0.234
```

``` bash
$ pdsh -g dsh-test -l root uptime
192.168.0.232:  16:21:38 up 32 days, 22:22, ? users,  load average: 0.01, 0.15, 0.21
192.168.0.231:  16:21:38 up 32 days, 22:19, ? users,  load average: 0.17, 0.16, 0.16
192.168.0.234:  16:21:39 up 32 days, 22:21, ? users,  load average: 0.15, 0.19, 0.19
192.168.0.233:  16:21:40 up 32 days, 22:22, ? users,  load average: 0.15, 0.15, 0.10
```

#### `dshbak`��ʽ�����

pdsh��ȱʡ�����ʽΪ�������Ӹ�������������������������ʱ��Ƚϻ��ң����Բ���`dshbak`��һЩ��ʽ�����������������

``` bash
$ pdsh -g dsh-test -l root 'date'       #�鿴��Щ����ʱ�䲻һ��������һ�࣬�ɶ��Բ�ǿ
192.168.0.232: Wed Jun 19 16:24:40 CST 2013
192.168.0.231: Wed Jun 19 16:24:40 CST 2013
192.168.0.234: Wed Jun 19 16:24:40 CST 2013
192.168.0.233: Wed Jun 19 16:24:40 CST 2013
```

ʹ��dshbak֮��ɶ��Ա�ú��˺ܶ�

``` bash
$ pdsh -g dsh-test -l root 'date' | dshbak -c  
----------------
192.168.0.[231-232,234]
----------------
Wed Jun 19 16:24:18 CST 2013
----------------
192.168.0.233
----------------
Wed Jun 19 16:24:19 CST 2013
```

### �ο��ĵ�

* [Using PDSH](https://code.google.com/p/pdsh/wiki/UsingPDSH)