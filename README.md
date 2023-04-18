# Market Money FE
---

# Consuming your Market Money API

Congratulations! You've written your first API. Just like the API you consumed for your week 1 project, your Market Money API can be used by other projects now, too. For this challenge, you will create a front end application that will make calls to your backend application, the Market Money API you have just created.

## Learning Goals:
* Consuming an API
* Gain familiarity with service oriented architecture

## Setup

Just like your week 1 project, this will be a new Rails app. You should create your own FE with `rails new market_money_fe -T --database=postgresql --skip-spring --skip-turbolinks`

In `/config/puma.rb`, you'll need to change the port from 3000 to 5000. This should be on or around line 12.

We do this because Market Money is not in production or hosted somewhere other than localhost. If Market Money is running on port 3000, our front end will need to have a different port so they can run at the same time. Now, when we do `rails s`, our front end application will automatically use port 5000. You can also do this manually every time you start your server by passing the port number with a `-p` flag like so:
`rails s -p 5000`. You should see that your server is "listening on tcp://localhost:5000" now instead of the usual 3000.

```ruby
port        ENV.fetch("PORT") { 5000 }
```

**In order for your frontend to properly get data from your backend Market Money API, you must keep your backend server running locally at the same time.**

## The Challenge

### User Story 1 - Markets Index Page
As a visitor, <br>
When I visit '/markets' <br>
I see all markets listed with their name, city and state<br>
When I click a button to see more info on that market <br>
I'm taken to that market's show page '/markets/:id' <br>

![Wireframe for /markets index](/images/markets_index.png)

### User Story 2 - Markets Show Page
As a visitor, <br>
When I visit a market's show page 'markets/:id' <br>
I see that market's name and readable address <br>
And I also see a list of all the Vendors that are at that market <br>
Each vendor name is a link to that vendor's show page <br>

![Wireframe for /markets show](/images/markets_show.png)

### User Story 3 - Vendor Show Page
As a visitor <br>
When I visit a vendor's show page 'vendors/:id' <br>
I see that vendor's name, contact information, whether they accept credit, and a description of what they sell <br>

![Wireframe for /vendors show](/images/vendors_show.png)

## Extra Practice
If you have time or want extra practice, complete the following user stories

### User Story 4 - Vendor Show Page can Search for Markets to Add
As a visitor <br>
When I visit a vendor's show page 'vendors/:id' <br>
I see a section on the page to search for Markets to add this Vendor<br>
When I fill out the form with a valid combination of parameters (see project requirements to know what parameter combinations are considered valid) <br>
And click the button to search for markets <br>
I see a list of Market's that match my search terms <br>
And each market listed is a link to it's show page <br>
* Note: If an invalid set of parameters are passed in, a flash message should describe the problem that occurred. 

### User Story 5 - Vendor Show Page can Add a Vendor to a Market
As a visitor <br>
When I visit a vendor's show page 'vendors/:id' <br>
And fill out the market search with valid parameters and hit "Search" <br>
And click on a search results button to Add Market <br>
I see a flash message saying that the vendor was added to a new market <br>
I'm taken back to the vendor show page <br>
* Note: This vendor should appear on the newly added market's show page. <br>

![Wireframe for markets search](/images/market_search.png)
![Wireframe for markets search results](/images/market_search_results.png)
![Wireframe for markets search sad path](/images/market_search_sad_path.png)

