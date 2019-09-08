# Custom Taxonomy Helper Class

## Installation

`composer require horttcore/wp-custom-taxonomy`

## Usage

Extend the abstract class `Taxonomy` and overwrite following methods:

* `getConfig()`
* `getLabels()`

The extending class _MUST_ define protected class variable `slug`
The extending class _MUST_ define protected class variable `postTypes`

### Example

```php
<?php
namespace Foo;

use Horttcore\CustomTaxonomy\Taxonomy;

class Bar extends Taxonomy {

    $slug = 'bar';
    
    $postTypes = ['post'];

    function getConfig(): array
    {
        return [
            'description'        => __('Lorem Ipsum …', 'textdomain'),
            'public'             => false,
            'publicly_queryable' => true,
            'hierarchical'       => false,
            'show_ui'            => true,
            'show_in_menu'       => true,
            'show_in_nav_menus'  => false,
            'show_in_rest'       => true,
            'rest_base'          => 'bars',
            'show_tagcloud'      => true,
            'show_in_quick_edit' => false,
            'show_admin_column'  => true,
            'rewrite'            => [
                'slug'       => _x('bars', 'Taxonomy slug', 'textdomain'),
                'with_front' => false,
            ]
        ];
    }

    function getLabels(): array
    {
        return [
            'name'                       => __('Bars', 'textdomain'),
            'singular_name'              => __('Bar', 'textdomain'),
            'search_items'               => __('Search Bars', 'textdomain'),
            'popular_items'              => __('Popular Bars', 'textdomain'),
            'all_items'                  => __('All Bars', 'textdomain'),
            'parent_item'                => __('Parent Bar', 'textdomain'),
            'parent_item_colon'          => __('Parent Bar:', 'textdomain'),
            'edit_item'                  => __('Edit Bar', 'textdomain'),
            'view_item'                  => __('View Bar', 'textdomain'),
            'update_item'                => __('Update Bar', 'textdomain'),
            'add_new_item'               => __('Add New Bar', 'textdomain'),
            'new_item_name'              => __('New Bar Name', 'textdomain'),
            'separate_items_with_commas' => __('Separate bars with commas', 'textdomain'),
            'add_or_remove_items'        => __('Add or remove bars', 'textdomain'),
            'choose_from_most_used'      => __('Choose from the most used bars', 'textdomain'),
            'not_found'                  => __('No bars found', 'textdomain'),
            'no_terms'                   => __('No bars', 'textdomain'),
            'items_list_navigation'      => __('Bars list navigation', 'textdomain'),
            'items_list'                 => __('Bars list', 'textdomain'),
            'most_used'                  => __('Most Used', 'textdomain'),
            'back_to_items'              => __('&larr; Back to Bars', 'textdomain'),
        ];
    }
}
```
