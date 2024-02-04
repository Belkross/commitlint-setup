# Introduction

This repository intends to show how to setup a commit message linter that will be triggered everytime someone do a
commit. This example runs with my personnal commitlint config (@belkross/commitlint-config).

# Steps

1. install dependencies: `npm install --save-dev commitlint @belkross/commitlint-config husky`
2. link commitlint with the config:
   1. create a **_commitlint.config.ts_** file
   2. add `module.exports = { extends: ["@belkross/commitlint-config"] }` in it
3. create a commit-msg hook
   1. init husky `npx husky init`
   2. delete the **_pre-commit_** file in the folder **_.husky_**
   3. create a file called **_commit-msg_** in the **_.husky_** folder
   4. add this script `npx --no -- commitlint --edit $1` in it
