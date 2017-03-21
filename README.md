# mesos-external-container-logger

This is a container logger module for [Mesos](http://mesos.apache.org/)
that redirects container logs to an external process.

This branch is a backport to Mesos 0.28.2 of the `ExternalContainerLogger` module
developed in
[MESOS-6003](https://issues.apache.org/jira/browse/MESOS-6003).
Read the [documentation](https://reviews.apache.org/r/51258/) or this
[blog post](https://wjoel.com/posts/mesos-container-log-forwarding-with-filebeat.html)
for more information and some example use cases.

The module has been compiled for Ubuntu 14.04.5 (trusty), See [Releases](https://github.com/r4um/mesos-external-container-logger/releases) if you need the binary. 

Use the `compile.sh` and optionally the `build-mesos.sh` scripts to build the module for other distributions.

To configure pass `--container-logger=org_apache_mesos_ExternalContainerLogger` along with a module
configuration like below


```
{
  "libraries": [{
    "file": "/usr/lib/libexternal_container_logger-0.1.0.so",
    "modules": [{
      "name": "org_apache_mesos_ExternalContainerLogger",
      "parameters": [{"value": "/usr/bin/filebeat-container-logger.sh",
                      "key": "external_logger_binary"}]
    }]
  }]
```
