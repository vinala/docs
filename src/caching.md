## Caching

### Introduction

Lighty provides a caching system, Caching is frequently used to reduce the time it takes to create or read from other resources. Caching is often used to make reading from expensive resources less expensive. You can store the results of expensive queries, or remote webservice access that doesn’t frequently change in a cache. Once in the cache, re-reading the stored resource from the cache is much faster than accessing the remote resource.

Caching in Lighty is facilitated by the `Cache` class. This class provides a set of static methods that provide a uniform API to dealing with all different types of Caching implementations. Lighty comes with several cache systems built-in, and provides an easy system to implement your own caching systems.

The built-in caching systems are :
* File : File cache is a simple cache that uses local files. It is the slowest cache engine, and doesn’t provide as many features for atomic operations. However, since disk storage is often quite cheap, storing large objects, or elements that are infrequently written work well in files.

* Database : working....

### Configuration

Configuring the Cache class can be done in `config/cache.php`, ...

### Dealing with caching
#### Write to cache