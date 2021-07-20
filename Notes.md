#APIs - What are they ?

# Example 1
- If we go to `www.yahoo.com` and take a look at the weather section, we can see that it displays the current geolocation we have and the weather forecast for it.
- The data is retrieved via a weather data service (like `https://openweathermap.org/api`). Their job (the service) is to collect the data, organize it and do all the 
complex operations on it.
- Afterwards, we can just use their API to tap into the live weather data.

# Example 2
- Similarly, when we go to Tinder (by logging in through Facebook), the sections `Shared Friends` and `Shared Interests` are retrieved from facebook. Tinder asks facebook for these pieces of data.
- Tinder is able to so by using the Facebook API.

# Further notes
- With APIs, we can build interesting web apps.
- APIs range from Stocks' information APIs to Pokémon APIs.

# Definition
- API: set of commands, functions, protocols and objects that programmers can use to
<em><u>create software</u></em> or <em><u>interact with an external system</u></em>.

- Simplified: certain pieces of data that are open/allowed to be accessed and other
  which are not.
  
- Some people consider it a contract between the data provider and the developer. Essentially, it says
"these are the pieces of data you can access, this is how etc., we as the website that provides the data will try not to change anything without informing you.".

- API: Application Programming Interface.

# Example of APIs that allow creation of software
- jQuery

# Example of APIs that interact with an external system
- Tinder through the Facebook API

- Model (Simplified):

``````````````````````````````````````````````````````````````````````````````````````````````````````
                            #            
##############       --- REQUEST --->        ###########################
#            #              #                #                         #
# OUR SERVER #             API               #     EXTERNAL SERVER     #  
#            #              #                # (Someone else's server) #
##############      <-- RESPONSE ---         ###########################                      
                            #
``````````````````````````````````````````````````````````````````````````````````````````````````````

# Practicalities of APIs - I
1) Endpoints 
- provide access to the API, ex.: `https://api.kanye.rest/`, by accessing the previously mentioned URL in a browser,
  we will make a request to the kanye.rest API that has an underlying database. Once the request to the API is fired up,
  we will see a random quote from our MVP Kanye W.
- different endpoints exist, but they will always be specified in the adherent API docs.

2) Paths
3) Parameters
- 2) and 3) go hand-in-hand, being used in the following format `Path/Params`.
-  Ex.: Endpoint: `https://sv443.net/jokeapi/v2/` a bit more complex API than the previous one.
-  Ex.: Endpoint with Parameters: `https://sv443.net/jokeapi/v2/{Parameter}` where Parameter can be a value from 
   ["Programming", "Misc", "Dark", "Pun", "Spooky", "Christmas"].

- If we specify `https://sv443.net/jokeapi/v2/Dark`, we will get jokes only from the Dark category.
- On the Joke API Server, they get the request for Dark jokes, then they query/filter their stored (DB) jokes for the
matches and then return the response. As this is also a main category, they have a route for it (Plan Ahead of Time, expected requests).
- Parameters come at the end of the URL after a `?` ex.: `https://sv443.net/jokeapi/v2/Programming?contains=debugging`. They allow custom
queries (contains=debugging is a key - value pair).
- Advanced queries (parameter chaining) ex.: `https://v2.jokeapi.dev/joke/Programming?blacklistFlags=nsfw&type=single&contains=debugging`.
Multiple parameters (subsequent queries, the order of the parameters does not matter) can be chained together by using the `&` symbol.
  
4) Authentication
- We have worked with the jokes API and the Kanye Rest API, however when it comes to more serious APIs that provide
monetizable data and data that will be provided to hundreds, thousands or maybe even billions of users, the API host/data provider 
has to think about a couple of aspects. These aspects are the threshold (limit) of requests that can be made to the API or how to demand
a certain of amount of contribution for each request.
-  The above mentioned details are related to authentication. Authentication means that the website/data provider that hosts the web service (API),
can identify who we are. Then they can track how often we request data from their server(s) and charge us or limit us accordingly.

# Practicalities of APIs - II
- By using the OpenWeather API as an example study case, we can see that in their `pricing` section, the number of free requests is limited to 60.
For starting out a project, this is just fine, however, say if the number of users increases dramatically for our application, then we would have to
use a pricing plan else, they will restrict our access to their API.
  
- To implement `Authentication` we need create an account on the platform of the data provider (web service) and then use the provided API key(s) to 
be able to access the API.
- For testing APIs we will use `Postman`. With `Postman`, the data (response) which is in Json format gets prettier in contrast to how it is being sent 
from the server (ugly/unformatted).

# Practicalities of APIs - III
- JSON format: JavaScript Object Notation. Json formatted data looks quite similar to JS objects, using key - value pairs for properties and allowing
us to embed objects within other objects or arrays of objects.
-  There are however some differences, `A JS object looks like this: var/const/let myObj = { numberProperty:1, stringProperty: 'a', arrayProperty: [] }`
-  The reasons for which we use JSON are that is human-friendly in terms of readability, it can easily be collapsed down to take as little as possible space during 
   data transfer over the network Ex.: `"{doors:2, color:"red", drawers:2}"`.
-  Once the data is received, we can rebuild it into JS objects fo example.
-  Aside from JSON, other data formats are available for data transmission from APIs, those are XML, HTML, CSV, YAML and PROTOCOL-BUFFERS. Even so, JSON is by far the
most-used, preferred one as it is the most light-weight (and allows easy mapping to JS objects).

# Practicalities of APIs - IV
- Using an API into an actual App.
Simplified model (High-level overview):
````````````````````````````````````````````````````````````````````````````````````````````
                                                                    #
CLIENT BROWSER    ---REQUEST-->   OUR SERVER        ---REQUEST-->  API       EXTERNAL SERVER
   (User)         <--RESPONSE--                     <--RESPONSE--   #
                                                                    #
````````````````````````````````````````````````````````````````````````````````````````````
- The definition of `REQUEST`, GET REQUEST for all the HTML, CSS and JS required to display the web app. content.
- The definition of `RESPONSE`, return all the HTML, CSS and JS required to display the web app. content. But, the `RESPONSE` also
includes some data from some other server (external API/web service), hence we will need to use the corresponding/specified path(s) and 
parameter(s) to access that data. 