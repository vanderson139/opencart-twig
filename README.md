# opencart-twig
Twig Template Engine For Opencart

Twig is a modern template engine for PHP

<b>Fast:</b> Twig compiles templates down to plain optimized PHP code. The overhead compared to regular PHP code was reduced to the very minimum.

<b>Secure:</b> Twig has a sandbox mode to evaluate untrusted template code. This allows Twig to be used as a template language for applications where users may modify the template design.

<b>Flexible:</b> Twig is powered by a flexible lexer and parser. This allows the developer to define its own custom tags and filters, and create its own DSL.

## Installation

- Upload the folders and files from the 'upload' directory via FTP to your OpenCart server's main directory. <b>No files will be replaced</b>

- Log into the admin backend,  proceed to Extensions > Installer, click on the Upload button and browse to vanderson_twig_ocmod.xml file.

- Proceed to Extensions > Modifications, and click on the Refresh button located near the top right corner.

- Use <b>$this->load->view('template_path')</b> on controllers to compile with twig, native php templates or both mixed.

- By default, cache is disabled. If you want to use cache, define the path variable on config.php and admin/config.php files:

define('TWIG_CACHE', DIR_CACHE . 'twig');


## Documentation

**Functions**

### link
Shortcut for $this->url->link();

> Params:

> * route
> * args
> * ssl

```twig

    {{ link('product/product', { 'foo': 'bar' }, 'SSL') }}
```

* param 'token' is automaticaly placed


## lang
Loads the corrensponding language string

> Params:

> * key
> * file

```twig

    {{ lang('text_yes') }}

    {{ lang('text_stock', 'product/product') }}
```


### config
Gets config value

> Params:

> * key
> * file


```twig

    {{ config('config_name') }}

    {{ config('custom_config', 'custom_file') }}
```

### image
Resize the image and return its url

> Params:

> * path
> * context
> * width
> * height

```twig

    <img src="{{ image('catalog/Your-Image.png') }}" />

    <img src="{{ image('catalog/Your-Image.png', 'thumb') }}" />

```

### asset
Generate link to the file

> Params:

> * path

```twig

    <script src="{{ asset('javascript/bootstrap.js') }}" ></script>

```


### load
Loads a controller

> Params:

> * path

```twig

    {{ load('common/column_left') }}

```


### paginate
Render a pagination view

> Params:

> * total
> * limit
> * route
> * args
> * template

```twig

    {{ paginate(50, 5, 'product/category') }}

    {{ paginate(50, 5, 'product/category', { 'foo': 'bar' }, 'custom_template/pagination.twig') }}

```

## Admin only

### can_access
Check if the logged user can access the resource

> Params:

> * key

```twig

    {% if can_access('user/user_permission') %}

        {#  Can access this resource  #}

    {% endif %}

```


### can_modify
Check if the logged user can modify the resource

> Params:

> * key

```twig

    {% if can_modify('user/user_permission') %}

        {# Can modify this resource #}

    {% endif %}

```

## Filters

### money
Shortcut for $this->currency->format()

> Params:

> * currency
> * value
> * format

```twig

    {{ product.price|money }}

```


### tax
Shortcut for $this->tax->calculate()

> Params:

> * tax_class_id
> * calculate

```twig

    {{ product.price|tax(product.tax_class_id) }}

```


### len
Shortcut for $this->length->format()

> Params:

> * length_class_id
> * decimal_point
> * thousand_point

```twig

    {{ product.length|len(product.length_class_id) }}

```


### wei
Shortcut for $this->weight->format()

> Params:

> * weight_class_id
> * decimal_point
> * thousand_point

```twig

    {{ product.weight|wei(product.weight_class_id) }}

```


### truncate
Limits the text based on config 'config_product_description_length'

> Params:

> * suffix
> * limit

```twig

    {{ product.description|truncate('...', 50) }}

```


### encrypt
Shortcut for Encryption->encrypt()

```twig

    {{ 'foo'|encrypt }}

```


### decrypt
Shortcut for Encryption->decrypt()


```twig

    {{ 'SUEfGT636cD1VNzqs-avGhuKx2w4suvPJ18k9qCYdws,'|decrypt }}

```


## Globals

This variables are accessible in all twig templates

> document_title
> document_description
> document_keywords
> document_links
> document_styles
> document_scripts
> route
> is_logged

### Admin Only

> user

### Catalog Only

> customer
> affiliate
> is_affiliate_logged
> cart


[![alt tag](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=92R8ND2JM9RBN)