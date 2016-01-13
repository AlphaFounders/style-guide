Currently we only force everyone add JIRA story number at the beginning of the commit message.

For a good commit message, I think we could improve in several aspects:

## Content

+ First, suggest try to use `git commit` instead of `git commit -m`, which will open a new editor
+ Put a title to explain what you are doing in this commit
+ Put more descriptions in the new paragraph

Example from @arkhi:
```
[JA-55] Live and let die :gun::
* [JS] Add quantity of items per product removed.
* [JS] Add support for asynchronous events for GTM.
* [JS] Handle clicks with event delegation.
* Add some doumentation.
* Fix `list` properties for enhancements in listing packages pages.
* Fix asynchronous event for removeFromCart.
* Fix structure of the products property.
* Handle cart update.
* Handle Franchisees by setting `variant: 'franchisee'`.
* Handle Recommendation pages.
* Make the numbering of clicks optional.
* Move hardcoded URL for Recommendation PDF into config.
* Move removeFromCart event from the decrease button to the remove button.
* Rename `$recommend` to `$jpid` in `productRecommend()`.
* Rename `JW.addToCart` to `JW.updateCart`.
* Rename `npd_packages` to `developer_packages` in config.
* When increasing or decreasing items for a product, have the minimum value set to 1 by default.
```

And you will notice that every commit have a lot of details, which is good for us to understand what he has done in this PR.

Also, it's a good place to record our effort in these commits, then when you create the PR, you can easily summarize all your work.

## Sort commits (Optional)

Sometimes we have a lot of commits in one PR, and some of the commits is just  one or two line change, doesn't have a lot of meaning.

Since we are using Fork-PR mode, I suggest before we open the PR, try to re-organize our commits, just leave the useful commit point there.

For more information, please ref to https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History#Squashing-Commits
