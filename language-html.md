## HyperText Markup Language

Please refer to [Idiomatic HTML](https://github.com/necolas/idiomatic-html) for
style–guides about HTML.

### Addendum

#### Line length and quotes

* Line length must be no longer than __120 characters__ (only exclusion is translation files)
* Developer has to use double quotes inside tags.
* Blade syntax should be with single quotes only.

#### Attributes order

`name` and `id` are often related. Keep them together, so that we have:
```html
<input class="location" id="galaxy-name" name="galaxy[name]"
    data-id="123456789"
    placeholder="Which galaxy does your world belong to?"
    value="Milky way"
>
```

#### Self-closing tags (void elements):

In the HTML 5 specification the `/` character is valid but has no effect for void elements such as `<br />, <hr />, <img />, <input />`.
So in our Rabbit team we decided not to close such void elements , i.e.
```html
<img class="my-class" id="void-element"
    src="please-do-not-use-slash-to-close-this-element"
>

#### Multi–lines

* Elements written on multi-lines MUST have their __attributes indented with 4
  spaces__: It is easier to use linters when indentation is consistent.
* Elements written on multi-lines MUST have the closing bracket of the opening
  tag __aligned with its opening bracket__: Because we’re using 4 spaces
  indentation, the aligned attributes would be aligned with the following code,
  which makes it harder to read.
* __No need__ to put every tag's property on the new line

Example (void element):

```html
<input class="hello" id="galaxy"
    placholder="Which galaxy does your world belong to?"
    value="Milky way"
>
```

Example for tags with content:
```html
<a class="btn btn-default"
    id="and-this-is-long-id" name="this-is-tag-name"
    href="{{ route('submittable-cases') }}"
>
    Some text for the link
</a>
```

Example (no attributes, short text):
```html
<tr>
    <td>I'm too short to split me</td>
</tr>
```

####Indentation for blade syntax

* Always use intendations for __Blade__ constructions
* We should follow PHP style guide, when we are using __Blade__ constructins. For instance:
    * Space between opening command and bracket (`@for (` etc.). (only exclusion for `@section(), @push()` etc).
    * Allways use strict equality check: `===`, not `==`
    * Spaces around dot when we use concatenation.

```html
@section('sidebar')
    @parent

    <p>This is appended to the master sidebar.</p>
    @for ($i...)
        <div class="some-div">
            @if ($sectionTitle === 'extra')
                <span>Some extra title</span>
            @endif
            <p>Some very smart text.</p>
        </div>
    @endfor

    @include('partial.name', [
        'paramNumber1' => 'this one ' . $isConcatenated . 'with that one',
        'paranNumberLonger2' => 'no need to align array elements assigment',
    ])
@endsection

```
