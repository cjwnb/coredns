# fs

## Name

*fs* - provide a filesystem abstraction.

## Description

Take into account *root*? Only for zone data??

## Syntax

~~~ txt
fs TYPE MOUNTPOINT
~~~

**TYPE** is the "file system" type. Defined are `disk` and `mem`. **MOUNTPOINT** is the location
where is mounted. By default the plugin mount "/" to point to `disk`. But for instance if you can
mount `s3` (if implemented) under `/s3`; then a path used in any other plugin that starts with
`/s3` will use S3 storage underneath. This plugin may be used multiple times to register multiple
paths using (different) "file system" implementations.

## Examples

~~~ corefile
. {
    fs disk /
}
~~~

## Notes

The *tls* plugin (as all default plugins) uses the *fs* plugin for storage abstraction, except when
finding the root CAs bundled by the OS. This is a std pkg library call which we can not intercept.