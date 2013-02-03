# WordPress Custom Meta Field Boxes

### Usage 

For each separate custom meta field box (from here referred to as *cmfb*) you would like, simply add a new array to the '$custom_meta_fields_array' variable.

Key an value pairs can consist of the following:
- id        => the unique identifier for the *cmfb*.
- title     => the title that you will see on the *cmfb*.
- post type => what post type this *cmfb* will be attached to, can be post, page, link, attachment, a custom post type or a combination of these within an array. 
- context   => the physical placement of the *cmfb* within the editor window.
- priority  => the ranking of the *cmfb* within the selected context, can be either high, core, default or low.            

```
	array(
    'id'              => '', 
    'title'           => '',              
    'post_type'       => '', //  
    'context'         => '', // 'normal', 'advanced', or 'side'         
    'priority'        => '', // 'high', 'core', 'default' or 'low'
    'fields'          => array(
      array(
        'type'        => '',
        'id' 	        => '',
      	'label'       => '',
      )
    )  
  )
```