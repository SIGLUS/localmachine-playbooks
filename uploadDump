#!/bin/bash

# Get the current date
DATE=$(date +%Y%m%d)

# Define the facility name variable
FACILITY_NAME=$1

if [ -z "$FACILITY_NAME" ]
then
   echo "Por favor, insira o nome da instalação. (Please enter the Facility Name.)"
   exit 1
fi

# Execute the database dump operation
/opt/simam/bin/dump-db

# Rename the database dump file
mv simam-db.sql.gz ${DATE}-${FACILITY_NAME}.sql.gz

# Upload the database dump file to AWS S3
aws s3 cp ${DATE}-${FACILITY_NAME}.sql.gz s3://siglus-localmachine-dbdump
