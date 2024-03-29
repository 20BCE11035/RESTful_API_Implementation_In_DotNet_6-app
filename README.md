# RESTful_API_Implementation_In_DotNet_6-app
RESTful_API_Implementation_In_DotNet_6  - It includes essential details such as `authentication` methods, available `endpoints`, `request` and `response` formats, error handling, and `usage` examples. - This API documentation simplifies the process of `leveraging` external services, fostering efficient and effective software development.

RESTful_API_Implementation_In_DotNet_6

- It includes essential details such as `authentication` methods, available `endpoints`, `request` and `response` formats, error handling, and `usage` examples.
- This API documentation simplifies the process of `leveraging` external services, fostering efficient and effective software development.

---

- ## SECTION 1

  - `Created By`: Selepe Sello
  - This is  the API Implemented using `.NET 6`.
  - The PHP API is in a separate Repository: [RESTful_API_Implementation_In_PHP](https://github.com/TebogoYungMercykay/RESTful_API_Implementation_In_PHP.git)

  ---

---

- ## SECTION 2

  ### These are the Default Users initially in the Database:

  - #### `Default User 1`:

    - `Name`: Test
    - `Surname`: User
    - `Email`: testuser@tuks.co.za
    - `Password`: @TestUser#564
    - `API_key`: a9198b68355f78830054c31a39916b7f
  - #### `Default User 2`:

    - `Name`: John
    - `Surname`: Doe
    - `Email`: johndoe3@gmail.com
    - `Password`: tEst@us5e#hd
    - `API_key`: K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p

    ---

---

- ## SECTION 3

  - All Requests to the `Database` should be Sent via `POST` method for security Purposes.
  - All `API` Request/Response bodies are in the Form of a `JSON` object.
  - The JSON Object Must contain the `type` attribute and some more data, this is so that the requests can be `distinguishable` and `handled` accordingly.
  - The `Database` in Question is a `SQLMicrosoft SQL Server` Database, Tool: `SSMS`.
  - The the `API_keys` on the `database` for sending `requests` to the API are included in `SECTION 1`.
  - #### `Note Well:`

    - All `SENSITIVE` data sent to the api like `passwords`, `usernames/emails` and etc will be `encrypted` from the client side first.
    - Then on the `API`, The Data will be `Decrypted` and `Handled` accordingly.
  - #### `Example Requests:`

    - ###### `SignUp`:

      - ###### Request by User 2:

        ```json
        {
          "type":"signup",
          "signup":{
            "name":"John",
            "surname":"Doe",
            "email":"johndoe3@gmail.com",
            "password":"tEst@us5e#hd",
            "PassConfirmation":"tEst@us5e#hd",
            "account": "default"
          }
        }
        ```
      - ###### Response form API

        ```json
        {
          "status": "success",
          "timestamp": 1680911562,
          "data": "K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p"
        }
        ```
    - ###### `Login`:

      - ###### Request by User 2:

        ```json
        {
          "type":"login",
          "login":{
            "username":"johndoe3@gmail.com",
            "password":"tEst@us5e#hd"
          }
        }
        ```
      - ###### Response form API

        ```json
        {
          "status": "success",
          "timestamp": 1680911562,
          "data": "K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p"
        }
        ```
    - ###### `Logout`:

      - ###### Request by User 2:

        ```json
        {
          "type":"logout",
          "logout":{
            "apikey":"K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p"
          }
        }
        ```
      - ###### Response form API

        ```json
        {
          "status": "success",
          "timestamp": 1680911562,
          "data": "User Successfully Logged Out!"
        }
        ```
    - ###### `Preferences`:

      - ###### Request by User 2:

        ```json
        {
          "type":"preferences",
          "preferences":{
            "apikey":"K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p",
            "theme":"dark",
            "pref":"param"
          }
        }
        ```
      - ###### Response form API

        ```json
        {
          "status": "success",
          "timestamp": 1680911562,
          "data": "Preferences Set Successfully!"
        }
        ```
    - ###### `Delete Account`:

      - ###### Request by User 2:

        ```json
        {
          "type":"delete_account",
          "delete_account":{
            "apikey":"K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p",
            "username":"johndoe3@gmail.com",
            "password":"tEst@us5e#hd"
          }
        }
        ```
      - ###### Response form API

        ```json
        {
          "status": "success",
          "timestamp": 1680911562,
          "data": "Account Deletion Successful!"
        }
        ```
    - ###### `Change Password`:

      - For this request, A user is not allowed to change their username/
      - ###### Request by User 2:

        - ###### `When Logged In:`

          ```json
          {
            "type":"change_password",
            "change_password":{
              "apikey":"K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p",
              "new_password":"tEst@us5e#hd"
            }
          }
          ```
        - ###### `When User is not Logged In:`

          ```json
          {
            "type":"change_password",
            "change_password":{
              "username":"johndoe3@gmail.com",
              "password":"tEst@us5e#hd",
              "new_password":"tEerray@5e#hd"
            }
          }
          ```
      - ###### Response form API

        ```json
        {
          "status": "success",
          "timestamp": 1680911562,
          "data": "Password Changed Successfully!"
        }
        ```
    - ###### `Generate New ApiKey`:

      - For this request, A user is not allowed to change their username/email
      - ###### Request by User 2:

        ```json
        {
          "type":"generate_apikey",
          "generate_apikey":{
            "apikey":"K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p"
          }
        }
        ```
      - ###### Response form API

        ```json
        {
          "status": "success",
          "timestamp": 1680911562,
          "data": "API Key Updated Successfully!"
        }
        ```
    - ###### `Get Data`:

      - ###### Request by User 2:

        ```json
        {
          "type":"get_data",
          "get_data":{
            "apikey":"K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p",
            "limit":4,
            "sort":"id_trim",
            "order": "ASC"
          }
        }
        ```
      - ###### Response form API

        ```json
        {
          "status": "success",
          "timestamp": 1680911562,
          "data": [
            {...},
            {...},
            {...},
            {...}
          ]
        }
        ```
    - ###### `Generate_External_data`:

      - ###### Request by User 2:

        ```json
        {
          "type":"Generate_External_data",
          "Generate_External_data":{
            "apikey":"K9yW8cGnE3qTfR7xV2sZ6bN1mJ4jL5p"
          }
        }
        ```
      - ###### Response form API

        ```json
        {
          "status": "success",
          "timestamp": 1680911562,
          "data": [
            {...},
            {...},
            {...},
            {...},
            {...},
            {...},
            {...}
          ]
        }
        ```

      ---

---

- ## SECTION 4

  - ### How the Sign Up and Login Works:


    - A User must have an account to view the Cars for practical 3, and all the other page.
    - If a `user` doesn't have an account they can only access the `signup`, `login` and `launch` pages.
    - So the `user` will have to `create an account` and `login`.
    - When a `user` submits the signup form, the `'required'` from HTML will make sure all fields are filled,
    - Then `JavaScript` will be loaded, And it will do signup validation on the `client side`.
    - Thereafter, If `javascript` is done, the form will be sent to `validate-signup.php` via `POST`.
    - This is to make sure the request is secured, Then `PHP` will do the validation on the `server side`.
    - Once all the validation is done, the user will be added to the 'users' database table, meaning they will have an account with `Jerman Otto`.
    - `Sign Up Instructions:`
      - All Fields SHOULD not be `Empty`
      - The `NAME` and `SURNAME` fields SHOULD contain only Characters
      - The `EMAIL` SHOULD contain `@gmail.com` or `@tuks.co.za`, and AT LEAST a Character on the LEFT.
      - Make sure the EMAIL doesn't contain `Illegal Characters`
      - Make sure the PASSWORD is at least `8 Characters` long and contains a `Number`, Contains a `Special Character`, `Uppercase` and `Lowercase` letters.
      - Make sure the PASSWORD doesn't contain Illegal Characters
      - The PASSWORD and CONFIRM PASSWORD SHOULD `match`
      - ###### This Is Implemented to make sure the Password is strong and it cannot be guessed or generated easily by Attackers using `Brute Force Attacks` and stuff.

    ---
  - ### How My Encryption Algorithm Works


    - Generate a `RANDOM` int, SALT value between `[2000000000, 2147483646]`.
    - Encrypt PASSWORD using the random number as the `salt` with `sha256` and `hash_pbkdf2` method, `hash_pbkdf2("sha256", p, s, i, b)`;
    - Using 1000 iterations for the hash_pbkdf2 method, and a HASH length of 32 BYTES, So that it can fit well into a column of this `size` => `VARCHAR(128)`.
    - Finally i `Concatenate` the `SALT` and `HASH` and the encode the resulting string to base 64, using `base64_encode()`.

    ---

  - ### API Key


    - The API key is a random string of `length=32`.
    - It Contains these `AlphaNumeric` Characters: `0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ`
    - The Key is then Displayed to the User using a `<p>` tag in every file right after the Heading.

    ---

---

- ## SECTION 5

  - ### Basic Setup Before Running/Interpreting the Codes


    - ### `For Windows:`

      - [Install dotnet 6 on windows 10/11 | Install .Net core 6](https://youtu.be/rASHrGzRxM8?feature=shared)
      - [SQL Server Tutorial For Beginners 2022](https://www.youtube.com/playlist?list=PL82C6-O4XrHfZoh2ZH7-HCPyh9oHeYPnz)
    - ### `For Linux:`

      - [Install .Net 6 Ubuntu | Asp.Net Core 6.0 Runtime Install | Dotnet 6 use on Linux Terminal](https://youtu.be/rASHrGzRxM8?feature=shared)
      - [Installing SQL Server on Linux](https://www.youtube.com/watch?v=GBboALYvvuE)

    ---

    - Random Example for DROPping a Database:
      ```sql
      ALTER DATABASE hack_api_test
      SET SINGLE_USER --or RESTRICTED_USER
      WITH ROLLBACK IMMEDIATE;
      GO
      DROP DATABASE hack_api_test;
      GO
      ```

    - SQL Server Sample Database: [sql-server-sample-database](https://www.sqlservertutorial.net/sql-server-sample-database/)

    ---

---

<p align="center">The End, Thank You</p>

---

---
