rsnapshot-based "tape rotation" backups, using USB HDDs
============================================================
This package provides a bare-minimum wrapper around rsnapshot to
ensure it has sensible defaults.

Features
------------------------------------------------------------
* Stores incrementals as hard links, like Apple Time Machine (active ingredient ``rsync --link-dest``).
* USB HDD can be read by Windows desktops.
* Sends a success/failure email.


Quick start guide
------------------------------------------------------------
#. Download or build datasafe-lite deb (``debuild``).
#. Install it (``apt install ./datasafe-lite*.deb``).
#. Plug in a USB HDD.
#. Erase it (``datasafe-lite-init /dev/disk/by-id/usb-SanDisk_Ultra_Fit_4C530001031224113231-0:0``).
#. Done!


Configuration
------------------------------------------------------------
* datasafe-lite sends a success/failure email when it finishes.
  If you don't receive one, check that system email is working.
  For more detailed logs try ``journalctl --unit=datasafe-lite``.

* By default only /home /srv and /var/mail are backed up.
  Change this in ``/etc/datasafe-lite.conf``.

* The default retention policy is ``56d 52w 24m 10y``.
  You **MUST** have at least one daily.
  You **MUST NOT** have any hourly.
