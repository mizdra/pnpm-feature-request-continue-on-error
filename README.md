# pnpm-feature-request-continue-on-run

## Setup

```console
$ pnpm i
```

## `pnpm run lint-by-npm-run-all` (`run-s -c lint:*`)

```console
$ pnpm run lint-by-npm-run-all

> app_name@0.0.0 lint-by-npm-run-all /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
> run-s -c lint:*


> app_name@0.0.0 lint:tsc /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
> tsc

src/runner.ts:4:7 - error TS2322: Type 'number' is not assignable to type 'string'.

4 const a: string = 1;
        ~


Found 1 error in src/runner.ts:4

 ELIFECYCLE  Command failed with exit code 1.

> app_name@0.0.0 lint:eslint /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
> eslint --cache --cache-location node_modules/.cache/eslint/ --cache-strategy content .


> app_name@0.0.0 lint:prettier /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
> prettier --cache --check .

Checking formatting...
All matched files use Prettier code style!
ERROR: "lint:tsc" exited with 1.
 ELIFECYCLE  Command failed with exit code 1.
```

## `pnpm run lint-by-pnpm-run` (`pnpm run --sequential '/lint:[^:]+/'`)

```console
$ pnpm run lint-by-pnpm-run

> app_name@0.0.0 lint-by-pnpm-run /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
> pnpm run --sequential '/lint:[^:]+/'


> app_name@0.0.0 lint:tsc /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
> tsc

src/runner.ts:4:7 - error TS2322: Type 'number' is not assignable to type 'string'.

4 const a: string = 1;
        ~


Found 1 error in src/runner.ts:4

 ELIFECYCLE  Command failed with exit code 1.

> app_name@0.0.0 lint:eslint /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
> eslint --cache --cache-location node_modules/.cache/eslint/ --cache-strategy content .

 ELIFECYCLE  Command failed with exit code 1.
```
