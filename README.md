# RoutesFAQ

#creating a route link to model#

#first create a new model 
    
    rails g model portfolio item_name:string item_description:text
    rake db:migrate

#next we want to create a controller with the show and index action
  
    rails g controller portfolio index show
    
#next thing we want to do is create the resources for all the portfolio routes

    resources :portfolio   if your root page is home index then use resources:home
   
#next we add instance @ so we can globally make use of the data

    def index
    @portfolios = Portfolio.all
    end

    def show
    @portfolios = Portfolio.find(params[:id])
    end
    
#now we can paste the ruby wrappers to use it in our index
to find where our show route is use rakeroutes
index section

    <% @portfolios.each do |portfolios| %>
    <%= link_to "Visit url", portfolio_path(portfolios.id) %>
    <% end %>
    
#inside our show view we can now make use of the ID data 
show section

    <%= @portfolios.title %>
