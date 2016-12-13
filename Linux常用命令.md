ssh -T git@139.199.5.18  # 测试目标服务是否可用，返回用户名ssh协议即可用

ssh -i "/home/mike/.centos/centos_id_rsa" root@139.199.5.18


scp -rp -i /home/mike/.centos/centos_id_rsa /home/mike/* root@139.199.5.18:/root/
