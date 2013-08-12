!SLIDE
# External services #

!SLIDE
## Consuming JSON ##
Fetching JSON within your domain

!SLIDE code
cd service_json

!SLIDE smaller
    @@@ javascript
    function MyController($scope, $http){
      $http.get('json/people.json').
      success(function(data, status, headers, config){
       $scope.people = data;
      }).
      error(function(data, status, headers, config){
        console.error('Could not load people')
      });
    };

!SLIDE smaller
    @@@ html
    <body ng-app ng-controller='MyController'>
      <div ng-repeat='person in people'>
        {{person.firstName}}
      </div>
    </body>

!SLIDE center
![json](json.png)

!SLIDE
## Consuming JSONP ##
Fetching JSON outside your domain

!SLIDE code
cd service_jsonp

!SLIDE smaller
    @@@html
    <script src="/javascripts/angular-resource.min.js"
            type="text/javascript"></script>

!SLIDE smaller
    @@@ html
    <body ng-app="MyApp">
      <div ng-controller='MyController'>
        <input type='text' ng-model='searchTerm'>

        <button ng-click='search()'>
          Search Google Finance
        </button>


        <div ng-repeat='result in searchResults'>
          <div>{{searchTerm}}</div>
          {{result.c}}
        </div>
      </div>
    </body>

!SLIDE smaller
    @@@javascript
    var app = angular.module("MyApp", ["ngResource"]);

    app.controller("MyController", function($scope, $resource){
      $scope.searchTerm    = 'GOOG'

      $scope.googleFinance = $resource(
        'https://finance.google.com/finance/info',
        {client:'ig', callback:'JSON_CALLBACK'},
        {get: {method:'JSONP', isArray: true}}
      );

      $scope.search = function() {
        $scope.searchResults = $scope.googleFinance.get(
          { q: $scope.searchTerm }
        );
      };
    });

!SLIDE center
![jsonp](jsonp.png)

!SLIDE
## Consuming RESTful services ##

!SLIDE
cd service_rest

!SLIDE smaller
    @@@javascript
    var app = angular.module("MyApp", ["ngResource"]);

    app.factory("Person", function($resource){
      return $resource(
        '/api/people/:id',
        {id: "@id"},
        {
          create:  { method: 'POST' },
          index:   { method: 'GET', isArray: true },
          show:    { method: 'GET', isArray: false },
          update:  { method: 'PUT' },
          destroy: { method: 'DELETE' }
        });
    });

    app.controller("MyController", function($scope, Person){
      $scope.people = Person.index();
    });

!SLIDE smaller
    @@@html
    <body ng-app ng-controller='MyController'>
      <div ng-repeat='person in people'>
        {{person.firstName}}
      </div>
    </body>

!SLIDE center
![json](json.png)

!SLIDE
# But wait, there's MORE! #

!SLIDE smaller
    @@@javascript
    // Passing parameters
    Person.index({searchTerm: 'Oscar'})

    // Fetching a single record
    person = Person.show({id: 123})

    // Update a record
    person.firstName ='Ermantrude'
    person.update()

    // Delete a record
    person.delete()

!SLIDE smaller
# Default verbs on $resources #
    @@@javascript
    {
      'get':    {method:'GET'},
      'save':   {method:'POST'},
      'query':  {method:'GET', isArray:true},
      'remove': {method:'DELETE'},
      'delete': {method:'DELETE'}
    };

!SLIDE smaller
# One more example #
    @@@javascript
    var User = $resource('/user/:userId', {userId:'@id'});
    var user = User.get({userId:123}, function() {
      user.abc = true;
      user.$save();
    });