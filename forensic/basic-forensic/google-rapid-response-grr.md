# Google Rapid Response GRR

## Google Rapid Response GRR

### Update config

grr\_config\_updater initialize

### Update Rekall profil

from grr.lib import rekall\_profile\_server

### delete client

aff4.FACTORY.Delete\("C.12c35ccfe21a0312"\) aff4.FACTORY.Delete\("C.57b631523d57fb76"\) aff4.FACTORY.Delete\(rdf\_client.ClientURN\(client\_id\)\)

### update rekall profil

from grr.lib import rekall\_profile\_server rekall\_profile\_server.GRRRekallProfileServer\(\).GetMissingProfiles\(\)

### update component

`python grr/client/client_build.py --config grr-server.yaml build_component \ grr/client/components/rekall_support/setup.py /tmp/rekall_component.bin`

`python grr/tools/config_updater.py --config grr-server.yaml upload_component \ /tmp/rekall_component.bin`

