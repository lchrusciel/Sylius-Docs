Shipping Categories
===================

These endpoints will allows you to easily manage shipping categories. Endpoints' base is `/api/shipping-categories`.

Shipping categories have two different serialization groups. While presenting a list you will receive an object with following fields:

+-------+---------------------------+
| Field | Description               |
+=======+===========================+
| id    | Id of shipping category   |
+-------+---------------------------+
| name  | Name of shipping category |
+-------+---------------------------+

If you request for a more detailed data, you will receive an object with following fields:

+-------------+----------------------------------+
| Field       | Description                      |
+=============+==================================+
| id          | Id of shipping category          |
+-------------+----------------------------------+
| name        | Name of shipping category        |
+-------------+----------------------------------+
| description | Description of shipping category |
+-------------+----------------------------------+


.. note::

    Read more about `shipping categories`__ in a components models section.

__ http://docs.sylius.org/en/latest/components/Shipping/models.html#shippingcategory

Index of all shipping categories
--------------------------------

You can retrieve the full shipment categories list by making the following request:

Definition
..........

.. code-block:: text

    GET /api/shipping-categories/

+---------------+----------------+-------------------------------------------------------------------+
| Parameter     | Parameter type | Description                                                       |
+===============+================+===================================================================+
| Authorization | header         | Token received during authentication                              |
+---------------+----------------+-------------------------------------------------------------------+
| page          | query          | *(optional)* Number of the page, by default = 1                   |
+---------------+----------------+-------------------------------------------------------------------+
| limit         | query          | *(optional)* Number of items to display per page, by default = 10 |
+---------------+----------------+-------------------------------------------------------------------+


Example
.......

.. code-block:: bash

    curl http://sylius.dev/api/shipping-categories/
        -H "Authorization: Bearer MWExMWM0NzE1NmUyZDgyZDJiMjEzMmFlMjQ4MzgwMmE4ZTkxYzM0YjdlN2U2YzliNDIyMTk1ZDhlNDYxYWE4Ng"
        -H “Accept:text/json”

Example Response
~~~~~~~~~~~~~~~~

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

    {
        "page":1,
        "limit":10,
        "pages":1,
        "total":2,
        "_links":{
            "self":{
                "href":"\/api\/shipping-categories\/?page=1&limit=10"
            },
            "first":{
                "href":"\/api\/shipping-categories\/?page=1&limit=10"
            },
            "last":{
                "href":"\/api\/shipping-categories\/?page=1&limit=10"
            }
        },
        "_embedded":{
            "items":[
                {
                    "id":1,
                    "name":"Regular"
                },
                {
                    "id":2,
                    "name":"Heavy"
                }
            ]
        }
    }

Getting a single shipping cateogry
----------------------------------

You can request detailed shipping category information by executing the following request:

Definition
..........

.. code-block:: text

    GET /api/shipping-categories/{id}

+---------------+----------------+-------------------------------------------------------------------+
| Parameter     | Parameter type | Description                                                       |
+===============+================+===================================================================+
| Authorization | header         | Token received during authentication                              |
+---------------+----------------+-------------------------------------------------------------------+
| id            | attribute      | Id of requested resource                                          |
+---------------+----------------+-------------------------------------------------------------------+
| page          | query          | *(optional)* Number of the page, by default = 1                   |
+---------------+----------------+-------------------------------------------------------------------+
| limit         | query          | *(optional)* Number of items to display per page, by default = 10 |
+---------------+----------------+-------------------------------------------------------------------+

Example
.......

.. code-block:: bash

    curl http://sylius.dev/api/shipping-categories/1
        -H "Authorization: Bearer MWExMWM0NzE1NmUyZDgyZDJiMjEzMmFlMjQ4MzgwMmE4ZTkxYzM0YjdlN2U2YzliNDIyMTk1ZDhlNDYxYWE4Ng"
        -H “Accept:text/json”

Example Response
~~~~~~~~~~~~~~~~

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

    {
        "id":1,
        "name":"Regular",
        "description":"Regular weight items",
        "_links":{
            "self":{
                "href":"\/api\/shipping-categories\/1"
            }
        }
    }

Creating shipping category
--------------------------

Definition
..........

.. code-block:: text

    POST /api/shipping-categories/

+---------------+----------------+--------------------------------------------------------+
| Parameter     | Parameter type | Description                                            |
+===============+================+========================================================+
| Authorization | header         | Token received during authentication                   |
+---------------+----------------+--------------------------------------------------------+
| name          | request        | Name of creating shipping category                     |
+---------------+----------------+--------------------------------------------------------+
| description   | request        | *(optional)* Description of creating shipping category |
+---------------+----------------+--------------------------------------------------------+

Example
.......

.. code-block:: bash

    curl http://sylius.dev/api/shipping-categories/
        -H "Authorization: Bearer MWExMWM0NzE1NmUyZDgyZDJiMjEzMmFlMjQ4MzgwMmE4ZTkxYzM0YjdlN2U2YzliNDIyMTk1ZDhlNDYxYWE4Ng"
        -H “Accept:text/json”
        -X POST
        --data "name=Light&description=Light weight items"


Example Response
~~~~~~~~~~~~~~~~

.. code-block:: text

    STATUS: 201 Created

.. code-block:: json

    {
        "id":3,
        "name":"Light",
        "description":"Light weight items",
        "_links":{
            "self":{
                "href":"\/api\/shipping-categories\/3"
            }
        }
    }

If you try to create a resource without name, you will receive a 400 error.

Example
.......

.. code-block:: bash

    curl http://sylius.dev/api/shipping-categories/-1
        -H "Authorization: Bearer MWExMWM0NzE1NmUyZDgyZDJiMjEzMmFlMjQ4MzgwMmE4ZTkxYzM0YjdlN2U2YzliNDIyMTk1ZDhlNDYxYWE4Ng"
        -H “Accept:text/json”
        -X POST

Example Response
~~~~~~~~~~~~~~~~

.. code-block:: text

    STATUS: 400 Bad Request

.. code-block:: json

    {
        "code":400,
        "message":"Validation Failed",
        "errors":{
            "children":{
                "name":{
                    "errors":[
                        "Please enter shipping category name."
                    ]
                },
                "description":[

                ]
            }
        }
    }

Updating shipping category
--------------------------

You can request full or partial update of resource. For full shipping category update, you should use PUT method.

Definition
..........

.. code-block:: text

    PUT /api/shipping-categories/{id}

+---------------+----------------+-------------------------------------------+
| Parameter     | Parameter type | Description                               |
+===============+================+===========================================+
| Authorization | header         | Token received during authentication      |
+---------------+----------------+-------------------------------------------+
| id            | attribute      | Id of requested resource                  |
+---------------+----------------+-------------------------------------------+
| name          | request        | Name of creating shipping category        |
+---------------+----------------+-------------------------------------------+
| description   | request        | Description of creating shipping category |
+---------------+----------------+-------------------------------------------+

Example
.......

.. code-block:: bash

    curl http://sylius.dev/api/shipping-categories/3
        -H "Authorization: Bearer MWExMWM0NzE1NmUyZDgyZDJiMjEzMmFlMjQ4MzgwMmE4ZTkxYzM0YjdlN2U2YzliNDIyMTk1ZDhlNDYxYWE4Ng"
        -H “Accept:text/json”
        -X PUT
        --data "name=Ultra Light&description=Ultra light weight items"


Example Response
~~~~~~~~~~~~~~~~

.. code-block:: text

    STATUS: 204 No Content

If you try to perform full shipping category update without all required fields specified, you will receive a 400 error.

Example
.......

.. code-block:: bash

    curl http://sylius.dev/api/shipping-categories/-1
        -H "Authorization: Bearer MWExMWM0NzE1NmUyZDgyZDJiMjEzMmFlMjQ4MzgwMmE4ZTkxYzM0YjdlN2U2YzliNDIyMTk1ZDhlNDYxYWE4Ng"
        -H “Accept:text/json”
        -X PUT

Example Response
~~~~~~~~~~~~~~~~

.. code-block:: text

    STATUS: 400 Bad Request

.. code-block:: json

    {
        "code":400,
        "message":"Validation Failed",
        "errors":{
            "children":{
                "name":{
                    "errors":[
                        "Please enter shipping category name."
                    ]
                },
                "description":[

                ]
            }
        }
    }


In order to perform a partial update, you should use a PATCH method.

Definition
..........

.. code-block:: text

    PATCH /api/shipping-categories/{id}

+---------------+----------------+--------------------------------------------------------+
| Parameter     | Parameter type | Description                                            |
+===============+================+========================================================+
| Authorization | header         | Token received during authentication                   |
+---------------+----------------+--------------------------------------------------------+
| id            | attribute      | Id of requested resource                               |
+---------------+----------------+--------------------------------------------------------+
| name          | request        | *(optional)* Name of creating shipping category        |
+---------------+----------------+--------------------------------------------------------+
| description   | request        | *(optional)* Description of creating shipping category |
+---------------+----------------+--------------------------------------------------------+

Example
.......

.. code-block:: bash

    curl http://sylius.dev/api/shipping-categories/3
        -H "Authorization: Bearer MWExMWM0NzE1NmUyZDgyZDJiMjEzMmFlMjQ4MzgwMmE4ZTkxYzM0YjdlN2U2YzliNDIyMTk1ZDhlNDYxYWE4Ng"
        -H “Accept:text/json”
        -X PATCH
        --data "name=Light"


Example Response
~~~~~~~~~~~~~~~~

.. code-block:: text

    STATUS: 204 No Content

Deleting shipping category
--------------------------

Definition
..........

.. code-block:: text

    DELETE /api/shipping-categories/{id}

+---------------+----------------+-------------------------------------------+
| Parameter     | Parameter type | Description                               |
+===============+================+===========================================+
| Authorization | header         | Token received during authentication      |
+---------------+----------------+-------------------------------------------+
| id            | attribute      | Id of requested resource                  |
+---------------+----------------+-------------------------------------------+

Example
.......

.. code-block:: bash

    curl http://sylius.dev/api/shipping-categories/3
        -H "Authorization: Bearer MWExMWM0NzE1NmUyZDgyZDJiMjEzMmFlMjQ4MzgwMmE4ZTkxYzM0YjdlN2U2YzliNDIyMTk1ZDhlNDYxYWE4Ng"
        -H “Accept:text/json”
        -X DELETE


Example Response
~~~~~~~~~~~~~~~~

.. code-block:: text

    STATUS: 204 No Content
