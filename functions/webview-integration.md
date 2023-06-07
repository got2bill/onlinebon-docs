# Webview Integration

## Authentication

To enable the Mobile Apps to authenticate at the Web Application, they can use a custom header called **Webview-Authorization**. They have to provide this header on every page they want to access. This header has to contain a valid **JWT Token** the app got from the API calling the endpoint [POST /authenticate](https://onlinebon.docs.apiary.io/#reference/authentication/authenticate/exchange-credentials-for-token).


## Mobile App / Webview Interactions

Here is a general [documentation](https://developer.android.com/develop/ui/views/layout/webapps/webview#BindingJavaScript) for *Andriod*


### Start / End Session

On the *Dashboard* and on the *completion page* of the webapp, there is link for starting and closing a session. These links should be routing to the App´s Session Page.

```ts
  const goToAppSession = () => {
    AndroidAdminJs.navigateToSession()
  }
```

### Go to POS

In the Admin UI we have a *button at the top that allows the user to navigate directly to the POS Selling Screen*. When in the webview context, this button has to link to the App

```ts
  function goToAppPos() {
      AndroidAdminJs.navigateToCashDesk()
  }
```

### Load Receipt

When the user is using the *receipt database*, he can load a receipt directly into the POS. This receipt has to be opened in the App when in the webview context.

```ts
  function loadReceiptInApp(receiptId: string) {
      AndroidAdminJs.loadReceipt(receiptId)
  }
```

### Toggle Navigation

When using the navigation toggle in the webview context, we want to toggle the navigation of the app.

```ts
  function toggleAppNavigation() {
    AndroidAdminJs.toggleNavigation()
  }
```
