Debbie 
==========
Fully based on the amazing work of [@nixme][nixme] (Gopal Patel) on his gem [**Jazz Hands**][jazz_hands]

__**We only removed some stuff that we're not using it**__

---

Spending hours in the rails console? Spruce it up and show off those
hard-working hands!

**debbie** is an opinionated set of console-related gems and a bit of glue:

* [**Pry**][pry] for a powerful shell alternative to IRB.
* [**Awesome Print**][awesome_print] for stylish pretty print.
* [**Hirb**][hirb] for tabular collection output.
* [**Pry Rails**][pry-rails] for additional commands (`show-routes`,
  `show-models`, `show-middleware`) in the Rails console.
* [**Pry Stack Explorer**][pry-stack_explorer] to navigate the call stack and
  frames.
* [**Pry Remote**][pry-remote] to connect remotely to a Pry console.
* [**Pry Byebug**][pry-byebug] Adds step, next, finish and continue commands and breakpoints to Pry using byebug.
* [**Coolline**][coolline] & [**Coderay**][coderay] for syntax highlighting as
  you type. _Optional. MRI 1.9.3/2.0.0 only_

## To-Do

* [**Simple log time profiler**][simple-log-time] Add a Simple Ruby Profiler for logging time consume in stuff


## Usage

Ruby 2+, Rails 3 or 4 only. Add to your project Gemfile:

```ruby
group :development, :test do
  gem 'debbie'
end
```

That's it. Run `bundle` and then `bundle exec rails c` as usual.

[Hirb][hirb] isn't enabled by default. To use, run `Hirb.enable` in the console.

Ruby compiled against a proper readline library, ideally GNU readline, is
recommended. Alternatively, [`gem install rb-readline`][rb-readline] for an
acceptible backup. Using ruby compiled against a `libedit` wrapper (primarily OS
X) will work but is not recommended.


## Options

Change the following options by creating an initializer in your Rails project
Example `config/initializers/debbie.rb`:

```ruby
if defined?(Debbie)
  Debbie.colored_prompt = false
  Debbie.enable_syntax_highlighting_as_you_type!
end
```

### `colored_prompt`

Color the console prompt? Defaults to `true` when the current ruby is compiled
against GNU readline or `rb-readline`, which don't have issues counting
characters in colored prompts. `false` for libedit.

Note: `Pry.color = false` trumps this setting and disables all console coloring.

### `prompt_separator`

Separator string between the application name and line input. Defaults to `»`
for GNU readline or libedit. Defaults to `>` for `rb-readline` which fails on
mixed encodings.

### Syntax highlighting

Syntax highlighting as you type via [Coolline][coolline] and [Coderay][coderay]
is disabled by default due to slightly buggy behavior. To enable, add
`Debbie.enable_syntax_highlighting_as_you_type!` to the initializer. Only
works with MRI 1.9.3 or 2.0.0.


## Contributing

Patches and bug reports are welcome. Just send a [pull request][pullrequests] or
file an [issue][issues]. [Project changelog][changelog].

[nixme]:              https://github.com/nixme
[jazz_hands]:         https://github.com/nixme/jazz_hands
[pry]:                http://pry.github.com
[awesome_print]:      https://github.com/michaeldv/awesome_print
[hirb]:               https://github.com/cldwalker/hirb
[pry-rails]:          https://github.com/rweng/pry-rails
[pry-remote]:         https://github.com/Mon-Ouie/pry-remote
[pry-stack_explorer]: https://github.com/pry/pry-stack_explorer
[coolline]:           https://github.com/Mon-Ouie/coolline
[coderay]:            https://github.com/rubychan/coderay
[rb-readline]:        https://github.com/luislavena/rb-readline
[pullrequests]:       https://github.com/goodpeople/debbie/pulls
[issues]:             https://github.com/goodpeople/debbie/issues
[changelog]:          https://github.com/goodpeople/debbie/blob/master/CHANGELOG.md
[simple-log-time]:    http://www.pablocantero.com/blog/2014/08/17/quick-and-dirty-simple-ruby-profiler/
[pry-byebug]:         https://github.com/deivid-rodriguez/pry-byebug
