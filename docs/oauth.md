YOAuth as Yahoo OAuth
=====================

Before going any further i would like to thank [Darren Kempiners](https://github.com/dkempiners) and [Andrew Martin](https://github.com/almartin82) for their help.

The ***YOAuth*** class is used to generates an oauth *session* which will be used in your requests to the *YQL Service* 

### **Definition**

#### *YOAuth(consumer_key, consumer_secret, \*\*kwargs)*

* ***consumer_key*** : Client Key of your application.
* ***consumer_secret*** : Client Secret of your application
* ***acess_token*** : The Access Token
* ***acess_token_secret*** : The Acess Token Secret
* ***session_handler*** : The OAuth Session Handler which is required when refreshing the token
* ***from_file*** : File containing the credentials.

The **minimum** information required in a ***credentials file***  are the ***consumer_key*** and the ***consumer_secret***.
If ***from_file*** is provided, the class will be instanciated with data within this file.

```python
>>> from myql.contrib.auth import YOAuth
>>> oauth = YOAuth('khdhkfhbb7rit93ffhbfh', 'urysfjue76885hgf')
```

Using a credentials json file

*credentials.json*
```json
{
    "consumer_key" : "khdhkfhbb7rit93ffhbfh",
    "consumer_secret": "urysfjue76885hgf"
}
```

```python
>>> oauth = YOAuth(None, None, from_file=os.path.realpath('credentials.json'))
```

### **Methods**

- #### *OAuth.json_get_data(filename)*

Return a dict containing the credentials

- #### *OAuth.json_write_data(json_data, filename)*

Update the credentials file

- #### *OAuth.token_is_valid()*

Check if the token is still valid

- #### *OAuth.refresh_token()*

Refresh the expired token