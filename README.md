# poc-skip-ci-pull_request_target

PoC of Skip CI on pull_request_target events.

## Background

[You can skip GitHub Actions workflow runs triggered by the push and pull_request events by including a command in your commit message.](https://docs.github.com/en/actions/managing-workflow-runs-and-deployments/managing-workflow-runs/skipping-workflow-runs)
But unfortunately, skip instructions doesn't apply to the pull_request_target events.
So if you want to skip CI triggered by pull_request_target events, you need to implement the feature yourself somehow.
This repository is a PoC for Skip CI triggered by pull_request_target events. 

## How does it work?

In this repository, you can skip CI by adding a label `skip-ci` to pull requests.
Then jobs except for `skip-ci` and `status-check` are skipped, while `skip-ci` and `status-check` jobs fail.
`status-check` job is a required status check, so you can't merge the pull request normally.
You need to merge it forcibly using admin permission.
This means skip CI needs admin permission.
This restriction is for security reason.

e.g. [#4](https://github.com/suzuki-shunsuke/poc-skip-ci-pull_request_target/pull/4)

## How to skip CI

1. Set a pull request label `skip-ci` and write the reason why you need to skip CI in the pull request
2. Get an approval from someone
3. Merge the pull request forcibly using the admin permission

## Reference

- Japanese
  - https://zenn.dev/shunsuke_suzuki/scraps/25db1238369089
- [Secure GitHub Actions by pull_request_target](https://dev.to/suzukishunsuke/secure-github-actions-by-pullrequesttarget-641)

## LICENSE

[MIT](LICENSE)
