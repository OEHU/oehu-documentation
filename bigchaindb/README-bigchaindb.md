# README on BigchainDB

## Basics


Configuration: `/root/.bigchaindb`

Mongo config: `/etc/mongodb.conf`

    mongo --port 27017 -u "user" -p "pass" --authenticationDatabase "admin"

    use bigchain

    db.createUser(
      {
        user: "bigchain-user",
        pwd: "le-pass",
        roles: [ { role: "readWrite", db: "bigchain" } ]
      }
    )

db.createUser(
  {
    user: "admin",
    pwd: "KnFmARCUNuiDRobwW3Zxz64Ze",
    roles: [ { role: "root", db: "admin" } ]
  }
);

db.grantRolesToUser( "oehu-admin", [ { role: "root", db: "admin" } ] )

    mongo --port 27017 -u "oehu-admin" -p "pass" --authenticationDatabase "admin"

Reloading bigchaindb:

    sudo monit reload

If ^ doesn't work:

- Find the PID of the monit daemon & kill it + `monit -d 1`

## Using mongodb for querying bigchaindb data

### Get device info (household type, etc)

    db.assets.find({ "data.id": "id:1a111111:devices:1a1a1a11-1a11-1a11-1111-11111111111a" })

Remember `id`.

### Get all transactions:

    db.getCollection('transactions').find({"asset.id": "a11aa1aa1aaa111111a1a11aaaa1aaa1aaa111a1aa1aa1a1a11111a11a11a111"})

Remember `id`.

### Get metadata (KwH & m3, location, etc)

    db.getCollection('metadata').find({ id: "a11aa1aa1aaa111111a1a11aaaa1aaa1aaa111a1aa1aa1a1a11111a11a11a111" })

Now you have your KwH & gas data.

____

_below some notes on queries we can use_

# Personal dashboard:

## Current state

- Get device
- Get last tx
- Get meta data of tx

## 24 hour use

- Get device
- Get tx of 24 hours ago `timestamp: { $gt: timestamp }, {limit: 1}`
- Get meta data of tx

## Monthly overview

- Get device

Then, for every day of current month:

- Get one tx
- Get meta data of tx

# Global dashboard

## Connected devices

    db.assets.find({}).size()

## Map

- Get all devices
- Get all metadata

## Gemiddeld verbruik afgelopen 24 uur

- Get all devices
- Get current values for every device
- Get values of 24 hours ago for every device
- Get meta data of tx

## Meters connected 

- Get count(assets)
