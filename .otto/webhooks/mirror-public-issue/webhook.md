---
event: issues
action: opened
repo: m2de/otto
title: "Mirror public issue #{{issue.number}}"
permissionMode: bypassPermissions
model: sonnet
persistent: true
maxTurns: 20
effort: low
---

A user has opened an issue on the public Otto repo (`m2de/otto`). The source code lives in the private monorepo `m2de/cc-project`, so your job is to mirror this issue there — labelled `otto-public` — so it can be picked up and fixed. That's the whole task: mirror it, nothing more.

Original issue:

- Number: #{{issue.number}}
- URL: {{issue.html_url}}
- Reporter: @{{issue.user.login}}
- Title: {{issue.title}}

Body:

```
{{issue.body}}
```

First, check whether a mirror already exists — webhooks can be re-delivered:

```
gh issue list -R m2de/cc-project --state all --label otto-public --limit 300 --json number,url,body \
  --jq '[.[] | select(.body | contains("m2de/otto/issues/{{issue.number}}")) | .url] | join(", ")'
```

Filter client-side like this rather than with `--search`: GitHub's search index strips URL punctuation, so searching for the issue URL silently returns nothing. If anything comes back, stop and report that it's already mirrored.

Otherwise create the mirrored issue with `gh issue create -R m2de/cc-project --label otto-public`. Keep the original title. In the body, include the original text and an attribution line linking {{issue.html_url}} and naming the reporter — that link is what the duplicate check above matches on, so the full `m2de/otto/issues/{{issue.number}}` URL must appear verbatim. Use your judgement on presentation: strip issue-template boilerplate and empty sections if they add noise, and note anything about the report that looks unclear or missing.

Do not touch the public issue — no comments, labels, or edits. Do not investigate or attempt a fix, and do not open a PR. Report the new issue URL and finish.
