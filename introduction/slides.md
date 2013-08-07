!SLIDE center
![angularjs](angularjs.png)

!SLIDE smbullets
# What is AngularJS? #
* Client site MVC
* Declarative extension of HTML
* Highly structured
* Extensible

!SLIDE smbullets
# Typical use cases: #

!SLIDE smbullets
# Benefits: #

!SLIDE smaller
# Getting Started #

    @@@ html
    <html>
      <head>
        <script src="https://ajax.googleapis.com/ajax/libs/
                     angularjs/1.0.7/angular.min.js">
        </script>
      </head>

      <body ng-app>
        {{8*2}}
      </body>
    </html>

!SLIDE smaller
# Data model binding #

    @@@ html
    <input type='text' ng:model='credit_card_number'></input>

    <label>
      Your card number is: {{credit_card_number}}
    </label>

!SLIDE smaller
# Click events #
    @@@ html
    <button ng:click='randomCase()'>
      {{crazyText}}
    </button>

    <script>
      function FirstController($scope){
        $scope.crazyText = 'Click me to randomize my casing'

        $scope.randomCase = function(){
          var array = $scope.carzyText.split('');
          for(var i=0; i < string.length; i ++){
            array[i] = Math.round(Math.random()) == 1 ?
              array[i].toUpperCase(): array[i].toLowerCase()
          };
          return array.join(' ')
        };
      }
    </script>

!SLIDE small
# Converting input #
    @@@ html
    <input type="number" ng-model="amount">
    {{amount | currency}}
