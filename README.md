# WordPress Custom Meta Field Boxes

### Usage 

For each separate custom meta field box (from here referred to as **cmfb**) you would like, simply add a new array to the `$custom_meta_fields_array` variable.

```
array(
  'id'              => '', 
  'title'           => '',              
  'post_type'       => '', 
  'context'         => '',        
  'priority'        => '',
  'fields'          => array(
    array(
      'type'        => '',
      'id' 	        => '',
    	'label'       => '',
    )
  )  
)
```

Key and value pairs can consist of the following:

#### ID
The unique identifier for the **cmfb**. Defaults to *custom_meta_field_box*. Any **cmfb** that has the same ID as the one that precedes it, with overwrite that one.

#### Title
The title that you will see on the **cmfb**. Defaults to *Custom Meta Field Box*.

#### Post Type
What post type this **cmfb** will be attached to, can be 'post', 'page', 'link', 'attachment', the slug of a custom post type or a combination of these within an array. Defaults to 'post'.

#### Context
The physical placement of the **cmfb** within the editor window. Can be either 'normal', 'advanced', or 'side'. Defaults to 'advanced'.
 
#### Priority
The ranking of the **cmfb** within the selected context, can be either 'high', 'core', 'default' or 'low'.            

For example:

```
array(
  'id'              => '', 
  'title'           => '',              
  'post_type'       => '', 
  'context'         => '',        
  'priority'        => '',
  'fields'          => array(
    array(
      'type'        => '',
      'id' 	        => '',
    	'label'       => '',
    )
  )  
)
```