### javac without checked exceptions


Sometimes you just need javac to be more lenient and bend the rules a little.

This version of javac completely ignores exception issues. It will happily let you compile code that throws without `throws ...` declarations, override a method which doesn't throw with a method that does, etc...  

You won't get errors, not even warnings. 

Same idea as project lombok's [experiment](https://projectlombok.org/disableCheckedExceptions.html) but with a simple patch on top of the openjdk sources.

------------------------------------------------------------------------

See [Releases](https://github.com/lemonsqueeze/javac_noce/releases) for jdk 1.8.0_65 build.

Patch and OpenJDK sources are in [1.8.0_65](https://github.com/lemonsqueeze/javac_noce/tree/1.8.0_65) branch.

------------------------------------------------------------------------

Build:

    $ git checkout 1.8.0_65
    # Edit make/build.properties, set boot.java.home to your jdk home
    $ cd make ; ant
    # javac is in built/dist/bootstrap/bin/javac


If you need it for another jdk version:

    $ hg clone http://hg.openjdk.java.net/jdk8u/jdk8u/langtools
    $ hg checkout jdk8u65-b17              # or whatever version you need    
    # apply patch from 1.8.0_65 branch and build

