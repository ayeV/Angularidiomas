# Angularidomas

pasos a seguir
Comandos....
ng g c componentes/login

ng add @angular/localize

 en el html del login...
<body class="text-center">
    <form class="form-signin">
      <div class="text-center mb-4">
            <img class="mb-4"  i18n-title title="Your LOGO"  src="https://svgsilh.com/svg/67861-03a9f4.svg" alt="" width="72" height="72">
  
        <h1 i18n="titulo de Bienvenida" class="h3 mb-3 font-weight-normal">Please sign in</h1>
         </div>
  
      <div class="form-label-group">
        <input type="email" i18n id="inputEmail" class="form-control" i18n-placeholder="Email address" placeholder="Email address" required="" autofocus="">
        <label for="inputEmail" i18n="label email">Email address</label>
      </div>
  
      <div class="form-label-group">
        <input type="password" id="inputPassword" class="form-control" placeholder="Password"
        i18n-placeholder="Password" required="">
        <label for="inputPassword" i18n="label Password" >Password</label>
      </div>
  
      <div class="checkbox mb-3">
        <label>
          <input type="checkbox"  i18n="label remember-me" value="remember-me"> Remember me
        </label>
      </div>
      <button class="btn btn-lg btn-primary btn-block" type="submit" i18n="Sign in">Sign in</button>
      <p class="mt-5 mb-3 text-muted text-center">© 2020</p>
    </form>
  
  
  </body>
 
en el css del login...
html,
body {
    height: 100%;
}

body {
    display: -ms-flexbox;
    display: -webkit-box;
    display: flex;
    -ms-flex-align: center;
    -ms-flex-pack: center;
    -webkit-box-align: center;
    align-items: center;
    -webkit-box-pack: center;
    justify-content: center;
    padding-top: 40px;
    padding-bottom: 40px;
    background-color: #f5f5f5;
}

.form-signin {
    width: 100%;
    max-width: 330px;
    padding: 15px;
    margin: 0 auto;
}

.form-signin .checkbox {
    font-weight: 400;
}

.form-signin .form-control {
    position: relative;
    box-sizing: border-box;
    height: auto;
    padding: 10px;
    font-size: 16px;
}

.form-signin .form-control:focus {
    z-index: 2;
}

.form-signin input[type="email"] {
    margin-bottom: -1px;
    border-bottom-right-radius: 0;
    border-bottom-left-radius: 0;
}

.form-signin input[type="password"] {
    margin-bottom: 10px;
    border-top-left-radius: 0;
    border-top-right-radius: 0;
}

    en el index.html...
    
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">




    Comando 
    ng xi18n --output-path src/idiomas --out-file traducciones.en.xlf

    copiar el archivo para cada idioma

    cambios en angular json>
    ...configurations":
    ..."serve":

{
    "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
    "version": 1,
    "newProjectRoot": "projects",
    "projects": {
        "idiomas": {
            "projectType": "application",
            "schematics": {},
            "root": "",
            "sourceRoot": "src",
            "prefix": "app",
            "architect": {
                "build": {

                    "builder": "@angular-devkit/build-angular:browser",
                    "options": {
                        "outputPath": "dist/idiomas",
                        "index": "src/index.html",
                        "main": "src/main.ts",
                        "polyfills": "src/polyfills.ts",
                        "tsConfig": "tsconfig.app.json",
                        "aot": true,
                        "assets": [
                            "src/favicon.ico",
                            "src/assets"
                        ],
                        "styles": [
                            "src/styles.css"
                        ],
                        "scripts": []
                    },
                    "configurations": {
                        "en": {
                            "aot": true,
                            "outputPath": "dist/en/",
                            "i18nFile": "src/idiomas/traducciones.en.xlf",
                            "i18nFormat": "xlf",
                            "i18nLocale": "en"
                                //"i18nMissingTranslation": "error"
                        },
                        "es": {
                            "aot": true,
                            "outputPath": "dist/es/",
                            "i18nFile": "src/idiomas/traducciones.es.xlf",
                            "i18nFormat": "xlf",
                            "i18nLocale": "es"
                                //,"i18nMissingTranslation": "error"
                        },
                        "production": {
                            "fileReplacements": [{
                                "replace": "src/environments/environment.ts",
                                "with": "src/environments/environment.prod.ts"
                            }],
                            "optimization": true,
                            "outputHashing": "all",
                            "sourceMap": false,
                            "extractCss": true,
                            "namedChunks": false,
                            "extractLicenses": true,
                            "vendorChunk": false,
                            "buildOptimizer": true,
                            "budgets": [{
                                    "type": "initial",
                                    "maximumWarning": "2mb",
                                    "maximumError": "5mb"
                                },
                                {
                                    "type": "anyComponentStyle",
                                    "maximumWarning": "6kb",
                                    "maximumError": "10kb"
                                }
                            ]
                        }
                    }
                },
                "serve": {
                    "builder": "@angular-devkit/build-angular:dev-server",
                    "options": {
                        "browserTarget": "idiomas:build"
                    },
                    "configurations": {
                        "production": {
                            "browserTarget": "idiomas:build:production"
                        },
                        "en": {
                            "browserTarget": "idiomas:build:es"
                        },
                        "es": {
                            "browserTarget": "idiomas:build:en"
                        }
                    }
                },
                "extract-i18n": {
                    "builder": "@angular-devkit/build-angular:extract-i18n",
                    "options": {
                        "browserTarget": "idiomas:build"
                    }
                },
                "test": {
                    "builder": "@angular-devkit/build-angular:karma",
                    "options": {
                        "main": "src/test.ts",
                        "polyfills": "src/polyfills.ts",
                        "tsConfig": "tsconfig.spec.json",
                        "karmaConfig": "karma.conf.js",
                        "assets": [
                            "src/favicon.ico",
                            "src/assets"
                        ],
                        "styles": [
                            "src/styles.css"
                        ],
                        "scripts": []
                    }
                },
                "lint": {
                    "builder": "@angular-devkit/build-angular:tslint",
                    "options": {
                        "tsConfig": [
                            "tsconfig.app.json",
                            "tsconfig.spec.json",
                            "e2e/tsconfig.json"
                        ],
                        "exclude": [
                            "**/node_modules/**"
                        ]
                    }
                },
                "e2e": {
                    "builder": "@angular-devkit/build-angular:protractor",
                    "options": {
                        "protractorConfig": "e2e/protractor.conf.js",
                        "devServerTarget": "idiomas:serve"
                    },
                    "configurations": {
                        "production": {
                            "devServerTarget": "idiomas:serve:production"
                        }
                    }
                }
            }
        }
    },
    "defaultProject": "idiomas",
    "cli": {
        "analytics": "5cd83f32-f52c-4ac9-bf9e-f21a7e76814c"
    }
}







    cambios package.json
    ...  "scripts":
    
    {
    "name": "idiomas",
    "version": "0.0.0",
    "scripts": {
        "ng": "ng",
        "start": "ng serve",
        "build": "ng build",


        "start:en": "ng serve --configuration=en",
        "start:es": "ng serve --configuration=es",

        "build:en": "ng build --configuration=en",
        "build:es": "ng build --configuration=es",
        "test": "ng test",
        "lint": "ng lint",
        "e2e": "ng e2e",
        "int:extract": "ng xi18n --output-path src/locale"
    },
    "private": true,
    "dependencies": {
        "@angular/animations": "~10.1.6",
        "@angular/common": "~10.1.6",
        "@angular/compiler": "~10.1.6",
        "@angular/core": "~10.1.6",
        "@angular/forms": "~10.1.6",
        "@angular/platform-browser": "~10.1.6",
        "@angular/platform-browser-dynamic": "~10.1.6",
        "@angular/router": "~10.1.6",
        "node": "^15.0.0",
        "nvm": "0.0.4",
        "rxjs": "~6.6.0",
        "tslib": "^2.0.0",
        "zone.js": "~0.10.2"
    },
    "devDependencies": {
        "@angular-devkit/build-angular": "~0.1001.7",
        "@angular/cli": "~10.1.7",
        "@angular/compiler-cli": "~10.1.6",
        "@angular/localize": "^10.1.6",
        "@types/jasmine": "~3.5.0",
        "@types/jasminewd2": "~2.0.3",
        "@types/node": "^12.11.1",
        "codelyzer": "^6.0.0",
        "jasmine-core": "~3.6.0",
        "jasmine-spec-reporter": "~5.0.0",
        "karma": "~5.0.0",
        "karma-chrome-launcher": "~3.1.0",
        "karma-coverage-istanbul-reporter": "~3.0.2",
        "karma-jasmine": "~4.0.0",
        "karma-jasmine-html-reporter": "^1.5.0",
        "protractor": "~7.0.0",
        "ts-node": "~8.3.0",
        "tslint": "~6.1.0",
        "typescript": "~4.0.2"
    }

}


Comandos

    ng serve -c=es -o --port=4205
    ng serve -c=en -o --port=4204
