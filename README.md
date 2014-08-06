# angular-spin

Angular directive to show an animated spinner (using [spin.js](http://fgnass.github.io/spin.js/))

Originally created by Uri Shaked <uri@urish.org>.

## Usage

Include both spin.js and angular-spinner.js in your application.

```html
<script src="bower_components/spin.js/dist/spin.js"></script>
<script src="bower_components/angular-spinner/angular-spinner.js"></script>
```

Add the module `angularSpin` as a dependency to your app module:

```js
var myapp = angular.module('myapp', ['angularSpin']);
```

You can now start using the spinner directive to display an animated
spinner. For example :

```html
<span spinner></span>
```

You can also pass spinner options, for example:

```html
<span spinner="{radius:30, width:8, length: 16}"></span>
```

Possible configuration options are described in the [spin.js homepage](http://fgnass.github.io/spin.js/).

### Using the spinnerService to control spinners

```html
<button ng-click="spin-me">Start spinner</button>
<button ng-click="spin-me">Stop spinner</button>

<span spinner spinner-group="spinner-1"></span>
```

The `spinnerService` service let you control spin start and stop :

```js
app.controller('MyController', ['$scope', 'spinnerService', function($scope, spinnerService){
    $scope.startSpin = function(){
        usSpinnerService.spin('spinner-1');
    }
    $scope.stopSpin = function(){
        usSpinnerService.stop('spinner-1');
    }
}]);
```

Note that when you specify a key, the spinner is rendered inactive.
You can still render the spinner as active with the spinner-start-active parameter :
```html
<span spinner spinner-key="spinner-1" spinner-start-active="1"></span>
```

The spinner-key will be used as an identifier (not unique) allowing you to have several spinners controlled by the same key :

```html
<span spinner spinner-key="spinner-1"></span>
<span spinner spinner-key="spinner-2"></span>

... random html code ...

<!-- This spinner will be triggered along with the first "spinner-1" -->
<span spinner spinner-key="spinner-1"></span>
```

## License

Released under the terms of MIT License.

