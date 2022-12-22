# myrepo
Sites Crash !💔

Blame not self too much? 🔐

A website vulnerability is a software bug, system misconfiguration, or some other weakness in the website its components and processes. This could cause unauthorized access and critical risk to the organizational assets.

How can I fix it? Let's jump on this with examples of websites with vulnerabilities!

http://testphp.vulnweb.com

List of Vulnerabilities and Coding Solutions:

Blind SQL Injection

Cross-site scripting

Directory traversal

PHP allow_url_fopen enabled (AcuSensor)

Script source code disclosure

SQL injection

http://testhtml5.vulnweb.com

List of Vulnerabilities:

AngularJS client-side template injection

Cross-site scripting

DOM-based cross-site scripting

http://testaspnet.vulnweb.com

List of Vulnerabilities:

Blind SQL Injection

Cross-site scripting

SQL injection

Microsoft IIS tilde directory enumeration

Unicode transformation issues

User-controllable script source

Blind SQL Injection

The best option is to use prepared queries, also known as parameterized statements, dealing with SQL queries that contain user input. Parameterized queries allow the database to understand which parts of the SQL query should be considered as user input, therefore solving SQL injection.

DECLARE ?account AS STRING = "Rundofase"

SELECT account, SUM(order_total)
  FROM central_office_orders
 WHERE account = ?account
 GROUP BY account

Cross-site scripting (XSS)

The correct way to prevent XSS attacks is to validate user input and ensure that data rendered by templates is escaped, to apply context-dependent encoding and/or validation of user input rendered on a page.

Encoding - Replace ALL control characters with known safe alternatives

Positive validation (whitelist) - Only allow a specific set of values

Negative validation (blacklist) - Block a specified list of dangerous values

In cases where positive validation is used, it should also be coupled with additional sanitization. For example, when allowing certain HTML tags, certain attributes of those tags should be removed, such as event handlers.

<?php
echo '<div>' . htmlspecialchars($_GET['input']) . '</div>';
// or
echo '<div>' . filter_input(INPUT_GET, 'input', FILTER_SANITIZE_SPECIAL_CHARS) . '</div>';

SQL injection

The only sure way to prevent SQL Injection attacks is input validation and parametrized queries including prepared statements, sanitising all input, not only web form inputs such as login forms, removing potential malicious code elements such as single quotes, grouping one or more SQL statements into a logical unit to create an execution plan and avoiding administrative privileges

CREATE TABLE `salary` (
		  `empid` int(11) NOT NULL,
		  `sal` int(11) DEFAULT NULL,
		  PRIMARY KEY (`empid`)
		) ENGINE=InnoDB DEFAULT CHARSET=utf8;

Unicode transformation issues

Identify the source of these Unicode transformation issues and fix them. If wrong encoding is sent, identification can go wrong, and receiving data will go wrong.

It's important to do this at the very start of the, as the parsing of the HTML may have to start again if the encoding it's currently using is wrong.

<html lang="en">
<head>
  <meta charset="utf-8">
</head>

User-controllable script source

The script should properly sanitize user input. Do not allow user input to control script source location references. In Javascript, runtime protection will guard against debugging and code tampering attacks, for example, Jscrambler Code Integrity

Microsoft IIS tilde directory enumeration

Discard all web requests using the tilde character and add a registry key, especially before reaching the IIS server and running an update on the latest version of the .NET framework would be a preferable solution.

AngularJS client-side template injection

It should not be possible for an attacker to inject AngularJS expressions by using curly braces. The application needs to either treat curly braces {{}} in user input as highly dangerous or avoid server-side reflection of user input entirely.

DOM-based cross-site scripting

The script should filter metacharacters from user input, likewise, Through the use of trusted types.

anElement.innerHTML = aTrustedHTML;

el.textContent = '';
const img = document.createElement('img');
img.src = 'xyz.jpg';
el.appendChild(img);

Directory traversal

The script should filter metacharacters from user input. Validation of user input before processing it, Ideally, the validation should compare against a whitelist of permitted values. The application should append the input to the base directory and use a platform filesystem API to canonicalize the path. Giving appropriate permissions to directories and files, processing URI requests that do not allow file request

Example of code to validate the canonical path of a file based on user input:

File file = new File(BASE_DIRECTORY, userInput); if (file.getCanonicalPath().startsWith(BASE_DIRECTORY)) { // process file }

PHP allow_url_fopen enabled (AcuSensor)

Disable allow_url_fopen from either php.ini (for PHP versions newer than 4.3.4) or .htaccess (for PHP versions up to 4.3.4).

Script source code disclosure

Analyze the source code of this script and solve the problem. Access to source code can be restricted with different code version control systems.

In conclusion, tools that detect website vulnerabilities can also be used to test such as Acunetix

mmmkmk
