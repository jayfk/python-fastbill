# python-fastbill

Super thin Python wrapper for Fastbill's HTTP API developed by
[Stylight](http://www.stylight.de/).

Limitations:

* only supports JSON payloads
* doesn't (overly) check for consistency of responses
* doesn't convert date strings to datetime objects

Dependencies:

* requests

## Installation

	pip install fastbill
	
[Official PyPI Fastbill page](https://pypi.python.org/pypi/fastbill/)

## Usage

    from fastbill import FastbillWrapper
    
    # Construct the api client for Fastbill's automatic API

    client = FastbillWrapper('fastbill_user', 'fastbill_key')
    
    # You can also specify a service_url, in case you need Fastbill's core API instead:
    
    core_client = FastbillWrapper('fastbill_user', 'fastbill_key', service_url='endpoint_url')
    
    # Make requests, e.g. service customer.create

    client.customer_create(data={})

    # Search for customer, subscriptions, etc...

    for customer in client.customer_get(filter={'city': 'Munich'}):
        print customer

    # But you can also see the full result

    result = client.customer_get(filter={'city': 'Munich'})
    print result.keys()

    # Will give you 'CUSTOMERS'
