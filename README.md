# zap2xml
Docker container for zap2xml.

This is zap2xml with Environment Variables driving the configuration. By default it runs every 12 hours to update your EPG data from zap2it or tvguide

## Quick Run
`docker run -d --name zap2xml -v /xmltvdata:/data -e USERNAME=youremail@email.com -e PASSWORD=**password** -e OPT_ARGS="-z -d 7" -e XMLTV_FILENAME=xmltv.xml watermark/zap2xml`

## Docker Compose
services:
  zap2xml:
    image: watermark/zap2xml
    container_name: zap2xml
    restart: unless-stopped
    volumes:
      - zap2xml_data:/data
    environment:
      - USERNAME=username
      - PASSWORD=password
      - OPT_ARGS=-z -d 7
volumes:
  zap2xml_data:

## Environment Settings
You can configure the following environment variables below:

### Required
- USERNAME - zap2it.com username
- PASSWORD - zap2it.com password

### Optional
- OPT_ARGS - additional command line arguments for zap2xml
- XMLTV_FILENAME - filename for your xmltv file (default: xmltv.xml)
- SLEEPTIME - time in seconds to wait before next run (default: 43200)

### Original Credit
Forked from https://github.com/shuaiscott/zap2xml