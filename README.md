# WordPress Custom Meta Field Boxes

> Quickly add custom meta field boxes to any post type

For more information about registering meta field boxes http://codex.wordpress.org/Function_Reference/add_meta_box.

This class works well with the [WordPress Custom Post Type class](https://github.com/beaucharman/wordpress-custom-post-type). They were made for each other <3.

### Declaring New Custom Meta Field Boxes

Include `custom-meta-field-boxes.php` in your `functions.php` file.

Declare the various argument arrays to setup the new custom meta field box (from here referred to as **cmfb**):

```php
$args = array(
  'id'              => '',
  'title'           => '',
  'post_type'       => '', // 'post', 'page', 'link', 'attachment' a custom post type slug, or array
  'context'         => '', // 'normal', 'advanced', or 'side'
  'priority'        => '', // 'high', 'core', 'default' or 'low'
  'fields'          => array(
    array(
      'type'        => '',
      'id'          => '',
      'label'       => ''
    )
  )
);
```

Then create an instance of the LT3_Custom_Meta_Field_Box class:

```php
new LT3_Custom_Meta_Field_Box( $args );
```

For the above arguments, key and value pairs can consist of the following:

**ID**

The unique identifier for the **cmfb**. Defaults to *custom_meta_field_box*. Any **cmfb** that has the same ID as the one that precedes it, with overwrite that one.

**Title**

The title that you will see on the **cmfb**. Defaults to *Custom Meta Field Box*.

**Post Type**

What post type this **cmfb** will be attached to, can be 'post', 'page', 'link', 'attachment', the slug of a custom post type or a combination of these within an array. Defaults to 'post'.

**Context**

The physical placement of the **cmfb** within the editor window. Can be either 'normal', 'advanced', or 'side'. Defaults to 'advanced'.

**Priority**

The ranking of the **cmfb** within the selected context, can be either 'high', 'core', 'default' or 'low'.

**Fields**

Add an array for each meta field to be added to the current **cmfb**.

### Currently available custom field types

**text**

**textarea**

**checkbox**

**select**

**post_select**

**term_select**

**radio**

**post_checkbox**

**image**

**file**

### Constants

Make sure to correctly set these following constants within `custom-meta-fields-box.php`:

```php

define('LT3_DEVELOPMENT_MODE', true);
define('LT3_FULL_SCRIPTS_PATH', 'script/path'); // for the file and image upload scripts
define('LT3_FULL_IMAGES_PATH', 'images/path'); // for the image placeholder

```

### Scripts

This class requires the folowing two scripts.

**cmfb-file-upload.js**

```javascript

/**
 * Custom Meta Field Boxes File Upload
 * ========================================================================
 * cmfb-file-upload.js
 * @license MIT license
 * ======================================================================== */
(function ($) {
  $('.custom_upload_file_button').click(function () {
    var $formField = $(this).siblings('.custom_upload_file');
    tb_show('Select a File', 'media-upload.php?type=image&TB_iframe=true');
    window.send_to_editor = function (html) {
      var $fileUrl = $(html).attr('href');
      $formField.val($fileUrl);
      tb_remove();
    };
    return false;
  });
  $('.custom_clear_file_button').click(function () {
    $(this)
      .parent()
      .siblings('.custom_upload_file')
      .val('');
    return false;
  });
}(jQuery));

```

**cmfb-image-upload.js**

```javascript

/**
 * Custom Meta Field Boxes Image Upload
 * ========================================================================
 * cmfb-image-upload.js
 * @license MIT license
 * ======================================================================== */
;(function($) {
  $('.custom_upload_image_button').click(function () {
    var imgUrl, classes, id;
    var formField = $(this).siblings('.custom_upload_image');
    var preview   = $(this).siblings('.custom_preview_image');
    tb_show('', 'media-upload.php?type=image&TB_iframe=true');
    window.send_to_editor = function (html) {
      imgUrl  = $('img',html).attr('src');
      classes = $('img', html).attr('class');
      id      = classes.replace(/(.*?)wp-image-/, '');
      formField.val(id);
      preview.attr('src', imgUrl);
      tb_remove();
    };
    return false;
  });
  $('.custom_clear_image_button').click(function () {
    var defaultImage = $(this).parent().siblings('.custom_default_image').val();
    $(this).parent().siblings('.custom_upload_image').val('');
    $(this).parent().siblings('.custom_preview_image').attr('src', defaultImage);
    return false;
  });
})(jQuery);

```

#### Change log
- Added a marker next to each label that contains the fields key within development mode.

#### Depedencies
- jQuery
