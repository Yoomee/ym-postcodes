# YmPostcodes

ym_postcodes provides a ruby wrapper for the API at postcodes.io.

The API provides UK postcode and geolocation data.

## Installation

Add this line to your application's Gemfile:

    gem 'ym_postcodes'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install ym_postcodes

## Usage

Call the #lookup class method on YmPostcodes::Postcode

```ruby
postcode = YmPostcode::Postcode.lookup "S1 2BJ"

# postcode =>
#
#{
#    "status": 200,
#    "result": {
#        "postcode": "S1 2BJ",
#        "quality": 1,
#        "eastings": 435824,
#        "northings": 387152,
#        "country": "England",
#        "nhs_ha": "Yorkshire and the Humber",
#        "admin_county": null,
#        "admin_district": "Sheffield",
#        "admin_ward": "Central",
#        "longitude": -1.46293025034242,
#        "latitude": 53.3800130453946,
#        "parliamentary_constituency": "Sheffield Central",
#        "european_electoral_region": "Yorkshire and The Humber",
#        "primary_care_trust": "Sheffield",
#        "region": "Yorkshire and The Humber",
#        "parish": null,
#        "lsoa": "Sheffield 075G",
#        "msoa": "Sheffield 075",
#        "nuts": "Central",
#        "incode": "2BJ",
#        "outcode": "S1"
#    }
#}

#postcode =>

#{
#    "status": 404,
#    "error": "Postcode not found"
#}
```

There is also a #lookup_many method which takes up to 100 postcodes and returns
the results in one API request

```ruby
postcode = YmPostcode::Postcode.lookup_many ["S1 2BJ", "S1 2BZ"]
```

## Credits

Thanks to the ideal-postcodes.co.uk team for providing http://www.postcodes.io
and to the authors of https://github.com/ideal-postcodes/ideal-postcodes-ruby
which inspired this gem.

## Licence

MIT

## TODO

 * Use OpenStruct instead of Hash http://ruby-doc.org/stdlib-1.9.3/libdoc/ostruct/rdoc/OpenStruct.html
 * Create a custom exception object: ```rescue YmPostcodes::InvalidApiRequestError => e``` 
 * Add WebMock for tests: http://robots.thoughtbot.com/how-to-stub-external-services-in-tests
