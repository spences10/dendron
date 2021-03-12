---
id: c5f308b8-41bc-469b-8d1b-8bf87a7be01a
title: '12'
desc: ''
updated: 1615563966497
created: 1615554015825
---

## Notes

- direnv the tool I didn't know I needed!
  - install on Fedora 33 with
    ```
    sudo dnf -y install direnv
    ```
  - Zsh config to hook in direnv
    ```
    # direnv
    if [ $(command -v direnv) ]; then
      eval "$(direnv hook zsh)"
    fi
    ```
  - In a new project create a `.envrc` file and add `dotenv` to it to
    load your environment variables
  - Allow the file with `direnv allow`
  - Alias to initialise direnv ini new projects:
    ````
    # direnv
    alias -g di='echo dotenv > .envrc && touch .env && direnv allow'```
    ````

## Links

- Unclutter your .profile with direnv & Updated Environment Variables
  Crash Course: https://www.youtube.com/watch?v=YkxoGRpHcVQ
- How I Automated the Boring with JavaScript, Cloudflare Workers, and
  Airtable: https://www.youtube.com/watch?v=tFQ2kbiu1K4

## Thoughts

## Grateful

## Events
