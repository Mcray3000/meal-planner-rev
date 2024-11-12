
# Testing example flows from v2_manual_test_results.md

Request

    curl -X 'GET' \   'https://meal-planner-9c99.onrender.com/recipes?ingredients=flour&ingredients=egg' \   -H 'accept: application/json'

Response:

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
        "instructions": "Add oil to pan and place on stove on medium heat. Crack eggs into a bowl and season with salt and pepper. Whisk eggs until consistent color/texture. Pour egg mixture into pan. Mix occasionally to prevent eggs from sticking to the pan. Cook until the eggs reach your desired consistency. Remove from heat and enjoy.",
        "time": 10,
        "difficulty": "beginner",
        "supplies": [
          {
            "supply_name": "pan"
          }
        ]
      },
      {
        "id": 12,
        "name": "Banana Bread",
        "ingredients": [
          {
            "name": "Sugar",
            "amount_units": "4 cups",
            "price": 3,
            "item_type": "1"
          },
          {
            "name": "Egg",
            "amount_units": "1 egg",
            "price": 3,
            "item_type": "1"
          },
          {
            "name": "Oil",
            "amount_units": "1/4 cup",
            "price": 2,
            "item_type": "1"
          },
          {
            "name": "Banana",
            "amount_units": "5 large",
            "price": 2,
            "item_type": "1"
          },
          {
            "name": "Flour",
            "amount_units": "2 cups",
            "price": 1,
            "item_type": "1"
          }
        ],
        "instructions": "combine all ingredients, back at 355 for 55 minutes",
        "time": 45,
        "difficulty": "beginner",
        "supplies": [
          {
            "supply_name": "pan"
          },
          {
            "supply_name": "mixing bowl"
          },
          {
            "supply_name": "electric mixer"
          }
        ]
      },
      {
        "id": 16,
        "name": "Milkshake",
        "ingredients": [
          {
            "name": "milk",
            "amount_units": "1 cup",
            "price": 2,
            "item_type": "dairy"
          },
          {
            "name": "ice cream",
            "amount_units": "2 cups",
            "price": 5,
            "item_type": "dairy"
          }
        ],
        "instructions": "put in blender until blended",
        "time": 5,
        "difficulty": "beginner",
        "supplies": [
          {
            "supply_name": "blender"
          }
        ]
      },
      {
        "id": 17,
        "name": "Pancakes",
        "ingredients": [
          {
            "name": "Egg",
            "amount_units": "2",
            "price": 3,
            "item_type": "1"
          },
          {
            "name": "Flour",
            "amount_units": "2 cups",
            "price": 1,
            "item_type": "1"
          }
        ],
        "instructions": "Mix and cook",
        "time": 15,
        "difficulty": "beginner",
        "supplies": [
          {
            "supply_name": "spatula"
          },
          {
            "supply_name": "pan"
          }
        ]
      },
      {
        "id": 20,
        "name": "Haddie's Cheating",
        "ingredients": [
          {
            "name": "spam",
            "amount_units": "3 tests",
            "price": -10,
            "item_type": "Spam"
          }
        ],
        "instructions": "Make multiple reviews",
        "time": 1,
        "difficulty": "beginner",
        "supplies": [
          {
            "supply_name": "computer"
          }
        ]
      },
      {
        "id": 21,
        "name": "string",
        "ingredients": [
          {
            "name": "string",
            "amount_units": "string",
            "price": 0,
            "item_type": "string"
          }
        ],
        "instructions": "string",
        "time": 0,
        "difficulty": "string",
        "supplies": [
          {
            "supply_name": "string"
          }
        ]
      },
      {
        "id": 22,
        "name": "string",
        "ingredients": [
          {
            "name": "string",
            "amount_units": "string",
            "price": 0,
            "item_type": "string"
          }
        ],
        "instructions": "Bake potatoes at 400",
        "time": 0,
        "difficulty": "string",
        "supplies": [
          {
            "supply_name": "string"
          }
        ]
      }
    ]

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

Request:

    curl -X 'GET' \ 'https://meal-planner-9c99.onrender.com/recipes/suggestions?ingredients=flour&ingredients=sugar' 
    \ -H 'accept: application/json'

Responce:

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
          {
            "name": "Oil",
            "amount_units": "1/4 cup",
            "price": 2,
            "item_type": "1"
          },
          {
            "name": "Egg",
            "amount_units": "1 egg",
            "price": 3,
            "item_type": "1"
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
        ]   },   {
        "id": 1,
        "name": "Updated Pancakes",
        "missing_ingredients": [
          {
            "name": "Egg",
            "amount_units": "2",
            "price": 3,
            "item_type": "1"
          }
        ]   } ]
        
Request:

    curl -X 'DELETE' \
      'https://meal-planner-9c99.onrender.com/recipes/1' \
      -H 'accept: application/json'

Response:

    Internal Server Error 500

Request: 

    curl -X 'DELETE' \ 'https://meal-planner-9c99.onrender.com/recipes/2'
     \ -H 'accept: application/json.'

Response:

	

    404 error: 
    	{ "detail": "Recipe was not found in db" }

Request:

    curl -X 'DELETE' \ 'https://meal-planner-9c99.onrender.com/recipes/23'
     \ -H 'accept: application/json'

Response:
	

    { "deleted_complete": "Recipe deleted" }

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


# New Workflow 1: Tom Spaghetti creates an account and wants to see what he can do with all his eggs


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

   
3. Then Joe calls `GET /stores` to get a list of the stores available in the app, along with the store IDs.
4. Finally, Joe calls `GET /stores/{store_id}/catalogue`, using the ID of Trader Joe's.

Joe now has a list of the catalogue items at Trader Joe's.

---

# New Workflow 2: Bob creates a shopping list under $10

First Bob must establish his preferences, then he can look through the catalogue of all stores, with his set parameters, and then add them to a cart.
1. Bob starts by calling `PUT users/{user_id}/preferences` to set the maximum price per item to $10.
2. Then Bob calls `GET stores/catalogue?budget<10` to find all items where the value is under $10.
3. Next, Bob calls `POST users/{user_id}/shopping_list` to create a shopping cart.
4. Finally, Bob calls `PUT users/{user_id}/{list_id}/item` with the request body `{sku: cheese, quantity: 1}`, using the list ID generated from making the cart.

Bob now has a shopping list with an item added to it that is priced under $10.

---

# New Workflow 3: Carl changes his budget preferences and deletes a shopping list

First, Carl must edit his preferences, then go and delete the list.
1. Carl starts by calling `PUT users/{user_id}/preferences` to set the maximum price per item to $8, replacing his last set of preferences.
2. Then Carl calls `GET users/{user_id}/shopping_lists` to get the shopping list IDs of all the shopping lists he has.
3. Finally, Carl calls `DELETE users/{user_id}/{list_id}` to remove the desired shopping list.
