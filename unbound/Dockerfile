FROM klutchell/unbound

COPY unbound.conf /opt/unbound/etc/unbound/

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
        CMD [ "drill", "-p", "53", "nlnetlabs.nl", "@127.0.0.1" ]
