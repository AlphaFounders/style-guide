## Cascading Style Sheets


### Coding conventions

Please refer to [Idiomatic CSS](https://github.com/necolas/idiomatic-css) for style–guides about CSS.


### Inline-block layout

Bootstrap has a grid system based on floats. There exists another grid based on `display: inline-block;`. See an example about [`inline-block` layout](http://s.codepen.io/arkhi/debug/wabPVK).

An implementation can be found in [juwai-admin](https://github.com/juwai/juwai-admin/blob/master/resources/assets/less/inline-align.less)
and the [CSS can be seen online](http://list.juwai.io/juwai-admin/css/inline-align.css).

This style of layout provides the following benefits:

* Allow automatic alignment elements on their baseline (cleaner design).
* Allow easily alignment of elements, both horizontally and vertically, including distributing them evenly on a row.
* Avoid `float` consequences (no more margin collapsing, no more height on the parent element…).

It also has one drawback: **there can't be any space between the columns**:

* This won't work:

    ```html
       <i>something</i> <i>something</i>
    ```
    ```html
       <i>something</i>
       <i>something</i>
    ```
* **This will work (preferred method)**:

    ```html
       <i>something</i><!--
    --><i>something</i>
    ```
* This will work:

    ```html
    <i>something</i><!-- This is not a space --><i>something</i>
    ```
    ```html
    <i>something</i><i>something</i>
    ```


#### Columns

**A row can't have more than 12 columns.**

The layout follows [Bootstrap’s logic](http://getbootstrap.com/css/#grid-options).

Use `.col-i.col-[xs|sm|md|lg]-X + .col-i.col-[xs|sm|md|lg]-Y` while:

* `X` and `Y` are numbers between 1 and 12 included.
* `X + Y ≤ 12`


#### Alignments

Use `.align-[top|middle|baseline|bottom]` to align the columns based on the baseline of the first element.

Use `.align-[left|center|right]` to align the columns to the left, center or right side or their container.

### Quotes

Do not use quotation marks in URI values (url()), if you do need to use the `@charset` rule, use double quotes.

* NOT OK:

    ```css
    @charset UTF-8;

    .sub-user-avatar {
        background-image: url("/images/sub-user-avatar-holder.png");
    }
    .main-user-avatar {
        background-image: url('/images/main-user-avatar.png');
    }
    ```

* OK:

    ```css
    @charset "UTF-8";

    .sub-user-avatar {
        background-image: url(/images/sub-user-avatar-holder.png);
    }
    
    .main-user-avatar {
        background-image: url(/images/main-user-avatar.png);
    }
    ```
