### Doc 
https://www.juniper.net/documentation/en_US/junos/information-products/pathway-pages/rest-api/rest-api.pdf 

### how to get the equivalent rpc of a Junos show command

To get the equivalent rpc of ```show version```:

```
lab@spine-03> show version | display xml rpc
<rpc-reply xmlns:junos="http://xml.juniper.net/junos/17.3R1/junos">
    <rpc>
        <get-software-information>
        </get-software-information>
    </rpc>
    <cli>
        <banner></banner>
    </cli>
</rpc-reply>
```

Some show commands use arguments, so the equivalents rpc require arguments:  

To get the equivalent rpc of ```show chassis hardware clei-models```

```
pytraining@mx80-17> show chassis hardware clei-models | display xml rpc 
<rpc-reply xmlns:junos="http://xml.juniper.net/junos/17.2R1/junos">
    <rpc>
        <get-chassis-inventory>
                <clei-models/>
        </get-chassis-inventory>
    </rpc>
    <cli>
        <banner></banner>
    </cli>
</rpc-reply>
pytraining@mx80-17> 
```

To get the equivalent rpc for ```show route receive-protocol bgp 192.168.10.4 active-path hidden```
```
pytraining@newhostname> show route receive-protocol bgp 192.168.10.4 active-path hidden | display xml rpc    
<rpc-reply xmlns:junos="http://xml.juniper.net/junos/12.3R11/junos">
    <rpc>
        <get-route-information>
                <active-path/>
                <bgp/>
                <peer>192.168.10.4</peer>
                <hidden/>
        </get-route-information>
         </rpc>
        <cli>
            <banner>{master:0}</banner>
        </cli>
    </rpc-reply>

{master:0}
pytraining@newhostname> exit 

Connection to 172.30.179.107 closed.
```
