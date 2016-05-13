# Changelog

## 2016-05-13

Status|Api|Content|
 -------| ------- | -----------
Added|GET /v2/my/locations|Get locations of current owner
Added|GET /v2/my/monitors|Get monitors of current owner
Added|GET /v2/my/settings|Get display settings
Added|PATCH /v2/settings|Update display settings

## 2016-05-05

Status|Api|Content|
 -------| ------- | -----------
Added|GET /v2/locations/{location_id}/staffs|Get staffs of location
Added|GET /v2/locations/{location_id}/certifications|Get certifications of location
Added|GET /v2/clients|Get clients
Added|GET /v2/clients/{client_id}/users|Get users of the specific client
Added|PATCH /v2/locations/{location_id}|Update location


## 2016-04-28

Status|Api|Content|
 -------| ------- | -----------
Added|/v2/followings|location and monitor following
Added|/v2/locations/{location_id}/sharings|location sharing
Added|/v2/locations/{location_id}/notifications|location notification
Added|/v2/monitors/{monitor_id}/calibrations|monitor calibration

## 2016-04-20
Status|Api|Content|
 -------| ------- | -----------
Added|/v2/monitors/{monitor_id}|new api for updating monitor
Added|/v2/dictionaries/*|bunche api for dictionary


## 2016-04-12
Status|Api|Content|
 -------| ------- | -----------
Updated|/v2/monitors/{monitor_id}|rename stale to status, returned by server
Added|/v2/locations/{location_id}/monitors|new api for getting all monitors of the location
Added|/v2/histories|new api for history

## 2016-04-11

Status|Api|Content|
 -------| ------- | -----------
Updated|/v2/locations/{location_id}|new parameter for unlock_token
Added|/v2/locations/{location_id}/unlock|new api for unlocking location
Added|/v2/readings|new api for all readings