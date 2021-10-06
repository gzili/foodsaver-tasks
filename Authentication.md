# User Authentication

It should be possible to implement basic cookie-based authentication by taking clues from this [example](https://github.com/dotnet/aspnetcore/tree/main/src/Security/samples/Cookies) and following this [tutorial](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/cookie?view=aspnetcore-5.0)

## Requirements

- POST `/api/users/register`
  - Receives `CreateUserDto`.
  - Flow
    1. If user with this email already exists, returns `Conflict()`.
    2. Properly hashes the received `password`.
    3. Create a new `User` instance using the hashed password.
    4. Calls the new `User` to the users repository.

- POST `/api/users/login`
  - Receives `LoginUserDto` containing `email` and `password` fields (should be created).
  - Flow
    1. Checks if the user with provided `email` exists in the repository. If it does not, returns `Unauthorized()`.
    2. Executes the neccessary steps to hash the provided password and compare it with password hash in the users repository for the user with provided email.
    3. If hashes do not match, returns `Unauthorized()`.
    4. If hashes match, executes the neccessary steps to correctly sign in the user, such as creating a `ClaimsPrincipal` and calling `HttpContext.SignInAsync` (according to the example and the tutorial). The `ClaimsPrincipal` should contain at least the user's ID to indentify the user on subsequent requests.
    4. After logging in the user, returns `NoContent()`, indicating a successful login. The cookie that identifies the user should be automatically attached to the response by the framework. The cookie becomes the single source of thruth and when this cookie is received by the server, it is assumed that the user is authenticated.

- Use the `[Authorize]` attribute on routes that require an authenticated user. This automatically protects sensitive routes and rejects anonymous requests.

- It should be possible to extract the user ID in controllers from the `HttpContext` property that is automatically provided by the `ControllerBase` class which all controllers extend.

- GET `/api/users` should return the currenty signed in user object without the `password` property or `Unauthorized()`.

- GET `/api/users/logout` should sign out the user if it is currently signed in by calling `HttpContext.SignOutAsync`. This should automatically invalidate the authentication cookie that is attached to the user.
