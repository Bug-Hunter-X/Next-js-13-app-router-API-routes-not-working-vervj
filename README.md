# Next.js 13 app router API routes not working

This repository demonstrates a bug in Next.js 13's App Router where API routes defined in the `pages/api` directory do not work as expected and return a 404 error.

## Bug Description

When using the App Router in Next.js 13, API routes defined under the `pages/api` directory return a 404 error instead of the expected JSON response. This issue occurs even with the simplest of API routes.

## Reproduction Steps

1. Create a new Next.js 13 app.
2. Create a file at `pages/api/hello.js` with the following content:
   ```javascript
   //pages/api/hello.js
   export default function handler(req, res) {
     res.status(200).json({ name: 'John Doe' });
   }
   ```
3. Start the development server.
4. Try accessing `/api/hello` in your browser. You should see a 404 error instead of the expected JSON response.

## Solution

The issue is likely due to a mismatch between the way the API routes are defined and the way the App Router handles them.  The solution is to use the new `app` directory structure and place the api route inside that directory.  The correct directory should be `app/api/hello.js`

## Additional Notes

This issue is specific to Next.js 13 and its App Router. Previous versions of Next.js do not have this problem.
