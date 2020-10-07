# ansible-f5
Ansible automation against f5 load balancers 

# playbooks
le-create-cert.yml - this should be run first.  This is what creates the certificates.  dns_key is the API key of your cloudflair account and should be supplied at run either through a vault or via tower's custom credentials.  The variables are documented in the beginning of the script.  This will create the keys, make the initial request, make the DNS txt files, then finalize the request and create the cert files.

le-cert-install-createenv.yml - This creates my demo VIP and installs the newly created certs to the virtual server.

le-cert-reinstall.yml - This is a simple playbook that will check the certs in the /opt/cert-store folder and update the F5's certs if they are newer.  Easiest thing to do is schedule le-create-cert.yml to run every 30 days, then have this play run directly after.  This is a great place to implement a workflow in ansible tower.

le-cert-resetlab.yml - This is a cleanup script that removes everything created for my demo lab environment.
