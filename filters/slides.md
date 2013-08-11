!SLIDE
# Filters #
Transform or reduce input

!SLIDE code
git clone git@github.com:nirds/angular\_seed\_app.git
git checkout filters_basics

!SLIDE smaller
# Transforming input #
    @@@ html
    <input type="number" ng-model="amount">
    {{amount | currency}}

!SLIDE center
![currency filter](currency_filter.png)

!SLIDE smaller
# Implementing a custom filter
    @@@ html
    <input type="text" ng-model="text">
    {{text | reverse}}

!SLIDE smaller
    @@@ javascript
    var app = angular.module("MyApp", []);

    app.filter('reverse', function() {
      return function(text){
        text = text || "";
        return text.split('').reverse().join('');
      };
    });

!SLIDE center
![custom filter](custom_filter.png)

!SLIDE smaller
# Reducing elements of array #
    @@@html
    <input type='text' ng:model='search'>
    <ul>
      <li ng:repeat='entry in entries | filter:search'>
        {{product.name}}
      </li>
    </ul>

!SLIDE center
![array filter](array_filter.png)