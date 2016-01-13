## HyperText Markup Language

Please refer to [Idiomatic HTML](https://github.com/necolas/idiomatic-html) for
style–guides about HTML.

### Addendum

#### Attributes order

`name` and `id` are often related. Keep them together, so that we have:
```html
<input class="location" id="galaxy-name" name="galaxy[name]"
    data-id="123456789"
    placeholder="Which galaxy does your world belong to?"
    value="Milky way"
>
```

#### Multi–lines

- Elements written on multi-lines MUST have their **attributes indented with 4
  spaces**: It is easier to use linters when indentation is consistent.
- Elements written on multi-lines MUST have the closing bracket of the opening
  tag **aligned with its opening bracket**: Because we’re using 4 spaces
  indentation, the aligned attributes would be aligned with the following code,
  which makes it harder to read.

Example:

```html
<input class="hello" id="galaxy"
    placholder="Which galaxy does your world belong to?"
    value="Milky way"
>
```
