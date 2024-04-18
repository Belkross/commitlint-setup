# Introduction

This repository intends to show how to setup a commit message linter that will be triggered everytime someone do a
commit. This example runs with my personnal commitlint config (@belkross/commitlint-config).

# Commit linter (local)

1. Install dependencies: `npm install --save-dev commitlint @belkross/commitlint-config husky`

2. Link commitlint with the config:

   1. Create a **_commitlint.config.ts_** file

   2. Add this line in it: `export default { extends: ["@belkross/commitlint-config"] }`

3. Create a commit-msg hook

   1. Initialize husky `npx husky init`

   2. Delete the **_pre-commit_** file in the folder **_.husky_** (if you don’t need it)

   3. Create a file called **_commit-msg_** in the folder **_.husky_**

   4. Add this script in it: `npx --no -- commitlint --edit $1`
   
## MacOS oneline command

Copy and paste the following command in your terminal

```
pnpm install --save-dev commitlint @belkross/commitlint-config husky &&
touch commitlint.config.ts &&
echo "export default { extends: [\"@belkross/commitlint-config\"] }" >> commitlint.config.ts && 
npx husky init && 
touch ./.husky/commit-msg && 
echo -e "echo \"\\\n *** checking commit message with commitlint\\\n\"\nnpx --no -- commitlint --edit $1" >> ./.husky/commit-msg
```

# Commit terminal helper

1. Install dependencies: `npm install --save-dev commitizen @commitlint/cz-commitlint`

2. Link the commitlint config with commitizen

   1. Add this code to the **_package.json_**: `"config": { "commitizen": { "path": "@commitlint/cz-commitlint" } }`

3. Add a commit script to **_package.json_**: `"commit": "npx cz"`
