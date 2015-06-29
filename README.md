# opencart-twig
Twig Template Engine For Opencart

Twig is a modern template engine for PHP

<b>Fast:</b> Twig compiles templates down to plain optimized PHP code. The overhead compared to regular PHP code was reduced to the very minimum.

<b>Secure:</b> Twig has a sandbox mode to evaluate untrusted template code. This allows Twig to be used as a template language for applications where users may modify the template design.

<b>Flexible:</b> Twig is powered by a flexible lexer and parser. This allows the developer to define its own custom tags and filters, and create its own DSL.

Installation
============

- Upload the folders and files from the 'upload' directory via FTP to your OpenCart server's main directory. <b>No files will be replaced</b>

- Log into the admin backend,  proceed to Extensions > Installer, click on the Upload button and browse to vanderson_twig_ocmod.xml file.

- Proceed to Extensions > Modifications, and click on the Refresh button located near the top right corner.

- Use <b>$this->load->view('template_path')</b> on controllers to compile with twig, native php templates or both mixed.

- By default, cache is disabled. If you want to use cache, define the path variable on config.php and admin/config.php files:

define('TWIG_CACHE', DIR_CACHE . 'twig');


Documentation
=============

Functions
=========

- link: shortcut for $this->url->link();

{{ link('account/address', {'foo': 'bar', 'another_param': 'another_value', 'SSL'}) }}
<i>// https://yourstore.com/index.php?foo=bar&another_param=another_value</i>
* param 'token' is automaticaly placed


- lang: loads the corrensponding language string

{{ lang('text_yes') }}
<i>// Yes</i>

{{ lang('text_stock', 'product/product') }}
<i>// Availability:</i>


- config: gets config value

{{ config('store_name') }}
<i>// Your Store</i>

{{ config('custom_config', 'custom_filename') }}
<i>// Custom Value loaded from system/config/custom_filename.php</i>


- image: Resize the image and return its url

{{ image('catalog/Your-image.png') }}
<i>// yourstore.com/image/cache/catalog/Your-image-228x228.png</i>
* default size from config_image_product_width and config_image_product_height

{{ image('catalog/Your-image.png', 'popup') }}
<i>// yourstore.com/image/cache/catalog/Your-image-500x500.png</i>
* size from config_image_popup_width and config_image_popup_height

{{ image('catalog/Your-image.png', '', 300, 300) }}
<i>// yourstore.com/image/cache/catalog/Your-image-300x300.png</i>
* custom size


- asset: generate link to the file

{{ asset('javascript/bootstrap.js') }}
* admin or catalog is automaticaly resolved


- load: loads a controller

{{ load('common/content_top') }}


- paginate: render a pagination view
    params:
        total
        limit
        route
        args
        template

{{ paginate(50, 5, 'product/product', {'foo': 'bar'}) }}
<i>// prints default pagination from Pagination->render()</i>

{{ paginate(50, 5, 'product/product', {'foo': 'bar'}, 'custom_template/pagination.twig') }}
<i>// custom pagination template</i>


// Admin only

- can_access: Check if the logged user can access the resource

{% if can_access('user/user_permission') %}
    <i>// Can access the users permissions</i>
{% endif %}


- can_modify: Check if the logged user can modify the resource

{% if can_modify('user/user_permission') %}
    <i>// Can modify the users permissions</i>
{% endif %}


Filters
=======

- money: shortcut for $this->currency->format()
    params:
        currency
        value
        format

{{ product.price|money }}
<i>// US$ 15.95</i>


- tax: shortcut for $this->tax->calculate()

{{ product.price|tax(product.tax_class_id) }}


- len: shortcut for $this->length->format()

{{ product.length|len(product.length_class_id) }}
<i>// 20.53cm</i>


- wei: shortcut for $this->weight->format()

{{ product.weight|wei(product.weight_class_id) }}
<i>// 20.53cm</i>


- truncate: limits the text based on config 'config_product_description_length'

{{ product.description|truncate('...', 50) }}
<i>// Lacus etiam nec amet accumsan mattis nostra. Curae...</i>

- encrypt: shortcut for Encryption->encrypt()

{{ 'foo'|encrypt }}
<i>// SUEfGT636cD1VNzqs-avGhuKx2w4suvPJ18k9qCYdws,</i>


- decrypt: shortcut for Encryption->decrypt()

{{ 'SUEfGT636cD1VNzqs-avGhuKx2w4suvPJ18k9qCYdws,'|decrypt }}
<i>// foo</i>


Globals
=======

This variables are accessible in all twig templates

- document_title
- document_description
- document_keywords
- document_links
- document_styles
- document_scripts
- route
- is_logged

// Admin Only

- user

// Catalog Only

- customer
- affiliate
- is_affiliate_logged
- cart


[![alt tag](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=92R8ND2JM9RBN)