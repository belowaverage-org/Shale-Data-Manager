# Shale Data Manager

Shale Data Manager is an array storage system using flat file storage. Shale works in layers.

This text you see here is *actually* written in Markdown! To get a feel for Markdown's syntax, type some text into the left window and watch the results in the right.

### Version
1.5.6

### Functions

* **Array** = loadDB(**String** *location*) - Loads an array from a location *See more about location sytax below*.
* **Array** = listDB(**String** *location*) - Lists all databases inside a location.
* **Boolean** = putDB(**Array** *Data*, **String** *location*) - Saves array into a location. Returns true if successful.
* **Boolean** = dropDB(**String** *location*) - Deletes a database from a location. Returns true if successful.
### Function Usage
```php
$data = loadDB('place\of\data'); //These are the folders the data will be stored in seperated by backslashes. Think of it as a map of where your data is. $data will contain an array of the database.
```
```php
$arrayofdatabases = listDB('place\of'); //Lets pretend inside the folder (place\of) there are 3 databases named "data", "ashleymadison", "profiles".

foreach($arrayofdatabases as $database) {
    echo 'Database name: '.$database.', And all of its data:<br>';
    print_r(loadDB('place\of\\'.$database));
}
/* May return something like this

    Database name: data, And all of its data:
    Array
    (
        [a] => apple
        [b] => banana
        [c] => Array
            (
                [0] => x
                [1] => y
                [2] => z
            )
    )
    And will then cycle through "ashleymadison" and then "profiles"
*/
```
```php
$data = array(
    "a" => "apple",
    "b" => "banana",
    "c" => array(
        "x",
        "y",
        "z"
    )
);

putDB($data, 'place\of\data'); //Will place the contents of $data into the database at the specified location of 'place\of\data'.
```
### Encryption Functions
Functions below are used by the functions above unless specified otherwise.
* **String** = encrypt(**String** *Data*, **String** *Encryption Key*) - Encryption key must be 16/24/32 characters long. Encrypts string into an encrypted string.
* **String** = decrypt(**String** *Data*, **String** *Encryption Key*) - Unencrypts the encrypted string.

### Installation
```php
require('shaledatamanager.lib.php');
```
