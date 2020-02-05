#### List of db
    show dbs
#### Select the database
    use flights
#### Create a collection
    db.flightData.insertMany(
        [{
            "departureAirport":"MUC",
            "arraivalAirport":"SFO",
            "aircraft":"Aribus A380",
            "distance":12000,
            "intercontinental":true
        },{
            "departureAirport":"LHR",
            "arraivalAirport":"TXL",
            "aircraft":"Airbus A857",
            "distance":12000,
            "intercontinental":true
        }]
    )
####