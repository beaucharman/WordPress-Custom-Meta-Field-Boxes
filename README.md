# WordPress Custom Meta Field Boxes

For more information about registering meta field boxes http://codex.wordpress.org/Function_Reference/add_meta_box

This class works well with the [WordPress Custom Post Types class](https://github.com/beaucharman/wordpress-custom-post-types). They were made for each other <3.

### Declaring New Custom Meta Field Boxes

Include `custom-meta-field-boxes.php` in your `functions.php` file.

Declare the various argument arrays to setup the new custom meta field box (from here referred to as **cmfb**):

```
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

Then create a variable (for future reference, but is not required) from an instance of the LT3_Custom_Meta_Field_Box class:

```
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

### Current **cmfb** types

**text**

**textarea**

**checkbox**

**select**

**post_select**

**term_select**

**radio**

**post_checkbox**

**file**

