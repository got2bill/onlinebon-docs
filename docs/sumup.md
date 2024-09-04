# Sumup

## Authentication
The account has to register an account with sumup first.

After he has an sumup account, he can go to the settings page in the web version of onlinebon and login to his account. With this login, he also activates the sumup integration.

For the Authorization of our requests, we are using the *OAuth2.0* method (https://developer.sumup.com/online-payments/introduction/authorization#o-auth-2-0)

After a successfull login, we persist the api `accessToken` and a `refreshToken` in the customer object.
```ts
interface Account {
   sum_up: {
     enabled: boolean
     access_token: string | null
     refresh_token: string | null
     expires_at: boolean | null
   }
}
```

All clients can query the accessToken by using the `/me` endpoint (https://onlinebon.docs.apiary.io/#reference/v2/user/get-logged-in-user). 

The received accessToken is valid for *1 hour*. After that, the application using the accessToken have to create another accessToken using the provided refreshToken (https://developer.sumup.com/online-payments/introduction/authorization#refresh-token-flow).

The new accessToken has to be persisted using the `/v2/accounts/:id` endpoint (https://onlinebon.docs.apiary.io/#reference/v2/accounts/update-an-account).  

## Checkout Web Integration

## Checkout Android Integration
