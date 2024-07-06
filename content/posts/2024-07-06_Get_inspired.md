---
title: Be inspired or be DESTROYED - daily wholesomeness in your terminal 
date: 2024-07-06T00:00:00
draft: false
tags:
  - Mastodon
  - CLI
  - Inspiration
---

Following this guide, you'll have the latest wholesome mastodon post printed when you open your shell.

**Be inspired or be DESTROYED!**


## Prerequisites
The following applications must be present on the system and in your $PATH:
- `curl`
- `jq`


## Fetching statuses from the terminal
Since the response from Mastodon is delivered as a JSON-array, having `jq` installed will help greatly with parsing the content. Mastodon has support for alt-text on images, and the user `@skeletor@mas.to` is kind enough to provide that with each posted image which makes it trivial to fetch the latest wholesome inspirational quote, even though the quote is images with text. This is accomplished by the following command:

`curl -s https://mas.to/api/v1/accounts/109308492833993188/statuses?limit=1 | jq -r '.[] | .media_attachments[] | select(.description != null) | .description'`


Getting a quote every time your start your terminal with bash is easy enough, just append the line above to your `~/.bashrc`

`echo >> "# Get the latest inspirational quote from @skeletor@mas.to" >> ~/.bashrc`
`echo "curl -s https://mas.to/api/v1/accounts/109308492833993188/statuses?limit=1 | jq -r '.[] | .media_attachments[] | select(.description != null) | .description'" >> ~/.bashrc`

For fish-shell users, a minor modification is needed due to [wildcards-globbing](https://fishshell.com/docs/current/language.html#wildcards-globbing). Your `~/.config/fish/functions/fish_greeting.fish` should have a backward slash to escape the questionmark in the `curl` command, like so:

```sh
function fish_greeting
# Get the latest inspirational quote from @skeletor@mas.to
curl -s https://mas.to/api/v1/accounts/109308492833993188/statuses\?limit=1 | jq -r '.[] | .media_attachments[] | select(.description != null) | .description'
end
```



## Potential improvements
This could be done more elegantly by having it starting as a systemD service and a corresponding timer to fetch the latest content, this would remove the risk of slowing down your session with each start-up if there is no network connectivity to the instance you're fetching content from.

Also, one could render the whole images in a terminal with support for that, but that is outside of scope for this implementation.

## Known limitations
- Posts that lack an alt-text will return `null`, and the won't be displayed.
- If the endpoint cannot be reached, it might cause a slowdown on the startup of the terminal session.


_Thanks to @karin@hachyderm.io who made a [post](https://khendrikse.netlify.app/blog/find-your-mastodon-account-id) on how to find account IDs on Mastodon_.

## Resources
- [Mastodon API-documentation](https://docs.joinmastodon.org/client/public/#posts)
- [How to find account ID](https://khendrikse.netlify.app/blog/find-your-mastodon-account-id/)
