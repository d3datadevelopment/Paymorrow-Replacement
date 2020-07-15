# Paymorrow replacement if module is not used

This package removes the unused OXID Paymorrow module package from the shop and prevents conflicts in later updates.

## Install

if the Paymorrow module is not used and should be removed from the shop installation

* Deactivate the Paymorrow module in the shop backend.
* Run this composer statement in your shop. Adjust this instruction if your installation requires it.

    `composer require d3/oxid-paymorrow-replacement --update-no-dev`
    
* Manually remove the files from source/modules/oxps/paymorrow.
* OXID eShop 6.2 only:

    ```
    composer require -n oxid-esales/oxideshop-update-component oxid-esales/developer-tools --update-no-dev
    vendor/bin/oe-console oe:module:reset-configurations
    vendor/bin/oe-console oe:oxideshop-update-component:install-all-modules
    composer remove -n oxid-esales/oxideshop-update-component oxid-esales/developer-tools --update-no-dev
    ```
    
    Please ignore "not readable file" message.

## Uninstall

if the Paymorrow module is to be used again

* Manually clean up the replacement module entry (d3/oxid-paymorrow-replacement) from the vendor/composer/installed.json and composer.lock files.
* Run this composer statement in your shop. Adjust this instruction if your installation requires it.

    `composer remove d3/oxid-paymorrow-replacement --update-no-dev`
