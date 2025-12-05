# `successfulAuthentication()`
>`successfulAuthentication(user: TokenableUser, context: RouteContext) => Promise<SuccessfulAuthentication>`

This function returns the user metadata along with the JWT token used to authenticate. It can be used to implement alternative signing in methods such as OAuth as ilustrated by these examples:

- [Github OAuth using Aeria](https://github.com/SamCaliman/aeria-github-auth/blob/master/api/src/routes/github.ts)
- [Twitch OAuth using Aeria](https://github.com/SamCaliman/aeria-twitch-auth/blob/master/api/src/routes/twitch.ts)

```ts
type TokenableUser = Pick<User,
  | '_id'
  | 'name'
  | 'email'
  | 'roles'
  | 'active'
  | 'picture'
>

type SuccessfulAuthentication = {
  user: TokenableUser
  token: TokenRecipient
}
```

### Example

The example below will try and retrieve a `user` document from the `customAuthenticate()` function (this function could for example implement OAuth or another authentication method not natively supported by Aeria, such as authenticating an user by it's secret key). In case of success, an `authResult` object is returned wrapped inside a `Result.result` object.

```ts
const { error, result: user } = await customAuthenticate(payload)
if( error ) {
  return Result.error(error)
}

const authResult = successfulAuthentication(user, context)
return Result.result(authResult)
```
