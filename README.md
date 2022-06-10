# OAuth Invision Community Signin Component for React

This component provides a sign in button for Invision Community Forums. Users are presented with a button that says 'Sign in with Invision' and when they click the button they are forwarded to Invision to authenticate the React app.

## Pull the repo	

Clone this repo into the components folder 

```bash
cd <react_project_root>/src/components
git clone https://github.com/gcoulby/invision-auth-react.git
```

## Import the component

Import the component into your project with the following command from the terminal

```js
import { InvisionSignin } from "components/invision-auth-react/invision-auth-react";
```

## Include the component in your project

The component has three exposed properties `community_url`, `client_id`, `scopes`.

| Parameter     | Format                                             |
| ------------- | -------------------------------------------------- |
| community_url | https://example.com (without forward slash on end) |
| client_id     | 429c5cc1a82example5b5074155a7b26                   |
| scopes        | ["profile", "email"]                               |

and are implemented like this:

```js
function App() {
  return (
    <div className="App">
      <InvisionSignin
        community_url="https://example.com"
        client_id="429c5cc1a82example5b5074155a7b26"
        scopes={["profile", "email"]}
      />

[...]
```

## Styling the component

Each element and sub-element in the rendered component can be styled. The following styles can be changed:

| Style                           | Use                                |
| ------------------------------- | ---------------------------------- |
| *.invision_button*              | Outer div for the whole component  |
| *.invision_button_signout*      | the div for the signout button     |
| *.invision_button_photo*        | the photo displayed when signed in |
| *.invision_button_signout_text* | the text displayed when signed in  |
| *.invision_button_signin*       | the div for the signin button      |
| *.invision_button_icon*         | the icon displayed when signed out |
| *.invision_button_signin_text*  | the text displayed when signed out |

## Auth Flow

The following auth flow is implemented to enable Role Based Access Control (RBAC) on clientside React applications. This OAuth flow demonstrates how client-side applications (e.g. React) should be configured to authenticate users with Invision OAuth authentication. 

Frontend pages views can be configured using Role Based Access Control (RBAC). However, the user can edit their clientside data to make themselves e.g. 'Staff lead/Management/Owner'. So you must NEVER server protected content in the frontend without serverside authentication. This example shows how the frontend would pass the invision access token to the backend API, which forwards the access_token to invision, this validates whether the user has access to this content before serving the content to the user.



![https://i.imgur.com/lJEzFML.png](https://i.imgur.com/lJEzFML.png)



> REMEMBER: Never trust the client in client-side apps, anything important should be authenticated server-side before being served to the client. 



