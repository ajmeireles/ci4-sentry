# CodeIgniter 4 & Sentry

---

### Introduction
This repository gives you a way (perhaps the only one!) to overwrite CodeIgniter 4's system log to throw exceptions to the Sentry.io. Setting it up is very easy, follow the tutorial below without skipping any steps.

### CodeIgniter 4 Compatibility
``4.1.4``

### Installation

1. Install Sentry PHP SDK:

``` bash
composer require sentry/sdk
```

2. Clone the repository:

``` bash
git clone git@github.com:ajmeireles/ci4-sentry.git app/ThirdParty/Sentry
```

3. Rewrite the CodeIgniter 4 Logger loader:

Edit: ``app/Config/Autoload.php`` and insert this line:


``` php
$classmap = [
    'CodeIgniter\Log\Logger' => APPPATH . 'ThirdParty/Sentry/Logger.php',
];
```

3. IN ``.env`` of CodeIgniter 4 create a new variable called: ``sentryDSN`` and insert your Sentry DNS

### Use

**All exceptions thrown by CodeIgniter 4 will be automatically sent to Sentry** also with the value `ENVIRONMENT` so you can create alert specific to the type of environment (development or production) of your CodeIgniter 4 application.