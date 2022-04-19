# Dark-Mode-Radarr
A Dark Theme for Radarr v.4.1.0.6175+ implemented via Nginx Reverse proxy and its sub_filter module.

## Gallery
[![Movies](http://ibb.co/yNCM9MK "Movies")](http://http://ibb.co/yNCM9MK "Movies")[![Discover](http://ibb.co/0BdJ9LY "Discover")](http:/http://ibb.co/0BdJ9LY/ "Discover")[![Calendar](http://ibb.co/YkPgzFY "Calendar")](http://http://ibb.co/YkPgzFY "Calendar")[![Profiles](http://ibb.co/34B0NzF "Profiles")](http://http://ibb.co/34B0NzF "Profiles")[![Quality](http://ibb.co/h13MBDW "Quality")](http://http://ibb.co/h13MBDW "Quality")

## Assumptions
- You have an instance of Radarr v.4.1.0.6175 or more recent :smile:
- You access your instance of Radarr via NGINX reverse proxy
- Your instance of NGINX has the HTTPS Subs Filter module (libnginx-mod-http-subs-filter) installed. Or you can installed in on your distro.

### Installation
Note: Instructions are for Debian (bionic). Modify the instructions to reflect the distro you're operating on.

1. Open a terminal session on your NGINX host

	a. Check if the **NGINX HTTPS Subs Filter** module (libnginx-mod-http-subs-filter) is installed. 
    
    	sudo dpkg -s libnginx-mod-http-subs-filter
        
	About two or three lines down you should have output that indicates that the module is ***installed***

	b.  If not installed, install it by running the following and then restarting NGINX...
    
    	sudo apt-get install -y libnginx-mod-http-subs-filter

	c. Modify the `/etc/nginx/sites-available/reverse` file and add the following to the location block of your Radarr instance.
	```bash
    	sub_filter
     		'</head>'
     		'<link rel="stylesheet" type="text/css" href="//radarr:7878/Content/dark-radarr.css">
     		</head>';
    	sub_filter_once on;
	```
	Note: Once added restart NGINX. Here **`radarr`** is the hostname of the host that is running Radarr. We will be adding the `dark-radarr.css` file to your instance of Radarr at `./Radarr/UI/Content/`. 

2. Open a terminal on the host running Radarr. Download the dark-mode.css file and uploaded it to the Radarr host in the location relative to your installation of Radarr. Like, `/app/Radarr/UI/Content` or `/Radarr/UI/Content`.

3. Verify that you can access http://radarr:7878/Content/dark-radarr.css 
(substitute radarr for the hostname of the host running Radarr)

4. If Step #3 is successful access Radarr via your reverse proxy URL (NGINX). For example, http://www.example.net/radarr/

## Enjoy
