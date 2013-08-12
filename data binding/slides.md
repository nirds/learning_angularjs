!SLIDE
# Data binding #
The literal and logical representations of data are tightly coupled throughout a scope.

!SLIDE
    @@@ html
    <div ng-app>
      <input type='text' ng-model='name'>
      {{name}}
      <input type='text' ng-model='name'>
      {{name}}
    </div>

!SLIDE exercise
# Exercise #
* cd databind
* Change to the databind directory
* Using the slide as a guide, make the form say something super nice to the user.
