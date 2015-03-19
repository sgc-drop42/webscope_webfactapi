Exposes an api to interact with website nodes

API specifications :

    GET request - *webfactory_url*/webfact/website.json(all website), *webfactory_url*/webfact/website/*nid*.json (one website)
        Provides the index and retrieve website functionality
        Websites items each contain :

            node_id

            node_title

            status

            hostname

            site_email

            category

            restart_policy

            template

            public

            owner_uid

            url

    PUT request webfactory_url*/webfact/website/*nid_to_update*.
        Provides update functionality, request can provide the following variables

            node_title

            hostname

            site_email

            public

            owner_uid

    POST request webfactory_url*/webfact/website
        Provides craete functionality, request needs to provide the following variables

            node_title

            hostname

            site_email

            public

            owner_uid


API usage examples :

$options = array(
    'method' => 'GET',
    'timeout' => 15,
    'headers' => array('Content-Type' => 'application/json'),
);

$result = drupal_http_request('http://website-url/webfact/website/*nid*', $options);

***********************************************************

Retrieve all websites :

$data = array('field_public'=>1);

$retrieve_data = json_encode($data);

$options = array(
    'method' => 'GET',
    'data' => $retrieve_data,
    'timeout' => 15,
    'headers' => array('Content-Type' => 'application/json'),
);

$result = drupal_http_request('http://website/webfact/website*', $options);

*optional filter by field eg ?parameters[field_public]=0

***********************************************************

Update website :

$data = array('node_title'=>'xxxxx node title','hostname'=>'yyyyyy','site_email'=>'gggggg@test.com','public'=>0,'owner_uid'=>27);

$update_data = json_encode($data);

$options = array(
    'method' => 'PUT',
    'data' => $update_data,
    'timeout' => 15,
    'headers' => array('Content-Type' => 'application/json'),
);

$result = drupal_http_request('http://website/webfact/website/*nid*', $options);

***********************************************************

Create website :

$data = array('node_title'=>'xxxxx node title','hostname'=>'yyyyyy','site_email'=>'gggggg@test.com','public'=>1,'owner_uid'=>12);

$create_data = json_encode($data);

$options = array(
    'method' => 'POST',
    'data' => $create_data,
    'timeout' => 15,
    'headers' => array('Content-Type' => 'application/json'),
);

$result = drupal_http_request('http://website/webfact/website', $options);

***********************************************************
