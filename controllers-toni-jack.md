Challenges
Routes, Views, Controllers

As a user, I can visit a custom landing page at localhost:3000.
- Done
As a user, I can see the names of my team members as hyperlinks on the landing page.
- Done
teamnames.html.erb
<ul>
    <li><%= link_to 'Toni', '/toni' %></li>
    <li><%= link_to 'Jack', '/jack' %></li>
</ul>
As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)
- Done
routes.rb
Rails.application.routes.draw do
  root 'team#teamnames'
  get '/toni' => 'team#toni'
  get '/jack' => 'team#jack'
  get '/teamnames' => 'team#teamnames'
end

toni.html.erb
<h1>Toni</h1>
<h2>Top Three Things</h2>
<ul>
    <li>Steak</li>
    <li>Home Cooking</li>
    <li>Desserts</li>

jack.html.erb
<h1>Jack</h1>
<h2>Top Three Things</h2>
<ul>
    <li>Pizza</li>
    <li>Coffee</li>
    <li>Tomato Soup</li>

Params

As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.
As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.
As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).
As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.