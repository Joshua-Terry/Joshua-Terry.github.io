
# API Documentation #

## `register` ##

  curl --header "Authorization: api-key [key]"       \
    --data "email=jake@example.com&password=bananas" \
    https://emailium.com/api/v0/register

And you could expect the server to respond with the following JSON:

  {"already_existed": false, "account_created": true,
   "password_updated": null, "is_cancelled_account": false}

Now, if we have an existing user, we might get some JSON like this:

  {"already_existed": true, "account_created": false,
   "password_updated": false, "is_cancelled_account": false}

## `email-is-registered` ##

   curl --header "Authorization: api-key [key]" \
     "https://emailium.com/api/v0/email-is-registered?email=existing@test.com"

And if the user is registered, the command will return JSON like the following:

  {"is_registered":true}

## `credentials-are-valid` ##

To test whether a particular username/password pair are valid:

  curl --header "Authorization: api-key [key]" \
    "https://emailium.com/api/v0/credentials-are-valid?email=joe@test.com&password=bananas"

And that will give back some JSON like this:

  {"is_valid":false}

## `is-valid` ##

  curl --header "Authorization: api-key [key]"         \
    --data "email=jon@example.com&new-password=abc123" \
    https://emailium.com/api/v0/change-password

