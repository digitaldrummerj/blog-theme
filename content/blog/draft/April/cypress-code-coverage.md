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

The first step we need to take us to install the npm dependencies that are needed to generate the code coverage reports.

```bash
npm install @cypress/code-coverage @istanbuljs/nyc-config-typescript istanbul-instrumenter-loader istanbul-lib-coverage nyc 
```

*Note:* I you do not already have cypress installed and configured in your project, see?????

## Instrumenting Your Code

 In addition to the code coverage dependencies we need to install the [ngx-build-plus](?????) package so that we can instrument the code when we compile it.
 
> If you aren’t familiar with instrumentation, it is the process of adding tracking statements into your code to be able to measure something which in this case is code coverage. 

By default with the Angular CLI there is no way to inject anything extra into the webpack configuration when you build or serve your application.  If you wanted to inject custom configuration like instrumenting the code, you would have to eject your project from the Angular build system and manage the webpack configuration yourself.  Instead with [ngx-build-plus](?????) you can inject the extra webpack configurations as part of the normal Angular build and serve commands that the Angular CLI provides.

> WARNING: Never run the build with the code coverage instrumentation as your production build.  It will cause major performance issues since it tracks each line of code that is called.

To install Install [npx-build-plus](?????) run: 

```bash
npm install ngx-build-plus
```

Now that we have  [npx-build-plus](?????) installed we need to CONFIGURE our project to use it when the Angular CLI build our code.   The reason we are doing it at build time instead of when serving is because eventually we will be running this from our automated builds where we aren't using `ng serve.

### Adding Webpack Config 



### Updating Angular.json to use ngx-build-plus


## nyc Configuration 

????? What is NYC used for?????

```json
 “nyc”: {
    “extends”: “@istanbuljs/nyc-config-typescript”,
    “all”: true
  }
```

```json
"@cypress/code-coverage": "^1.12.2",
"@istanbuljs/nyc-config-typescript": "^1.0.1",
"cypress": "^4.1.0",
"istanbul-instrumenter-loader": "^3.0.1",
"istanbul-lib-coverage": "^3.0.0",
"ngx-build-plus": "^8.1.3",
"nyc": "^15.0.0"
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

