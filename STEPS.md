## 1 - Analysis before deployment
Initially before deploying any code, I have gone through the codebase to review the code for inconsistensies/improvements. These have been as follows:

**Login.html**
- `<label for="passwrd">` changed into `<label for="password">`
RATIONALE: A small typo; the label should match the correct name of the defined input field

**application.py**
- `users = connection.execute("SELECT * FROM users").fetchall()` into `users = connection.execute("SELECT username, password FROM users").fetchall()`
RATIONALE: Minimalizing data exposure; to authenticate, we don't need ALL data from a user. We only need their username and password.

- `app.logger.info(f"the user '{username}' logged in successfully {password}")` into `app.logger.info(f"the user '{username}' logged in successfully")`
RATIONALE: No need to log/display the password typed in; the user will know their password and/or can use recovery mechanisms if they forgot

- app.logger.warning(f"the user '{ username }' failed to log in {password}") into `app.logger.warning(f"the user '{ username }' failed to log in")`
RATIONALE: No need to log/display the password typed in; the user will know their password and/or can use recovery mechanisms if they forgot