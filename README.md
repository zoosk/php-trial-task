# Trial task for PHP developers

Our support team informed us that our users are often using simple passwords like "password123" or "hello" and their accounts are getting hacked. This has to be fixed ASAP, but we have no developers who have time for implementing the changes needed. So *YOU* are our only chance! 💪

Your objective for this task is to build two components:

1. A REST API that receives a password and gives information about its validity based on a set of rules
2. A script that reads the already existing passwords from a database and sets a validity flag based on the response from your API

Please use PHP 7.3 or higher (8 is an option), MySQL (or MariaDB) to implement the trial task and set up your project with [composer](https://getcomposer.org/). You can use any libraries or frameworks you think are necessary or helpful for you, but it helps us a lot if you keep it minimal. We recommend sticking to a coding standard and using a linter of your choice (we recommend [PSR-12](https://www.php-fig.org/psr/psr-12/) and [PHPCSFixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)).

When reviewing your task, we especially value:

- attention to good code and architecture
- consistent styling and not too many typos or commented code
- a good README with instructions on how to run your code

If you have any questions regarding the task, please reach out to us anytime!

## Part 1 - Password validation API

Implement an API that provides an endpoint to validate a password. The endpoint should allow to send a POST request with a password and respond with either a [204](https://httpstatusdogs.com/204-no-content) if the password is fine or with a [400](https://httpstatusdogs.com/400-bad-request) and a set of errors in case the password does not match the minimal password rules. Consult the [Swagger UI in the GitHub page of this project](https://zoosk.github.io/php-trial-task/?url=swagger.yml) for the desired API structure.

All rules to check if a password is valid should be stored in a separate configuration file (JSON, YAML or something else). This file should – at least – include the following information per rule:

- Regular expression to check the rule
- Error message to show in case the rule is not met

A password is valid if:

- it has a minimum length of five characters
- it uses at least one digit
- it does not have more than two repeating consecutive characters (like 'bbb' – two are allowed, but not three or more)
- it includes at least one upper-case character OR one special character (anything that is neither letter nor a number)

## Part 2 - Script for batch-validation of passwords

This repository includes an SQL dump of 200 passwords. Write a CLI script in PHP that reads those passwords from a DB and uses the API you created earlier to validate each of them. It should output a success message or the errors you received from the API for each response.

Additionally the script has to set the `valid` field to 1 or 0 for valid and invalid passwords in the given MySQL table.

Please provide and document a possibility to change the MySQL connection settings used by the script.

## Sending the solution to us

You can choose to send the solution as a ZIP archive (https://git-scm.com/docs/git-archive) or upload it as a private repository to a GIT hoster of your choice, giving us access to it.

We are looking forward to your implementation! 😊