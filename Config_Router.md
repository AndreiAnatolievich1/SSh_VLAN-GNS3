
`router> en` <br>
`router# conf t` <br>
`router(config)# enable secret cisco` <br>
`router(config)# service password-encryption`  <br>
`router(config)# hostname router1`  <br>
`router1(config)# username admin_R privilege 15 secret cisco` <br>
`router1(config)# line console 0`  <br>
`router1(config-line)#en` <br>
`router1(config)# line vty 0 15` <br>
`router1(config-line)# transport input ssh` <br>
`router1(config-line)# en` <br>
`router1(config)#ip domain-name test.local`  <br>
`router1(config)#crypto key generate rsa general-keys modulus 2048`  <br>
`router1(config)# int g1/0`  <br>
`router1(config-if)# no shutdown`  <br>
`router1(config-if)#ex` <br>
`router1(config)# int g1/0.10` <br>
`router1(config-subif)# encapsulation dot1Q 10` <br>
`router1(config-subif)#ip addr 192.168.10.1 255.255.255.0` <br>
`router1(config-subif)# ip nat inside` <br>
`router1(config-subif)#ex` <br>
`router1(config)# int g1/0.20` <br>
`router1(config-subif)# encapsulation dot1Q 20` <br>
`router1(config-subif)#ip addr 192.168.20.1 255.255.255.0` <br>
`router1(config-subif)# ip helper-address 192.168.102.2` <br>
`router1(config-subif)# ip nat inside` <br>
`router1(config-subif)#ex` <br>
`router1(config)# int g1/0.30` <br>
`router1(config-subif)# encapsulation dot1Q 30` <br>
`router1(config-subif)#ip addr 192.168.30.1 255.255.255.0` <br>
`router1(config-subif)# ip helper-address 192.168.102.2` <br>
`router1(config-subif)# ip nat inside` <br>
`router1(config-subif)#ex` <br>
`router1(config)# int f0/0` <br>
`router1(config-if)# no shutdown` <br>
`router1(config-if)#ip addr dhcp` **указываем что интерфейс получает адрес по dhcp** <br>
`router1(config-if)# ip nat outside` <br>
`router1(config-if)#ex` <br>
`router1(config)# access-list 1 permit 192.168.10.0 0.0.0.255`  <br>
`router1(config)# access-list 1 permit 192.168.20.0 0.0.0.255` <br>
`router1(config)# access-list 1 permit 192.168.30.0 0.0.0.255` <br>
`router1(config)# ip nat inside source list 1 interface f0/0 overload`  <br>
`router1(config)# ip routing` <br>
