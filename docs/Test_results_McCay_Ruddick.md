
# Testing example flows from v2_manual_test_results.md

## Test supply matching ##

Request

    curl -X 'GET' \   'https://meal-planner-9c99.onrender.com/recipes?ingredients=flour&ingredients=egg' \   -H 'accept: application/json'

Response:
```
    [
      {
        "id": 1,
        "name": "Scrambled Eggs",
        "ingredients": [
          {
            "name": "Egg",
            "amount_units": "3 eggs",
            "price": 3,
            "item_type": "1"
          },
          {
            "name": "Pepper",
            "amount_units": "to taste",
            "price": 1,
            "item_type": "1"
          },
          {
            "name": "Salt",
            "amount_units": "to taste",
            "price": 1,
            "item_type": "1"
          },
          {
            "name": "Oil",
            "amount_units": "2 tbsp",
            "price": 2,
            "item_type": "1"
          }
        ],
		...
    ]
```

## Test Recipe creation

Request:

    curl -X 'POST' \
      'https://meal-planner-9c99.onrender.com/recipes' \
      -H 'accept: application/json' \
      -H 'Content-Type: application/json' \
      -d '{
     "name": "Omelette",
     "instructions": "Beat eggs and cook.",
     "time": 5,
     "difficulty": "beginner",
     "ingredients": [
     { "name": "Egg", "amount_units": "3", "price": 0.5, "item_type": "wet" },
     { "name": "Milk", "amount_units": "1/4 cup", "price": 0.3, "item_type": "wet" }
     ],
     "supplies": [
     { "supply_name": "pan" }
     ]
     }'
Response:

    {
      "recipe_created": "Recipe created successfully",
      "recipe_id": 23
    }

## Test recipe update

Request:

    curl -X 'PUT' \
      'https://meal-planner-9c99.onrender.com/recipes/1' \
      -H 'accept: application/json' \
      -H 'Content-Type: application/json' \
      -d '{
     "name": "Updated Pancakes",
     "instructions": "Mix ingredients and cook.",
     "time": 20,
     "difficulty": "beginner",
     "ingredients": [
     { "name": "Flour", "amount_units": "2 cups", "price": 1.5, "item_type": "dry" },
     { "name": "Egg", "amount_units": "2", "price": 0.5, "item_type": "wet" }
     ],
     "supplies": [
     { "supply_name": "Spatula" }
     ]
     }'

Response:

    {
      "recipe_updated": "Recipe updated successfully"
    }

## Test recipe suggestions

Request:

    curl -X 'GET' \ 'https://meal-planner-9c99.onrender.com/recipes/suggestions?ingredients=flour&ingredients=sugar' 
    \ -H 'accept: application/json'

Response:

    [   {
        "id": 12,
        "name": "Banana Bread",
        "missing_ingredients": [
          {
            "name": "Banana",
            "amount_units": "5 large",
            "price": 2,
            "item_type": "1"
          },
          ...
          }
        ]   },   {
        "id": 17,
        "name": "Pancakes",
        "missing_ingredients": [
          {
            "name": "Egg",
            "amount_units": "2",
            "price": 3,
            "item_type": "1"
          }
        ]   }, ...

## Test delete recipe 1

Request:

    curl -X 'DELETE' \
      'https://meal-planner-9c99.onrender.com/recipes/1' \
      -H 'accept: application/json'

Response:

    Internal Server Error 500

## Test delete recipe 2

Request: 

    curl -X 'DELETE' \ 'https://meal-planner-9c99.onrender.com/recipes/2'
     \ -H 'accept: application/json.'

Response:

    404 error: 
    	{ "detail": "Recipe was not found in db" }

## Test delete recipe 3

Request:

    curl -X 'DELETE' \ 'https://meal-planner-9c99.onrender.com/recipes/23'
     \ -H 'accept: application/json'

Response:
	
    { "deleted_complete": "Recipe deleted" }

## Cart Tests

Request:

    curl -X 'POST' \ 
    'https://meal-planner-9c99.onrender.com/carts/create/{cart_id}'
     \ -H 'accept: application/json' \ -d ''

Response:

    Internal Server Error 500

Request: 

    curl -X 'POST' \
      'https://meal-planner-9c99.onrender.com/carts/create/1?customer_id=1&payment_id=1' \
      -H 'accept: application/json' \
      -d ''

Response:

    Internal Server Error 500
Request:

    curl -X 'POST' \ 
    'https://meal-planner-9c99.onrender.com/carts/{cart_id}/items/{item_id}?ingredient_name=test&quantity=2' 
    \ -H 'accept: application/json' \ -d ''

Response:

    Internal Server Error 500

    
Request:

    curl -X 'POST' \ 
    'https://meal-planner-9c99.onrender.com/carts/{cart_id}/checkout?customer_name=test&card_num=123123&exp_date=3212&customer_id=3'
     \ -H 'accept: application/json' \ -d ''

Response:

    Internal Server Error 500

None of the cart endpoints appear to be functioning, and some endpoints listed in v2_manual_test_results.md and ExampleFlows.md do not seem to exist. All of them return 500 errors when called.

# Testing example flows from v1_manual_test_results.md

Request:

    curl -X 'GET' \
    'https://meal-planner-9c99.onrender.com/reviews/1' \
    -H 'accept: application/json'

Response:

    [ { "recipe_name": "Updated Pancakes", "rating": 1, "review": "good", "customer": "Robert California" }, { "recipe_name": "Updated Pancakes", "rating": 5, "review": "This recipe rocks", "customer": "Robert California" }, { "recipe_name": "Updated Pancakes", "rating": 0, "review": "\"Cake blows\"", "customer": "Robert California" }, { "recipe_name": "Updated Pancakes", "rating": 0, "review": "\"Cake blows\"", "customer": "testTy123" }, { "recipe_name": "Updated Pancakes", "rating": 0, "review": "\"Cake blows\"", "customer": "Test Customer!" } ]

Request:

    curl -X 'POST' \ 'https://meal-planner-9c99.onrender.com/reviews/create/1?customer_id=1&rating=0&review=This%20Stinks' \ -H 'accept: application/json' \ -d ''


Response:

    { "review_id": 32 }

Request:

    curl -X 'POST' \
  'https://meal-planner-9c99.onrender.com/reviews/delete/4/32?deleted_by=Spaghetti%20Tom' \
  -H 'accept: application/json' \
  -d ''

  Response:

      "Ok"


# New Workflow 1: Tom Spaghetti creates an account and wants to see what he can do with his egg and he is curious to share his eggsellent recipe


1. Tom starts by calling `POST /customers/register` to register and account

Request:

	curl -X 'POST' \
	  'https://meal-planner-9c99.onrender.com/customers/register?customer_name=Tom%20Spagetiit' \
	  -H 'accept: application/json' \
	  -d ''

Response:

	{
	  "customer_id": 18
	}

   
2. Then Tom calls `GET /recipes/suggestions` to get a list of recipes he can use eggs in

Request:

	curl -X 'GET' \
	  'https://meal-planner-9c99.onrender.com/recipes/suggestions?ingredients=egg' \
	  -H 'accept: application/json'

Response:

	[
	  {
	    "id": 12,
	    "name": "Banana Bread",
	    "missing_ingredients": [
	      {
	        "name": "Flour",
	        "amount_units": "2 cups",
	        "price": 1,
	        "item_type": "1"
	      },
	      ...
	    ]
	  },
	  {
	    "id": 17,
	    "name": "Pancakes",
	    "missing_ingredients": [
	      {
	        "name": "Flour",
	        "amount_units": "2 cups",
	        "price": 1,
	        "item_type": "1"
	      }
	    ]
	  },
	  {
	    "id": 1,
	    "name": "Updated Pancakes",
	    "missing_ingredients": [
	      {
	        "name": "Flour",
	        "amount_units": "2 cups",
	        "price": 1,
	        "item_type": "1"
	      }
	    ]
	  }
	]

3. Tom loves the options, but he wants to add one of his own so he calls POST /recipes/

Request:

	curl -X 'POST' \
	  'https://meal-planner-9c99.onrender.com/recipes/' \
	  -H 'accept: application/json' \
	  -H 'Content-Type: application/json' \
	  -d '{
	  "id": 369,
	  "name": "Toms Eggs",
	  "ingredients": [
	    {
	      "name": "egg",
	      "amount_units": "1 big ol egg",
	      "price": 1000000000,
	      "item_type": "Dragon"
	    }
	  ],
	  "instructions": "Put egg in pan, forget about it",
	  "time": 9001,
	  "difficulty": "advanced",
	  "supplies": [
	    {
	      "supply_name": "pan"
	    }
	  ]
	}'

Response:

	{
	  "recipe_created": "Recipe created successfully",
	  "recipe_id": 25
	}

---

# New Workflow 2: Tom Spaghetti's harshest critic Marty Marinara wants to see what Tom has been up to, review his recipe, and change it if it's not up to his standards

1. Marty starts by calling `GET recipies/{id}` and he knows Toms ID is 25

Request:

	curl -X 'GET' \
	  'https://meal-planner-9c99.onrender.com/recipes/25' \
	  -H 'accept: application/json'
Response:

	{
	  "id": 25,
	  "name": "Toms Eggs",
	  "ingredients": [
	    {
	      "name": "Egg",
	      "amount_units": "1 big ol egg",
	      "price": 3,
	      "item_type": "1"
	    }
	  ],
	  "instructions": "Put egg in pan, forget about it",
	  "time": 9001,
	  "difficulty": "advanced",
	  "supplies": [
	    {
	      "supply_name": "pan"
	    }
	  ]
	}
 
 Marty notices here the code seems to have changed Tom's price from 1 billion to 3 and his item_type from "Dragon" to "1"

2. Then Marty calls `POST /reviews/create/{recipe_id}` to post his review about Toms Eggs.

Request:

	curl -X 'POST' \
	  'https://meal-planner-9c99.onrender.com/reviews/create/25?customer_id=3&rating=2&review=Where%20on%20earth%20am%20I%20to%20find%20a%20big%20ol%20egg' \
	  -H 'accept: application/json' \
	  -d ''

Response:

	{
	  "review_id": 33
	}
 
Marty notices that he has just impersonated someone as he has never been given a customer_id, he just gave one randomly


3. Feeling malicious Marty decides to update Toms recipie without his knowdlege by calling `PUT recipies/{id}`

Request: 
	   curl -X 'PUT' \
	  'https://meal-planner-9c99.onrender.com/recipes/25' \
	  -H 'accept: application/json' \
	  -H 'Content-Type: application/json' \
	  -d '{
	  "id": 25,
	  "name": "Marty",
	  "ingredients": [
	    {
	      "name": "Marty",
	      "amount_units": "Marty",
	      "price": -100000,
	      "item_type": "Marty"
	    }
	  ],
	  "instructions": "Marty",
	  "time": -100000,
	  "difficulty": "Marty",
	  "supplies": [
	    {
	      "supply_name": "Marty"
	    }
	  ]
	}'
Response:
	
	{
	  "recipe_updated": "Recipe updated successfully"
	}

 4. Marty now would like to check his work by calling `GET recipies/{id}` again

Request:
	curl -X 'GET' \
	  'https://meal-planner-9c99.onrender.com/recipes/25' \
	  -H 'accept: application/json'
Response:
	{
	  "id": 25,
	  "name": "Marty",
	  "ingredients": [
	    {
	      "name": "marty",
	      "amount_units": "Marty",
	      "price": -100000,
	      "item_type": "Marty"
	    }
	  ],
	  "instructions": "Marty",
	  "time": -100000,
	  "difficulty": "Marty",
	  "supplies": [
	    {
	      "supply_name": "marty"
	    }
	  ]
	}

Marty has now soiled Toms's plans to have fun and share his recipe, He has also put in negative values into price and time.

---

# New Workflow 3: Tom Spaghetti is back to check on his ratings and see how his recipe is doing.

1. Tom starts by checking on his good ol recipe_id number 25 `GET reviews/{recipe_id}` to see if anyone left any constructive feedback for him

Request:

	curl -X 'GET' \
	  'https://meal-planner-9c99.onrender.com/reviews/25' \
	  -H 'accept: application/json'
Response:
	[
	  {
	    "recipe_name": "Marty",
	    "rating": 2,
	    "review": "Where on earth am I to find a big ol egg",
	    "customer": "Test Customer!"
	  }
	]

 Tom is very confused, he wrote down his recipie_id so he is certian something must be wrong, who is this "Test Customer!" and why is his recipe named "Marty"

2. Confused, Tom checks on his recipe by calling `GET recipies/{id}`

Request:

	curl -X 'GET' \
	  'https://meal-planner-9c99.onrender.com/recipes/25' \
	  -H 'accept: application/json'
Response:

	{
	  "id": 25,
	  "name": "Marty",
	  "ingredients": [
	    {
	      "name": "marty",
	      "amount_units": "Marty",
	      "price": -100000,
	      "item_type": "Marty"
	    }
	  ],
	  "instructions": "Marty",
	  "time": -100000,
	  "difficulty": "Marty",
	  "supplies": [
	    {
	      "supply_name": "marty"
	    }
	  ]
	}
 Tom is very confused and hisheartened

3. Worried that this horrid recipe might be tied back to Tom he attempts to delete it using `DELETE recipies/{id}`

Request:
	curl -X 'DELETE' \
	  'https://meal-planner-9c99.onrender.com/recipes/25' \
	  -H 'accept: application/json'
Response:
	Internal Server Error (500)

There seems to be an issue with the delete function; Tom is now trapped as the owner of the recipe, while Marty has won and remained anonymous.
