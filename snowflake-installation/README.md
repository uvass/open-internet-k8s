
# Installation

Snowflake is a system that allows people from all over the world to access censored websites and applications. You can read about Tor and Snowflake as software on the Snowflake page https://snowflake.torproject.org/?lang=en_US

I'm using the snowflake proxy software as mentioned in the link above. To install it on K8s (in my case I have set up a K8s cluster based on Rancher) you can use helm.

Just to add the helm repo and install it by using the following commands.

```
helm repo add microauth-medium https://hub.microauth.io/chartrepo/medium
helm repo update
helm install snowflake-proxy microauth-medium/tor-snowflake-proxy
```

After that the Snowflake proxy should be up and running.

To uninstall just enter

```
helm uninstall -n security snowflake-proxy
```