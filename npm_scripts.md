---
marp: true
---

# npm scripts
---

## There are 2 types scripts in `package.json`

- [Life Cycle Scripts](https://docs.npmjs.com/cli/v9/using-npm/scripts#life-cycle-scripts)
    - prepare, prepublish, prepublishOnly, prepack, postpack, dependencies
- customized by users in `scripts` property in `package.json` file

---

# Pre and Post Scripts

```JSON
{
  "scripts": {
    "precompress": "{{ executes BEFORE the `compress` script }}",
    "compress": "{{ run command to compress files }}",
    "postcompress": "{{ executes AFTER `compress` script }}"
  }
}
```

### In this example npm run compress would execute these scripts as described.

---

# What does npm do when executing `npm run xxx`

- reads the corresponding command line from package.json
- prepares the environment
- invokes sh and gives it the command and the env.

---

  - `PATH`: npm adds the node_modules/.bin directory to your PATH environment variable, which allows you to run executables installed by your project's dependencies without needing to specify their full path
   - `npm_package_xxx` environment variables: YOUR PACKAGE's name, version based on `package.json`
   - `npm_config_xxx` environment variables:
        ```shell
       PS D:\MyProjects\npm-test> npm run my-val --VAL=TRUE
        > npm-test@1.0.0 my-val
        > echo "TEST-BOOLEAN-VAL: %npm_config_VAL%"
        "TEST-BOOLEAN-VAL: TRUE"
        ```
   - npm also changes the current working directory to the root directory of your project before executing the script. This ensures that any relative paths used in the script are resolved correctly.


---

# Why we use npm scripts?
> One of the benefits of using npm scripts is that they can be easily shared and reused by other developers, making it easy to create and maintain a consistent workflow across different projects. Additionally, npm scripts can be run on different platforms and environments, making it easy to automate your workflows and ensure consistent results across different environments.
