just change nginx file


[root@STM1 html]# cat /etc/nginx/nginx.conf

    # For more information on configuration, see:
    #   * Official English Documentation: http://nginx.org/en/docs/
    #   * Official Russian Documentation: http://nginx.org/ru/docs/
    
    user nginx;
    worker_processes auto;
    error_log /var/log/nginx/error.log;
    pid /run/nginx.pid;
    
    # Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
    include /usr/share/nginx/modules/*.conf;
    
    events {
        worker_connections 1024;
    }
    
    http {
        log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                          '$status $body_bytes_sent "$http_referer" '
                          '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         on;
    keepalive_timeout   65;
    types_hash_max_size 4096;

    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    # Load modular configuration files from the /etc/nginx/conf.d directory.
    # See http://nginx.org/en/docs/ngx_core_module.html#include
    # for more information.
    include /etc/nginx/conf.d/*.conf;

    upstream hpcsa {
	server 10.10.10.129;
	server 10.10.10.132;
	}
    server {
        listen       80;
        listen       [::]:80;
        server_name  _;
        root         /usr/share/nginx/html;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

	location / {
                proxy_pass http://hpcsa/;
        }

        error_page 404 /404.html;
        location = /404.html {
        }

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
        }

    }

    # Settings for a TLS enabled server.
    #
    #    server {
    #        listen       443 ssl http2;
    #        listen       [::]:443 ssl http2;
    #        server_name  _;
    #        root         /usr/share/nginx/html;
    #
    #        ssl_certificate "/etc/pki/nginx/server.crt";
    #        ssl_certificate_key "/etc/pki/nginx/private/server.key";
    #        ssl_session_cache shared:SSL:1m;
    #        ssl_session_timeout  10m;
    #        ssl_ciphers HIGH:!aNULL:!MD5;
    #        ssl_prefer_server_ciphers on;
    #
    #        # Load configuration files for the default server block.
    #        include /etc/nginx/default.d/*.conf;
    #
    #        error_page 404 /404.html;
    #            location = /40x.html {
    #        }
    #
    #        error_page 500 502 503 504 /50x.html;
    #            location = /50x.html {
    #        }
    #    }
    
    }

[myimage](![ezgif com-video-to-gif](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/24fab9a6-0b86-4f00-8c6c-701af933b066))


# weight 3 for server 1 (linux)

	[root@STM1 html]# cat /etc/nginx/nginx.conf
	# For more information on configuration, see:
	#   * Official English Documentation: http://nginx.org/en/docs/
	#   * Official Russian Documentation: http://nginx.org/ru/docs/
	
	user nginx;
	worker_processes auto;
	error_log /var/log/nginx/error.log;
	pid /run/nginx.pid;
	
	# Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
	include /usr/share/nginx/modules/*.conf;
	
	events {
	    worker_connections 1024;
	}
	
	http {
	    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
	                      '$status $body_bytes_sent "$http_referer" '
	                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         on;
    keepalive_timeout   65;
    types_hash_max_size 4096;

    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    # Load modular configuration files from the /etc/nginx/conf.d directory.
    # See http://nginx.org/en/docs/ngx_core_module.html#include
    # for more information.
    include /etc/nginx/conf.d/*.conf;

    upstream hpcsa {
	server 10.10.10.129 weight=3;
	server 10.10.10.132;
	}
    server {
        listen       80;
        listen       [::]:80;
        server_name  _;
        root         /usr/share/nginx/html;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

	location / {
                proxy_pass http://hpcsa/;
        }

        error_page 404 /404.html;
        location = /404.html {
        }

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
        }

    }

	# Settings for a TLS enabled server.
	#
	#    server {
	#        listen       443 ssl http2;
	#        listen       [::]:443 ssl http2;
	#        server_name  _;
	#        root         /usr/share/nginx/html;
	#
	#        ssl_certificate "/etc/pki/nginx/server.crt";
	#        ssl_certificate_key "/etc/pki/nginx/private/server.key";
	#        ssl_session_cache shared:SSL:1m;
	#        ssl_session_timeout  10m;
	#        ssl_ciphers HIGH:!aNULL:!MD5;
	#        ssl_prefer_server_ciphers on;
	#
	#        # Load configuration files for the default server block.
	#        include /etc/nginx/default.d/*.conf;
	#
	#        error_page 404 /404.html;
	#            location = /40x.html {
	#        }
	#
	#        error_page 500 502 503 504 /50x.html;
	#            location = /50x.html {
	#        }
	#    }
	
	}

![ezgif com-video-to-gif (1)](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/37e4d631-e761-4139-869e-911c804c3e7d)

    
### [Nginx-Loadbalancer](https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/)



make 3 websites on windows server 
1st on 8000 for reverse proxy ip welcome to acts
2nd on 9000 /hpcsa welcome to hpcsa
3rd on 9500 /ditis welcome to ditis



#loadbalancer for 4 websites

4 websites
and 2 upstreams 

	# For more information on configuration, see:
	#   * Official English Documentation: http://nginx.org/en/docs/
	#   * Official Russian Documentation: http://nginx.org/ru/docs/
	
	user nginx;
	worker_processes auto;
	error_log /var/log/nginx/error.log;
	pid /run/nginx.pid;
	
	# Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
	include /usr/share/nginx/modules/*.conf;
	
	events {
	    worker_connections 1024;
	}
	
	http {
	    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
	                      '$status $body_bytes_sent "$http_referer" '
	                      '"$http_user_agent" "$http_x_forwarded_for"';
	
	    access_log  /var/log/nginx/access.log  main;
	
	    sendfile            on;
	    tcp_nopush          on;
	    tcp_nodelay         on;
	    keepalive_timeout   65;
	    types_hash_max_size 4096;
	
	    include             /etc/nginx/mime.types;
	    default_type        application/octet-stream;
	
	    # Load modular configuration files from the /etc/nginx/conf.d directory.
	    # See http://nginx.org/en/docs/ngx_core_module.html#include
	    # for more information.
	    include /etc/nginx/conf.d/*.conf;
		
		upstream test{
		server 10.10.10.132:8000;
		server 10.10.10.132:10000;
		}	
		
		upstream test2{
		server 10.10.10.132:9500;
		server 10.10.10.132:10100;
		}
	
	    server {
		        listen       80;
	        listen       [::]:80;
	        server_name  _;
	        root         /usr/share/nginx/html;
	
	        # Load configuration files for the default server block.
	        include /etc/nginx/default.d/*.conf;
	
		location /app1 {
	            proxy_pass http://test/;
	    	}
		
		location /app2 {
			proxy_pass http://test2/;
		}
	
		error_page 404 /404.html;
	        location = /404.html {
	        }
	
	        error_page 500 502 503 504 /50x.html;
	        location = /50x.html {
	        }
	
	    }
	
	# Settings for a TLS enabled server.
	#
	#    server {
	#        listen       443 ssl http2;
	#        listen       [::]:443 ssl http2;
	#        server_name  _;
	#        root         /usr/share/nginx/html;
	#
	#        ssl_certificate "/etc/pki/nginx/server.crt";
	#        ssl_certificate_key "/etc/pki/nginx/private/server.key";
	#        ssl_session_cache shared:SSL:1m;
	#        ssl_session_timeout  10m;
	#        ssl_ciphers HIGH:!aNULL:!MD5;
	#        ssl_prefer_server_ciphers on;
	#
	#        # Load configuration files for the default server block.
	#        include /etc/nginx/default.d/*.conf;
	#
	#        error_page 404 /404.html;
	#            location = /40x.html {
	#        }
	#
	#        error_page 500 502 503 504 /50x.html;
	#            location = /50x.html {
	#        }
	#    }
	
	}
![ezgif com-video-to-gif (4)](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/01cff2f5-73ec-4628-a8cd-3b4f1827a1c1)



