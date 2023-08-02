# Werkzeug Console PIN Cracker
Generates all possible PIN combinations using below possible combinations!

```
Module Name      Application Name
-------------------------------------
flask.app      - wsgi_app
werkzeug.debug - DebuggedApplication
flask.app      - Flask
```

# Background - How does the PIN generate?
First we need to understand how the pin is generated. There are a few slight differences depending on version but the general flow is as follows.

1. Take the username of the user running the Flask application.
2. Take the module name of the Flask application.
3. Take the application name of the Flask application.
4. Take the path to the Flask app.py file.
5. Take the output of uuid.getnode(), which is the MAC address of the network interface hosting the application, in decimal form.
6. Take the ID from /etc/machine-id.
7. On newer systems, combine the ID from /etc/machine-id with the last part of the value from /proc/<pid>/cgroup, split on the / character.
8. Concatenate all of the above values into a single string.
9. Take the MD5 hash or SHA1 hash of the concatenated string.
10. Encode the resulting digest as a 9-digit decimal number, with hyphens inserted every 3 digits.


Reference: https://www.bengrewell.com/cracking-flask-werkzeug-console-pin/
