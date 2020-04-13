---
categories: ["Cypress", "Testing", "Angular"]
date: 2020-04-12T00:00:00Z
draft: true
title: Add Code Coverage to Your Cypress Tests
series: ["Code Coverage"]
---

In part 1 of the series we talked about why you need code coverage so you aren't testing in the dark and can make data-driven decisions on if you have actually tested your code the way you think you have.

In part 2 of the series on code coverage, we are going to add code coverage reports to our [Cypress](https://cypress.io) tests for our Angular UI.   The Angular UI we will be using is the Todo Application that gets created when I run my [Angular workshop](https://digitaldrummerj.me/workshop/angular)???????

For this article,  we are going to be generating the code coverage report using  the Cypress UI.  In our next installment in the series we will add it to our automated builds.  

## Get The Code

You can find the code for this article at [https://github.com/digitaldrummerj/angular-workshop](https://github.com/digitaldrummerj/angular-workshop)???????


## Dependencies

```json
"@cypress/code-coverage": "^1.12.2",
"@istanbuljs/nyc-config-typescript": "^1.0.1",
"cypress": "^4.1.0",
"istanbul-instrumenter-loader": "^3.0.1",
"istanbul-lib-coverage": "^3.0.0",
"ngx-build-plus": "^8.1.3",
"npm-run-all": "^4.1.5",
"nyc": "^15.0.0",
"source-map-support": "^0.5.16",
```

## nyc TeamCity Config

```json
 "nyc": {
    "extends": "@istanbuljs/nyc-config-typescript",
    "all": true
  }
```

## npm scripts

```json
"start": "ng serve",
"cy:open": "cypress open --env coverage=true"
```

