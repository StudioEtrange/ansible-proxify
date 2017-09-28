studioetrange.proxify
=========

Role for configuring a bunch of things for network HTTP/FTP proxies.

Role Variables
--------------




```yml
proxy_env :
  http_proxy : http proxy
  https_proxy : https proxy
  ftp_proxy : ftp proxy
  no_proxy : no proxy
  proxify_dockerd : true|false -- Default value is false. Configure docker daemon with proxy
```

See also [defaults/main.yml](defaults/main.yml).


Dependencies
------------

None


Example Playbook
----------------

```yml
- hosts: servers
  roles:
    - role: studioetrange.proxify
      proxy_env :
        http_proxy : 'http://foo.bar:3128'
        https_proxy : 'http://foo.bar:3128'
        ftp_proxy : ''
        no_proxy : '127.0.0.1,localhost'
```

Inject proxy into docker daemon conf

```yml
- hosts: servers
  roles:
    - role: studioetrange.proxify
      proxy_env :
        http_proxy : 'http://foo.bar:3128'
        https_proxy : 'http://foo.bar:3128'
        ftp_proxy : ''
        no_proxy : '127.0.0.1,localhost'
        proxify_dockerd : true
```

Testing
-------
For development, we use Vagrant.

```
git clone https://github.com/StudioEtrange/ansible-proxify studioetrange.docker
```


License
-------

MIT

Author Information
------------------

This is a fork of Andrew Rothstein's work <andrew.rothstein@gmail.com> https://github.com/andrewrothstein/ansible-proxify
