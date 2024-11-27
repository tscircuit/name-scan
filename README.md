# name-scan

An automatic AI-based scan to make sure variable and function names are good

A cli and github action that scans a github pull request diff for typescript variable names or function names, then
fails if they don't pass a name check.

Every variable name is stored in a database if it's accepted or rejected so that the output is consistent and fast for
subsequent runs. Every variable name is stored with it's type.

There are a set of anti-patterns and a general prompt for checking a variable name. For example, `on<Noun>` for a callback
is considered a bad name, callbacks prefixed with `on` should always be `on<Verb>`

Just because a variable name passes doesn't mean it's good in context, this is just to speed up code reviews.

## HTTP API

This service can be used as an API, just do `POST /namecheck/check_diff_for_bad_names` with `{ diff: string }`. You can get
the diff for any Github pull request by adding ".patch" to the github url at the PR
