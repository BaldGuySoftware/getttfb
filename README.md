# Overview

getttfb is a CLI Tool to determine the Time To First Byte for a given URL and
IP/hostname.  By default it will also attempt to upload the results to a local
Redis instance for tracking.


# Examples

This example will send a request to localhost with the host header of
"www.google.com". The "type" of check is "proxycheck" and is used in storing
the data in Redis if used. Because I'm a bit lazy in this codebase, you still
need to send all the arguments.

  getttfb www.google.com localhost proxycheck


# Redis

If configured with with Redis, the results will be stored in the Redis host
identified by the environment variables `GETTTFB_REDISHOST`, using
`GETTTFB_REDISAUTH` for the redis password on connect.

# Output

XTIMESTAMP TOTALTTFB CONNECTIONTIME SERVERTTFB

The output is tab delimited. Total TTFB is the entire process including DNS and
connection time. Connection time is just the time it takes to make a
connection, and server TTFB is the time post-connection - the actual processing
time.


# TODO

Lots of things.

 * More (some?) error checking on the Redis commands
 * Make the "test type/name" variable optional - perhaps an ENV variable?
 * Travis-ci.org integration and github release upload?
 * Create a Docker file
 * Docker Hub image auto-upload?