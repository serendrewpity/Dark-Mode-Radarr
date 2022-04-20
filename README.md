# Dark-Mode-Radarr
A Dark Theme for Radarr v.4.1.0.6175+ implemented via Nginx Reverse proxy and its sub_filter module.
[![Movies](https://i.ibb.co/tH6NGNn/2022-04-19-7-53-13.jpg "Movies")](http://https://i.ibb.co/tH6NGNn/2022-04-19-7-53-13.jpg "Movies")

## Assumptions
- You have an instance of Radarr v.4.1.0.6175 or more recent :smile:
- You access your instance of Radarr via NGINX reverse proxy
- Your instance of NGINX has the HTTPS Subs Filter module (libnginx-mod-http-subs-filter) installed. Or you can installed in on your distro.
- Alternatively, if you do not have NGINX reverse proxy then you can install the **Stylus** browser extension ([Chrome](http://https://chrome.google.com/webstore/detail/stylus/clngdbkpkpeebahjckkjfobafhncgmne?hl=en "Chrome") or [Firefox](https://addons.mozilla.org/en-US/firefox/addon/styl-us/ "Firefox")) and import the custom CSS Code as a [UserStyles](https://userstyles.world/ "UserStyles") or Stylish

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
    	proxy_set_header Accept-Encoding "";
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

## Gallery
[![Movies](https://i.ibb.co/tH6NGNn/2022-04-19-7-53-13.jpg "Movies")](http://https://i.ibb.co/tH6NGNn/2022-04-19-7-53-13.jpg "Movies")[![Discover](https://i.ibb.co/fMM0jD9/2022-04-19-9-42-22.jpg "Discover")](http://https://i.ibb.co/fMM0jD9/2022-04-19-9-42-22.jpg "Discover")[![Calendar](https://i.ibb.co/VSJ67cr/2022-04-19-7-54-27.jpg "Calendar")](http://https://i.ibb.co/VSJ67cr/2022-04-19-7-54-27.jpg "Calendar")[![Profiles](https://i.ibb.co/bQzrBJv/2022-04-19-7-53-01.jpg "Profiles")](http://https://i.ibb.co/bQzrBJv/2022-04-19-7-53-01.jpg "Profiles")[![Quality](https://i.ibb.co/fGjSk4p/2022-04-19-7-55-29.jpg "Quality")](http://https://i.ibb.co/fGjSk4p/2022-04-19-7-55-29.jpg "Quality")
