# Sabre Get Booking Authorization & Token Authentication on Postman

This guide provides a step-by-step process for authenticating and obtaining a token for the **Sabre Get Booking Collection** using Postman. 
While [Sabre Dev Studio](https://developer.sabre.com/) is detailed on this, I had issues because the different sections are scattered/disjointed in various places. 

So I focused on pulling from those sources, personally walking through these steps, and creating a guide specifically tailored to developers who want to try out Sabre APIs in a limited manner on Postman, but lack proper Sabre credentials. 

## Step 1: Login to the Sabre Dev Studio Platform
- Visit [Sabre Dev Studio](https://developer.sabre.com/) and **log in** (or **sign up** if you don’t have an account).  
- Click your **profile** at the top-right corner and select **Applications**.  

## Step 2: Obtain Your User ID and Password
- In the **Applications** section, retrieve your **User ID** and **Password**.  

## Step 3: Generate Your Authorization Header
- Visit the [REST API Token Guide](https://developer.sabre.com/guides/travel-agency/developer-guides/rest-apis-token-credentials).  
- Follow the instructions to create your **authorization header** by:
  1. Concatenating your `USER_ID` and `PASSWORD` with a colon (`:`):
     ```
     USER_ID:PASSWORD
     ```
  2. Encoding the result in **Base64**.

- Example:
  ```
  USER_ID:PASSWORD → Base64 encode → VjE6Mnd0eXdvNm44MXE0Mzg3djpERVZDRU5URVI6RVhU
  ```

## Step 4: Set Up Your Postman Test Environment
- Import the **Environment file** and **Booking Management collection** by following the setup guide:  
  [Sabre Postman Collection Setup](https://github.com/SabreDevStudio/postman-collections/blob/master/Booking-Management/README.md).

## Step 5: Select the Authentication Request
- Open **Postman** and navigate to **Booking Management API collection**.
- Locate the **Authentication** folder.
- Select **REST Authorize**.

## Step 6: Configure the Headers
- In the **Headers** section, set:

  ```plaintext
  Content-Type: application/x-www-form-urlencoded
  Authorization: Basic <your_base64_encoded_value_from_Step_3>
  ```

- Example:

  ```plaintext
  Authorization: Basic VjE6Mnd0eXdvNm44MXE0Mzg3djpERVZDRU5URVI6RVhU
  ```

## Step 7: Set the Request Body & Send the Request
- In the **Body** section, ensure this parameter is set:

  ```plaintext
  grant_type=client_credentials
  ```

- Click **Send**.

## Step 8: Verify the Response
- A **200 OK** response confirms successful authentication.
- The response body contains:

  ```json
  {
    "access_token": "your_generated_token",
    "token_type": "Bearer",
    "expires_in": 1800
  }
  ```

- Use this token for API requests within its validity period.
