Getting started
---------------

First, start the ubuntu package builder VM:

    $ vagrant up

Follow the instructions it gives you for setting up your environment. Then,
logged into the box, you should be able to make source packages by running
`make <target>` in the `packager` directory. You will be prompted to sign the
source packages with your GPG key.

    $ cd ~/packager
    $ make collectd

To test a binary package build, you first need to set up sbuild:

    $ ./tools/sbuildinit  # follow the instructions about restarting your shell
    $ ./tools/sbuildinit

You can then build binary packages from .dsc files:

    $ sbuild -A -d precise-amd64 build/collectd/collectd_5.3.0-ppa4.dsc

Building packages for multiple series
-------------------------------------

Building packages for multiple series ("Precise", "Lucid", etc.) is slightly
more involved. See [`building_for_multiple_series.md`][building_for_multiple_series.md].

Submitting to Launchpad
-----------------------

Once you've verified that you're able to build a .deb from your .dsc, you can
submit the original .changes file to Launchpad for building:

    $ dput ppa:gds/govuk build/collectd/collectd_5.3.0-ppa4_source.changes