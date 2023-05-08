# dm-api-account
No description provided (generated by Openapi Generator https://github.com/openapitools/openapi-generator)

This Python package is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project:

- API version: v1
- Package version: v1
- Build package: org.openapitools.codegen.languages.PythonClientCodegen

## Requirements.

Python >= 3.6

## Installation & Usage
### pip install

If the python package is hosted on a repository, you can install directly using:

```sh
pip install dm-api-account --extra-index-url https://nexus.s.o3.ru/repository/pypi-all/simple/

OR

pip install git+https://github.com/GIT_USER_ID/GIT_REPO_ID.git
```
(you may need to run `pip` with root permission: `sudo pip install git+https://github.com/GIT_USER_ID/GIT_REPO_ID.git`)

Then import the package:
```python
import dm_api_account
```

### Setuptools

Install via [Setuptools](http://pypi.python.org/pypi/setuptools).

```sh
python setup.py install --user
```
(or `sudo python setup.py install` to install the package for all users)

Then import the package:
```python
import dm_api_account
```

## Getting Started

Please follow the [installation procedure](#installation--usage) and then run the following:

```python

import time
import structlog
import dm_api_account
from pprint import pprint
from dm_api_account.api import account_api
from dm_api_account.model.bad_request_error import BadRequestError
from dm_api_account.model.change_email import ChangeEmail
from dm_api_account.model.change_password import ChangePassword
from dm_api_account.model.general_error import GeneralError
from dm_api_account.model.registration import Registration
from dm_api_account.model.reset_password import ResetPassword
from dm_api_account.model.user_details_envelope import UserDetailsEnvelope
from dm_api_account.model.user_envelope import UserEnvelope
# Defining the host is optional and defaults to http://localhost
# See configuration.py for a list of all supported configuration parameters.
configuration = dm_api_account.Configuration(
    host = "http://localhost"
)



# init log
structlog.configure(
    processors=[
        structlog.processors.JSONRenderer(indent=4, sort_keys=True, ensure_ascii=False)
    ]
)

# Enter a context with an instance of the API client
with dm_api_account.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = account_api.AccountApi(api_client)
    token = "token_example" # str | Activation token
x_dm_auth_token = "X-Dm-Auth-Token_example" # str | Authenticated requests require X-Dm-Auth-Token header. You can get the data from POST /account/ method, sending login and password in \"token\" response field (optional)
x_dm_bb_render_mode = "X-Dm-Bb-Render-Mode_example" # str | Requests with user defined texts that allows usage of BB-codes may be rendered differently by passing the X-Dm-Bb-Render-Mode header of one of following values Html, Bb, Text, SafeHtml (optional)

    try:
        # Activate registered user
        api_response = api_instance.activate(token, x_dm_auth_token=x_dm_auth_token, x_dm_bb_render_mode=x_dm_bb_render_mode)
        pprint(api_response)
    except dm_api_account.ApiException as e:
        print("Exception when calling AccountApi->activate: %s\n" % e)
```

## Documentation for API Endpoints

All URIs are relative to *http://localhost*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*AccountApi* | [**activate**](docs/AccountApi.md#activate) | **PUT** /v1/account/{token} | Activate registered user
*AccountApi* | [**change_email**](docs/AccountApi.md#change_email) | **PUT** /v1/account/email | Change registered user email
*AccountApi* | [**change_password**](docs/AccountApi.md#change_password) | **PUT** /v1/account/password | Change registered user password
*AccountApi* | [**get_current**](docs/AccountApi.md#get_current) | **GET** /v1/account | Get current user
*AccountApi* | [**register**](docs/AccountApi.md#register) | **POST** /v1/account | Register new user
*AccountApi* | [**reset_password**](docs/AccountApi.md#reset_password) | **POST** /v1/account/password | Reset registered user password
*LoginApi* | [**v1_account_login_all_delete**](docs/LoginApi.md#v1_account_login_all_delete) | **DELETE** /v1/account/login/all | Logout from every device
*LoginApi* | [**v1_account_login_delete**](docs/LoginApi.md#v1_account_login_delete) | **DELETE** /v1/account/login | Logout as current user
*LoginApi* | [**v1_account_login_post**](docs/LoginApi.md#v1_account_login_post) | **POST** /v1/account/login | Authenticate via credentials


## Documentation For Models

 - [BadRequestError](docs/BadRequestError.md)
 - [BbParseMode](docs/BbParseMode.md)
 - [ChangeEmail](docs/ChangeEmail.md)
 - [ChangePassword](docs/ChangePassword.md)
 - [ColorSchema](docs/ColorSchema.md)
 - [GeneralError](docs/GeneralError.md)
 - [InfoBbText](docs/InfoBbText.md)
 - [LoginCredentials](docs/LoginCredentials.md)
 - [PagingSettings](docs/PagingSettings.md)
 - [Rating](docs/Rating.md)
 - [Registration](docs/Registration.md)
 - [ResetPassword](docs/ResetPassword.md)
 - [User](docs/User.md)
 - [UserDetails](docs/UserDetails.md)
 - [UserDetailsEnvelope](docs/UserDetailsEnvelope.md)
 - [UserEnvelope](docs/UserEnvelope.md)
 - [UserRole](docs/UserRole.md)
 - [UserSettings](docs/UserSettings.md)


## Documentation For Authorization

 All endpoints do not require authorization.

## Author




## Notes for Large OpenAPI documents
If the OpenAPI document is large, imports in dm_api_account.apis and dm_api_account.models may fail with a
RecursionError indicating the maximum recursion limit has been exceeded. In that case, there are a couple of solutions:

Solution 1:
Use specific imports for apis and models like:
- `from dm_api_account.api.default_api import DefaultApi`
- `from dm_api_account.model.pet import Pet`

Solution 2:
Before importing the package, adjust the maximum recursion limit as shown below:
```
import sys
sys.setrecursionlimit(1500)
import dm_api_account
from dm_api_account.apis import *
from dm_api_account.models import *
```

