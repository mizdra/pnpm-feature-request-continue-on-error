# pnpm-feature-request-continue-on-error

## Setup

```console
$ pnpm i
```

## `pnpm exec run-s --continue-on-error "lint:*"`

```console
$ pnpm exec run-s --continue-on-error "lint:*"

> app_name@0.0.0 lint:tsc
> tsc

src/runner.ts:4:7 - error TS2322: Type 'number' is not assignable to type 'string'.

4 const a: string = 1;
        ~


Found 1 error in src/runner.ts:4


> app_name@0.0.0 lint:eslint
> eslint --cache --cache-location node_modules/.cache/eslint/ --cache-strategy content .


> app_name@0.0.0 lint:prettier
> prettier --cache --check .

Checking formatting...
All matched files use Prettier code style!
ERROR: "lint:tsc" exited with 1.
```

## `pnpm run --sequential "/lint:[^:]+/"`

```console
$ pnpm run --sequential "/lint:[^:]+/"

> app_name@0.0.0 lint:tsc /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
> tsc

src/runner.ts:4:7 - error TS2322: Type 'number' is not assignable to type 'string'.

4 const a: string = 1;
        ~


Found 1 error in src/runner.ts:4

 ELIFECYCLE  Command failed with exit code 1.

> app_name@0.0.0 lint:eslint /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
> eslint --cache --cache-location node_modules/.cache/eslint/ --cache-strategy content .
```

## `pnpm run "/lint:[^:]+/"`

```console
$ pnpm run "/lint:[^:]+/"
. lint:tsc$ tsc
│ src/runner.ts(4,7): error TS2322: Type 'number' is not assignable to type 'string'.
└─ Failed in 453ms at /Users/mizdra/src/github.com/mizdra/pnpm-feature-request-continue-on-run
. lint:eslint$ eslint --cache --cache-location node_modules/.cache/eslint/ --cache-strategy content .
└─ Running...
. lint:prettier$ prettier --cache --check .
│ Checking formatting...
│ All matched files use Prettier code style!
└─ Done in 201ms
 ELIFECYCLE  Command failed with exit code 1.
```
