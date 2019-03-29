# Content of the chapter:
- introduction to the theme.php
- creating a theme manually
- creating a theme configuration


## How to create theme programaticaly
### file creation
- go to themes/Frontend
- create a theme folder, e.g. GregAdvance
- create a Theme.php in a new theme folder (relative path: GregAdvance/Theme.php)
- create a theme preview file called preview.png (133x98px) and place in theme folder (relative path: GregAdvamce/preview.png). This file will be visible in backend (backend path: configuration->theme manager)
### code for Theme.php file
```
<?php

namespace Shopware\Themes\GregAdvanced;  //namespace has to be the same like theme folder name

use Shopware\Components\Form;   

class Theme extends \Shopware\Components\Theme //required class
{
    protected $extend = 'Responsive'; //extend from reponsive theme
    protected $name = 'Greg Advanced Theme'; //what user will see in the backend, text will be displayed
    protected $description = 'This is a long description field';
    protected $author = 'gReg';
    protected $license = '';


    //create custom theme configuration (simple version)
    public function createConfig(Form\Container\TabContainer $container)
    {
        $tab = $this->createTab('first_tab', 'My First Tab', []); //args: name, title, array of options (optional)

        $fieldset = $this->createFieldSet('first_fieldset', 'My Fieldset'); //args: name, title

        $textField = $this->createTextField('first_text_field', 'Text Field', 'Default Value', []);  //args: name, title, default value, array of options(optional)

        $fieldset->addElement($textField); //attach field to the fieldset

        $tab->addElement($fieldset); //attach fieldset to the tab

        $container->addTab($tab); //attach tab to the main container
    }
}
```