Creating the application 

$ rails new full-stack -d postgresql -T
$ cd full-stack 
$ git remote add origin https://github.com/learn-academy-2022-bravo/full-stack-rails-amanda-natalia.git
$ git checkout -b main
$ git status 
$ git add . 
$ git commit -m "Initial main commit"
$ git push origin main
$ git checkout -b full-stack-al-nd


Creating the database

$ rails db:create
$ rails g model LearnStudent title:string content:string
$ rails db:migrate
$ rails c     --In rails terminal
$ LearnStudent.create(title: "Week 1", content: "Intro")
$ LearnStudent.create(title: "Week 2", content:"Javascript Fund
amentals")
$ LearnStudent.create(title: "Week 3", content: "Intro to React
")


Creating the Controller

$ rails g controller LearnStudent

Creating the Index 
controller --
``` 
    def index
       @weeks = LearnStudent.all 
    end
```
routes --
Rails.application.routes.draw do
  get 'weeks' => 'learn_student#index'
end

view -- From starting 
<h1>Learn Weeks</h1>
<ul>
  <% @weeks.each do |weeks| %>
    <li>
      <%= weeks.title %>
    </li>
  <% end %>
</ul>

To incorporating Show links 
```
<h1>Learn Weeks</h1>
<ul>
  <% @weeks.each do |week| %>
    <li>
      <%= link_to week.title, week_path(week) %>
    </li>
  <% end %>
</ul>
```


SHOW

controller --
    def show 
        @week = LearnStudent.find(params[:id])
    end 

routes --
Rails.application.routes.draw do
    get 'weeks' => 'learn_student#index'
    get 'week/:id' => 'learn_student#show', as: 'week'
end

view -- 
```
<h2>Learn Student Information</h2>

<p>
    <%= @week.title %>
</p>

<p>
    <%=  @week.content %>
    Blog post: Lorem
</p>
  
<p>
    <%= link_to  'Back Home', weeks_path %>. 
</p>
```


NEW 

controller --
```
    def new
        @week = LearnStudent.new
    end
    ```

routes -- 
```
Rails.application.routes.draw do
    root 'learn_student#index', as: 'weeks'
    get 'week/new' => 'learn_student#new', as: 'new_week'
    get 'week/:id' => 'learn_student#show', as: 'week'
end
```    

view -- 
```
<h2>Please Input New Week</h2>

<%= form_with model: @weeks do |form| %>

    <%= form.label :title %>
    <%= form.text_field :title %>
    <br />
    <br />
    <%= form.label :content %>
    <%= form.text_field :content %>
    <br />
    <br />
    <%= form.submit "Add Next Week" %>
  
  <% end %>


  <p>
    <%= link_to  'Back Home', weeks_path %> 
</p>


CREATE 

controller --
```
    def create
        @week = LearnStudent.create(week_params)
        if @week.valid?
            redirect_to weeks_path
        end
    end

    private
    def week_params
        params.require(:learn_student).permit(:title, :content)
      end
end
```

route -- 
```
Rails.application.routes.draw do
    root 'learn_student#index', as: 'weeks'
    get 'week/new' => 'learn_student#new', as: 'new_week'
    get 'week/:id' => 'learn_student#show', as: 'week'
    post 'week' => 'learn_student#create'
end
```