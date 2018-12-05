# tq-xxx Attempt use of TCP Fast Open

When a transparent HTTP or TLS proxy is in the path between the probe and the
target server, an attempt to use TCP fast open may reveal its presence in
following ways:

1. The connection fails due to an unknown TCP option being present
2. The second connection fails due to data being present on the TCP SYN packet
3. TCP fast open is not negotiated where expected, or is negotiated where it is
   not expected

## Methodology

1. Fetch a webpage from a target server using either HTTP or HTTPS, using TCP
   fast open to establish a TFO cookie
2. If successful, fetch a webpage from the same server, again using TCP fast
   open (this time will have data on the SYN)
3. If the first connection failed, retry the request without the use of the TCP
   fast open to confirm that this was responsible for the connectivity failure,
   and not just that the host was down

## Examples

- None yet

## References

- [RFC7413: TCP Fast Open](https://tools.ietf.org/html/rfc7413)

## Implementations

- An independent implementation exists for this technique in PATHspider's [TFO
  plugin](https://pathspider.readthedocs.io/en/latest/plugins/tfo.html)
