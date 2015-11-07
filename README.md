# ansible-nginx-unicorn-rails
Ansible playbook for deploying Rails with Unicorn on nginx on Ubuntu

## Assumptions
- `remote_user` does everything: checkout, deploy, etc.
- single `nginx` Rails app
- `unicorn` socket and PID locations (see `templates/unicorn-config`)

## Vars
`remote_user`: deploying user, needs somewhat permissive `sudo`

`rbenv_url`: git URL for `rbenv`

`rbenv_path`: desired path for `rbenv`

`ruby_build_url`: git URL for `ruby-build`

`ruby_build_path`: ...

`ruby`: path to Ruby interpreter

`ruby_version`: desired Ruby version

`ruby_path`: path to Ruby version

`ruby_bin`: path to installed Ruby binaries

`gem_install`: just a shortcut

`app_name`: name of your app (really just an identifier for configs)

`app_path`: where your app will be installed

`app_git_url`: git URL for your app's repo

`app_env`: Rails environment name for your app

## NOTES
- really only works with a single Rails app as the default `nginx` site is clobbered
- clobbers `remote_user`'s `.bash_profile`
- clobbers the repo's `config/unicorn.rb` in favor of a template (see `templates/unicorn-config`)
- `rake` stuff isn't working at the moment (no migrations)

