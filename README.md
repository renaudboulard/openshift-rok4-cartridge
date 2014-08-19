## Openshift Rok4 Cartridge

A cartridge for openshift that enables Rok4.
It also runs the nginx server from gsterjov

Rok4 is a open source WMS/WMTS serveur, write in C++ allowing the diffusion of geo-referenced image data.
Developed by teams [Geoportail](http://geoportail.fr/url/7FFQN5) project of the [National Institute of Geographic and Forest Information](http://www.ign.fr/), it implements the open standards of the Open Geospatial Consortium ([OGC](http://www.opengeospatial.org/)) WMS 1.3.0 and 1.0.0 WMTS.

This cartridge is scalable on openshift.

### Installation

To install this cartridge use the cartridge reflector when creating an app

	rhc create-app myapp http://cartreflect-claytondev.rhcloud.com/reflect?github=renaudboulard/openshift-rok4-cartridge


### Configuration

The cartridge installs two config files. One at <code>$OPENSHIFT_NGINX_DIR/conf/nginx.conf</code> which gets loaded by the executable
and sets up specific app configuration such as logs and pid files.

The config then includes another nginx.conf which must exist at <code>$OPENSHIFT_REPO_DIR/nginx.conf</code>. This config should
contain all your server specific set up including which ip/port to listen on.

The repo nginx.conf is actually seen in your repository as <code>nginx.conf.erb</code> so environment variables can be used
in the config. Every time the server starts it first processes <code>nginx.conf.erb</code>.


A <code>public/</code> folder is included where static content is served by default. However, as can be seen in the <code>nginx.conf.erb</code> file it
is entirely configurable and only exists as a form of documentation.
