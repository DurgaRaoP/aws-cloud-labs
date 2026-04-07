#!/bin/bash
# Script to check if Apache httpd is running and start it if not
# Author: Pusalapati Durga Rao

if systemctl is-active --quiet httpd; then
    echo "httpd is RUNNING"
else
    echo "httpd is STOPPED - starting it now"
    sudo systemctl start httpd
fi
