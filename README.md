# Routify

A shitty tool to generate processable JSON data for routes.

## Installation

```bash
npm install -g https://github.com/astridlol/routify
```

## Usage

In order to use Routify, you need to add some comments to your routes. Here's a few examples:

```js
// Example 1
/** Allows a user to create an account
 * @route: /accounts/
 * @method: POST
 * @body: { username: string, password: string }
 * @returns: Application/JSON
 * @400: { success: false, error: string }
 * @400: { success: false, error: "Username already exists" }
 * @200: { success: true, ...accountData }
 */

// Example 2

/** Allows a user to log in to an account
 * @route: /accounts/login
 * @method: POST
 * @body: { username: string, password: string }
 * @returns: Application/JSON
 * @401: { success: false, error: "Invalid username or password" }
 * @200: { success: true, token: "token" }
 */

// Example 3

/** Allows viewing of a specific account
 * @route: /account/:UUID
 * @method: POST
 * @params: { UUID: string }
 * @returns: Application/JSON
 * @404: { success: false, error: "Account not found" }
 * @200: { success: true, ...accountData }
 */

```

After that, you can use Routify to generate a JSON file of your routes.

```bash
routify --file [file with routes]
```

By default, the file will be stored in the current directory, and will be named as so: `API-[current-date]`.<br>
In order to change the name of the file, you can use the `--api` flag.
```bash
routify --file [file with routes] --api [what the routes do]
```

## Example

```bash
routify --file routes.js
```

## But, how is this useful?

By itself, Routify is not very useful. However, it can be used as a base for other tools.<br>
Using the data generated by Routify, you can then easily process API data, and use it wherever you need it.<br>
For example, you could easily make a custom documentation site, or a Discord bot to get information on certain routes.<br>

## License
This project is licensed under the MIT license. See the [LICENSE](LICENSE) file for more information.
