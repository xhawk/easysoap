## What ?
`easySoap` is a WSDL SoapClient for Node.js.

## How to get ?

    npm install easysoap

## How to use ?

    var easySoap    = require('easysoap');

    //soap client params
    var clientParams = {

        //set soap connection data (mandatory values)
        host    : 'www.sample.com',
        path    : '/dir/soap',
        wsdl    : '/dir/wsdl',

        //set soap header (optional)
        header  : [{
            'name'      : 'item_name',
            'value'     : 'item_value',
            'namespace' : 'item_namespace'
        }]
    };

    //soap client options
    var clientOptions = {
        secure : true/false //is https or http
    };

    //create new soap client
    var SoapClient = new easySoap.Client(clientParams, clientOptions);

        BexSoapClient.on('error', function(error) {
            console.log(error);
        });

        SoapClient.once('initialized', function() {

            //after successful initialized


            //old deprecated way, will be removed in future versions
            SoapClient.once('soapMethod', function(err, data, header) {
                //soap response
            });

            SoapClient.call({
                'method' : 'soapMethod',
                'params' : {
                    'test' : 1
                }
            });


            //new promise way
            SoapClient.call({
                'method' : 'soapMethod2',
                'params' : {
                    'test' : 2
                }
            })
            .done(function(data) {

                console.log(data.content); //contain soap response data
                console.log(data.header);  //contain soap response header

                //soap response
            }, function(err) {
                //soap error
            });




        });

        //initialize soap client
        SoapClient.init();
