Japan Post Tracking API - Python
================================
Use Python to track Japan Post shipments with Japan Post Tracking API.

Features
--------
- Real-time Japan Post tracking.
- Batch Japan Post tracking.
- Other features to manage your Japan Post tracking.

Installation
------------

Installation is easy:

    $ pip install trackingmore-sdk-python

Quick Start
----------
Get the API key:

To use this API, you need to generate your API key.

- <a href="https://admin.trackingmore.com/developer/apikey" target="_blank" rel="noreferrer">
  Click here</a> to access TrackingMore admin.

- Go to the "Developer" section.

- Click "Generate API Key".

- Give a name to your API key, and click "Save" .


Then, start to track your Japan Post shipments.

Usage
----------

Create a tracking (Real-time tracking):

      import trackingmore
      trackingmore.api_key = 'your api key'
      
      try:
        params = {'tracking_number': 'RN061075020JP','courier_code':'japan-post'}
        result = trackingmore.tracking.create_tracking(params)
        print(result)
      except trackingmore.exception.TrackingMoreException as ce:
        print(ce)
      except Exception as e:
        print("other error:", e) 


Create trackings (Max. 40 tracking numbers create in one call):

    import trackingmore
    trackingmore.api_key = 'your api key'
    
    try:
      params = [
        {'tracking_number': 'RM129335604IN', 'courier_code': 'japan-post'},
        {'tracking_number': 'RN061021865JP', 'courier_code': 'japan-post'}
      ]
      result = trackingmore.tracking.batch_create_trackings(params)
      print(result)
    except trackingmore.exception.TrackingMoreException as ce:
      print(ce)
    except Exception as e:
      print("other error:", e) 


Get status of the shipment:

    import trackingmore
    trackingmore.api_key = 'your api key'
    
    try:
      # Perform queries based on various conditions
      # params = {'tracking_numbers': 'RM129335604IN', 'courier_code': 'japan-post'}
      # params = {'tracking_numbers': 'RN061021865JP,RN061075020JP', 'courier_code': 'japan-post'}
      params = {'created_date_min': '2023-08-23T06:00:00+00:00', 'created_date_max': '2023-09-05T07:20:42+00:00'}
      result = trackingmore.tracking.get_tracking_results(params)
      print(result)
    except trackingmore.exception.TrackingMoreException as ce:
      print(ce)
    except Exception as e:
      print("other error:", e) 


Update a tracking by ID:

    import trackingmore
    trackingmore.api_key = 'your api key'
    
    params = {'customer_name': 'New name', 'note': 'New tests order note'}
    id_string = "9d8a46505ea0e17b78ab92125b3f0ceb"
    try:
      result = trackingmore.tracking.update_tracking_by_id(id_string, params)
      print(result)
    except trackingmore.exception.TrackingMoreException as ce:
      print(ce)
    except Exception as e:
      print("other error:", e) 
