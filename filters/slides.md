!SLIDE
# Filters #
Transform or reduce an inputted array

!SLIDE smaller
    @@@html
    <input type='text' ng:model='search'>
    <ul>
      <li ng:repeat='product in products | filter:search'>
        {{product.name}}
      </li>
    </ul>

!SLIDE
# Creating your own filters #