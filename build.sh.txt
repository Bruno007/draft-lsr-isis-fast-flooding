#!/bin/bash

D=draft-decraeneginsberg-lsr-isis-fast-flooding

xml2rfc $D.xml

nl -ba $D.txt > $D.nl.txt
