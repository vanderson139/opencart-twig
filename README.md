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

[![alt tag](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=92R8ND2JM9RBN)