Updating a Trade
================

The technical specifications can be viewed on our
`API docs <https://api.tradesafe.co.za/#contract-put>`_.

To update a trade certain conditions have to be met. In this example we must
have already verified the funds before this request can be processed.

Not all steps are avalible and currenly we do not allow any modification of the
trade data after it has been accepted.

The example below would be typically run once you have recieved notification
that your user has recieved the goods or service.

PHP Example
-----------

.. code-block:: php
  :linenos:

  <?php
  # The JWT for your account
  $json_token = 'your_jwt_token';

  # The url of the API
  $service_url = 'https://sandbox.tradesafe.co.za/api/contract/{ID_OF_THE_TRADE}.json';

  $curl = curl_init($service_url);

  $postfields = array(
    "id" => "5899715f-bda4-4c91-b78c-033aac102991",
    "step" => "GOODS_ACCEPTED"
  );

  curl_setopt_array($curl, array(
    CURLOPT_CUSTOMREQUEST => "PUT",
    CURLOPT_RETURNTRANSFER => TRUE,
    CURLOPT_HTTPHEADER => array(
      'Authorization: Bearer ' . $json_token,
      'Content-Type: application/json'
    )
  ));

  $curl_response = curl_exec($curl);
  curl_close($curl);

  $response = json_decode($curl_response);

  print_r($response);
  ?>
