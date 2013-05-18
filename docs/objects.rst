libnmap.objects
===============

What
----
this module contains the definition and API of all "NmapObjects" which enables user to manipulate nmap data:

1. NmapReport
2. NmapHost
3. NmapService

The following structure applies by default:

NmapReport contains:
    - Scan "header" data (start time, nmap command, nmap version, ...)
    - List of NmapHosts (0 to X scanned hosts could be nested in a nmap report)
    - Scan "footer" data (end time, summary, ...)
    
NmapHost contains:
    - Host "header" data (state, hostnames, ip, ...)
    - List of NmapService (0 to X scanned services could be nested in a scanned host)
    - Host "footer" data (os version, fingerprint, uptime, ...)
    
NmapService contains:
    - scan results for this service:
        - service state, service name
        - optional: service banner
        - optionla: NSE scripts data

Each of the above-mentioned objects have a diff() method which enables the user of the lib the compare two different objects
of the same type.
If you read the code you'll see the dirty trick with id() which ensures that proper objects are being compared. The logic of diff will certainly change overtime but the API (i/o) will be kept as is.

For more info on diff, please check the module's `documentation <diff>_`.

Code API
--------

.. automodule:: libnmap.objects
.. autoclass:: NmapReport
    :members:
.. autoclass:: NmapHost
    :members:
.. autoclass:: NmapService
    :members: