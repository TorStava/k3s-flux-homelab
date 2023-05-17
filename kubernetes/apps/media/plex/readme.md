# Plex

If you have trouble connecting to the service, you can use port forwarding and connect to localhost:32400

    kubectl port-forward -n media service/plex 32400:32400

Remember to port-forward TCP 32400 from your firewall to the Plex LoadBalancer IP (PLEX_METALLB_IP)

In server settings enable remote access and verify that the port is the same as you forwarded on the Firewall.

Not sure if it does any harm/good, but I also prefer to disable IPv6 under Settings/Network

Whitelist LAN networks (modify to your preferred networks):

    192.168.1.0/255.255.255.0, 10.0.0.0/255.0.0.0

Verify that custom server access URLs contain your public URL, as well as the LB IP:

    https://plex.${SECRET_DOMAIN},http://${PLEX_METALLB_IP}:32400

Then, add your libraries and enjoy!
