```
❯ yarn c8:plain
yarn run v1.22.4
$ c8 --reporter none -- node -r source-map-support/register -e 'require("./lib/src/foo").bad()'

${pwd}/src/foo.ts:2
  throw new Error("bad");
        ^
${pwd}/lib/src/foo.js:5
    throw new Error("bad");
    ^

Error: bad
    at Object.bad (${pwd}/src/foo.ts:2:9)
    at [eval]:1:26
    at Script.runInThisContext (vm.js:132:18)
    at Object.runInThisContext (vm.js:309:38)
    at internal/process/execution.js:77:19
    at [eval]-wrapper:6:22
    at evalScript (internal/process/execution.js:76:60)
    at internal/main/eval_string.js:23:3
error Command failed with exit code 1.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
```

```
❯ yarn nycissue
yarn run v1.22.4
$ nyc --require source-map-support/register --cache false --source-map --produce-source-map --exclude-after-remap false --reporter none -- node --enable-source-maps -r source-map-support/register -e 'require("./lib/src/foo").bad()'

${pwd}/lib/src/foo.js:2
exports.__esModule = true;
                                                                                                                                                                                                                                                           ^
${pwd}/lib/src/foo.js:2
cov_2aaleuslda=function(){return actualCoverage;};}return actualCoverage;}cov_2aaleuslda();cov_2aaleuslda().s[0]++;exports.__esModule=true;cov_2aaleuslda().s[1]++;exports.bad=void 0;function bad(){cov_2aaleuslda().f[0]++;cov_2aaleuslda().s[2]++;throw new Error("bad");}cov_2aaleuslda().s[3]++;exports.bad=bad;//# sourceMappingURL=foo.js.map
                                                                                                                                                                                                                                                     ^

Error: bad
    at Object.bad (${pwd}/lib/src/foo.js:2:252)
    at [eval]:1:26
    at Script.runInThisContext (vm.js:132:18)
    at Object.runInThisContext (vm.js:309:38)
    at internal/process/execution.js:77:19
    at [eval]-wrapper:6:22
    at evalScript (internal/process/execution.js:76:60)
    at internal/main/eval_string.js:23:3
error Command failed with exit code 1.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
```
