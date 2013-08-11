!SLIDE
# Controllers #
Business logic and behavior is defined in controllers

!SLIDE smbullets
# Benefits #
* Behavior is divorced from the DOM
* No setting up callbacks
* No watching the DOM for changes

!SLIDE code
git clone git@github.com:nirds/angular\_seed\_app.git
git checkout controllers_basics

!SLIDE
# Initialize variables #

!SLIDE smaller
    @@@ html
    <input type='text' ng-model="important_information">
    <label>
      {{important_information}}
    </label>

!SLIDE smaller
    @@@ javascript
    function MyController($scope){
      $scope.important_information = 'Set in MyController';
    }

!SLIDE center
![setting variables](setting_variables.png)

!SLIDE
# Respond to click event #

!SLIDE smaller
    @@@ html
    <button ng-click='randomizeCase()'>
      Randomize case!
    </button>

!SLIDE smaller
    @@@ javascript
    function MyController($scope){
      $scope.important_information = 'Set in MyController';

      $scope.randomizeCase = function(){
        var array = $scope.important_information.split('');

        for(var i=0; i < array.length; i ++){
          if(Math.round(Math.random()) == 1)
            array[i].toUpperCase();
          else
            array[i].toLowerCase();
        };

        $scope.important_information = array.join('');
      }
    }

!SLIDE center
![click event](random_case.png)

!SLIDE
# Submitting forms #

!SLIDE code
git checkout controllers_forms

!SLIDE
# Urls, routing and templates #

!SLIDE code
git checkout controllers_routing

