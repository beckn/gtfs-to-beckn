# GTFS to beckn Adapter

## Release History

| Version | Release Date   | Contributors    |
|---------|----------------|-----------------|
| 0.5     | 21st Feb, 2022 | Nirmal Rajeevan |

## Changelog

None

## Overview

A simple BPP implementation that converts [GTFS](https://gtfs.org) data into a [beckn](https://github.com/beckn/protocol-specifications) catalog. Discovery flow is implemented here. Transfers are currently not supported.

This application reads static GTFS data from gtfs-data folder and returns catalog of available fare products between stations including the schedule and fare.

You can find exact mappings of GTFS to beckn schema [here](./GTFS-TO-BECKN.md).

You can find a general how it works document [here](./HOW-IT-WORKS.md).

## Installation

### Installation via CLI

This application can be installed just like any other NodeJS application by running,

```
npm install
```

To build this application, just run

```
npm run build
```

### Building the application using Docker 

Run the following command :
`docker build . -t gtfs-bpp`

To run the built image run the command :
`docker run -p 8000:8000 --name gtfs-bpp-image --env MAPS_KEY=< key > gtfs-bpp`

#### Environment Variables

The following environment variables should be set.

- `MAPS_KEY` : Google maps API key for location matrix API
- `sign_public_key` : Signing public key
- `sign_private_key` : Signing public key
- `bpp_id` 
- `bpp_uri`
- `registry_url`
- `unique_key_id`
- `country` : Default value set as "IND"
- `domain` : Default value set as "nic2004:60212"
- `city` : Default value set as ""
- `core_version` :  Default value set as "0.9.3"
- `ENABLE_LOCATION_SERVICES` : If `true` will take in the start and end GPS coordinates, finds the closest stations to the coordinates and returns ticket information for trips between the them. Else will return a list of all stops if GPS coordinates are passed.

#### Optional
- `THRESHOLD_DISTANCE_KM` : Threshold to select next closest station (default: 0.50)
- `MAX_STATIONS` : Maximum number of nearest stations to return for a location (default:2)
- `DISTANCE_LIMIT_KM` : Maximum distance from which closest station should be returned (default:15)
