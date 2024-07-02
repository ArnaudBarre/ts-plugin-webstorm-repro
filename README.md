# ts-plugin-webstorm-repro

## Setup

- node_modules have been commited for simplicity
- typescript has been patch with `registerCodeFix({ errorCodes: [61333], getCodeActions: () => undefined });` (see second commit)
- node_modules/dev-plugin is linked via the tsconfig
- you need to restart the TS server after each edit
- ./plugin-logs.txt is generated for simplify debug
- the plugin register a second codefix, 61_334, directly in setup
- the plugin generate two diagnostics: 61_333 for 0-10 range and 61_334 for 0-20 range (numbers are made up, they just need to be different builtin TS codefixes)
- the plugin logs each time `getCodeFixesAtPosition` is being called

## Repro

Go in `./index.ts` and trigger actions on both lines

## Current behaviour (WebStorm 2024.1.5)

Go fixes are available for 61_333 but not 61_334
