SetUp:
$ rails new routes_controllers_views_params -d postgresql -T
$ cd routes_controllers_views_params
$ rails db:create
$ rails generate controller Main
$ rails server
http://localhost:3000

Challenges
Routes, Views, Controllers

As a user, I can visit a custom landing page at localhost:3000.
    def home_page  
    render html: 'This is the Home Page.'     
    end
    root 'main#home_page'

As a user, I can see the names of my team members as hyperlinks on the landing page.

<ul>
    <li>
        <%= link_to 'Jonathan', '/jonathan' %> 
    </li>
    <li>
        <%= link_to 'Vicente', '/vicente' %> 
    </li>
    <li>
        <%= link_to 'Jeorge', '/jeorge' %> 
    </li>
</ul>

As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)

<ul>
    <li>
    Chick-Fil-A
    </li>
    <li>
    In-And-Out
    </li>
    <li>
    Taco Bell
    </li>
</ul>

<ul>
    <li>
    Peets Coffee
    </li>
    <li>
    Coffee & Donuts
    </li>
    <li>
    Barista 
    </li>
</ul>

<ul>
    <li>
    Karls Strauss Brewery
    </li>
    <li>
    Modern Times
    </li>
    <li>
    Ballast Point Brewery
    </li>
</ul>

Params

As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.


As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.


As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).


As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.