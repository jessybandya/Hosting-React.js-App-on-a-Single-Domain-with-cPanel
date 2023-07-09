# Hosting React.js App on a Single Domain with cPanel

This guide will walk you through the steps to host a React.js app on a single domain using cPanel.

## Prerequisites

- Access to a cPanel hosting account
- Basic understanding of React.js and cPanel file management

## Steps

1. Access cPanel

   - Go to your cPanel login page, usually found at `www.yourdomain.com/cpanel`.
   - Enter your credentials and log in.

2. Upload Build Content

   - Once logged in, navigate to the "File Manager" option.
   - In the "File Manager," open the `public_html` folder.
   - Remove everything in the `public_html` folder.
   - Upload the build content of your React.js app to the `public_html` folder.

3. Add .htaccess File

   - In the root directory (same location as `index.html`), create a new file named `.htaccess`.
   - Open the `.htaccess` file and add the following content:

     ```
     RewriteEngine On
     RewriteCond %{SERVER_PORT} 80
     RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
     
     RewriteBase /
     RewriteRule ^index\.html$ - [L]
     RewriteCond %{REQUEST_FILENAME} !-f
     RewriteCond %{REQUEST_FILENAME} !-d
     RewriteRule . /index.html [L]
     
     # php -- BEGIN cPanel-generated handler, do not edit
     # Set the “ea-php73” package as the default “PHP” programming language.
     <IfModule mime_module>
       AddHandler application/x-httpd-ea-php73 .php .php7 .phtml
     </IfModule>
     # php -- END cPanel-generated handler, do not edit
     ```

   - Save the `.htaccess` file.

4. Access Your React App

   - Open your web browser.
   - Visit `www.yourdomain.com` (replace with your actual domain) in the address bar.

## Conclusion

You have successfully hosted your React.js app on a single domain using cPanel. By uploading the build content and placing the `.htaccess` file in the root directory, you can access your React app by visiting your domain in a web browser.

Please note that this guide provides a basic outline of the hosting process. Depending on your specific cPanel setup and requirements, additional steps or configurations may be necessary.

Make sure to adjust the instructions and paths according to your specific hosting account and React.js app. Feel free to modify and enhance the README as needed to provide more context and information about your hosting environment.
