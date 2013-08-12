!SLIDE
# Directives #
Extend the behavior of HTML by either creating new elements or by augmenting existing elements.

!SLIDE
## Creating a new element ##

!SLIDE
cd directives_e

!SLIDE smaller
    @@@html
    <body ng-app="MyApp">
      <crazy-panel>
        This is some crazy text!
      </crazy-panel>
    </body>

!SLIDE center
![crazy_directive](crazy_directive.png)

!SLIDE smaller
    @@@javascript
    var app = angular.module("MyApp", []);

    app.directive('crazyPanel', function(){
      return {
        restrict: "E",
        link: function(scope, element, attributes){
          var target = element[0],
          innerHTML = target.innerHTML,
          arr = [],
          colors = ['red', 'green', 'blue', 'black', 'orange'];

          angular.forEach(innerHTML.split(''), function(c, key){
            arr.push("<span style='color: " +
              colors[key%colors.length] +
              "'>" + c + "</span>");
          });

          target.innerHTML = arr.join('');
        }
      };
    });

!SLIDE smaller
    @@@javascript
    var app = angular.module("MyApp", []);

    app.directive('crazyPanel', function(){
      return {
        restrict: "E",
        link: function(scope, element, attributes){
          // ...
        }
      };
    });

!SLIDE
## Extending the behavior of elements ##

!SLIDE
cd directives_e

!SLIDE smaller
    @@@html
    <body ng-app="MyApp">
      <ul wrap='li' uppercase>
        the highest case of them all
      </ul>
    </body>

!SLIDE smaller
    @@@javascript
    var app = angular.module("MyApp", []);

    app.directive('uppercase', function(){
      return {
        restrict: "A",
        link: function(scope, element, attributes){
          var target = element[0];
          target.innerHTML = target.innerHTML.toUpperCase();
        }
      };
    });

!SLIDE smaller
    @@@javascript
    app.directive('wrap', function(){
      return {
        restrict: "A",
        link: function(scope, element, attributes){
          var wrap    = attributes['wrap'],
              opening = '<' + wrap + '>',
              closing = '</' + wrap + '>',
              target  = element[0];

          target.innerHTML = [
            opening, target.innerHTML, closing
          ].join('');
        }
      };
    });

!SLIDE center
![a directives](a_directives.png)

!SLIDE smaller smbullets
# Exercise #
* cd directives\_e\_exercise
* Create your own directive
* The directive must be restricted to elements
* The directive must randomly display three different images of your choosing