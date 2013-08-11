!SLIDE
# External services #

!SLIDE
## Consuming JSON ##

!SLIDE code
git checkout services_json

!SLIDE smaller
    @@@ html
    <body ng-app ng-controller='MyController'>
      <div ng-repeat='person in people'>
        {{person.firstName}}
      </div>
    </body>

!SLIDE smaller
    @@@javascript
    function MyController($scope, $http){
      $http.get('json/people.json').
      success(function(data, status, headers, config){
       $scope.people = data;
      }).
      error(function(data, status, headers, config){
        console.error('Could not load people')
      });
    };

!SLIDE center
![json](json.png)