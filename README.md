# Custom Taxonomy Helper Class

## Installation

`composer require horttcore\wp-custom-taxonomy`

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
            'name'                       => __('Bars', 'email-collector'),
            'singular_name'              => __('Bar', 'email-collector'),
            'search_items'               => __('Search Bars', 'email-collector'),
            'popular_items'              => __('Popular Bars', 'email-collector'),
            'all_items'                  => __('All Bars', 'email-collector'),
            'parent_item'                => __('Parent Bar', 'email-collector'),
            'parent_item_colon'          => __('Parent Bar:', 'email-collector'),
            'edit_item'                  => __('Edit Bar', 'email-collector'),
            'view_item'                  => __('View Bar', 'email-collector'),
            'update_item'                => __('Update Bar', 'email-collector'),
            'add_new_item'               => __('Add New Bar', 'email-collector'),
            'new_item_name'              => __('New Bar Name', 'email-collector'),
            'separate_items_with_commas' => __('Separate bars with commas', 'email-collector'),
            'add_or_remove_items'        => __('Add or remove bars', 'email-collector'),
            'choose_from_most_used'      => __('Choose from the most used bars', 'email-collector'),
            'not_found'                  => __('No bars found', 'email-collector'),
            'no_terms'                   => __('No bars', 'email-collector'),
            'items_list_navigation'      => __('Bars list navigation', 'email-collector'),
            'items_list'                 => __('Bars list', 'email-collector'),
            'most_used'                  => __('Most Used', 'email-collector'),
            'back_to_items'              => __('&larr; Back to Bars', 'email-collector'),
        ];
    }
}
```
