Request

    curl -X 'GET' \   'https://meal-planner-9c99.onrender.com/recipes?ingredients=flour&ingredients=egg' \   -H 'accept: application/json'

Responce

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
Responce:

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

Responce:

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

Responce:

    Internal Server Error 500

Request: 

    curl -X 'DELETE' \ 'https://meal-planner-9c99.onrender.com/recipes/2'
     \ -H 'accept: application/json'

Responce:

	

    404 error: 
    	{ "detail": "Recipe was not found in db" }

Request:

    curl -X 'DELETE' \ 'https://meal-planner-9c99.onrender.com/recipes/23'
     \ -H 'accept: application/json'

Responce:
	

    { "deleted_complete": "Recipe deleted" }

Request:

    curl -X 'POST' \ 
    'https://meal-planner-9c99.onrender.com/carts/create/{cart_id}'
     \ -H 'accept: application/json' \ -d ''

Responce:

    Internal Server Error 500

Request: 

    curl -X 'POST' \
      'https://meal-planner-9c99.onrender.com/carts/create/1?customer_id=1&payment_id=1' \
      -H 'accept: application/json' \
      -d ''

Responce:

    Internal Server Error 500
Request:

    curl -X 'POST' \ 
    'https://meal-planner-9c99.onrender.com/carts/{cart_id}/items/{item_id}?ingredient_name=test&quantity=2' 
    \ -H 'accept: application/json' \ -d ''

Responce:

    Internal Server Error 500

    
Request:

    curl -X 'POST' \ 
    'https://meal-planner-9c99.onrender.com/carts/{cart_id}/checkout?customer_name=test&card_num=123123&exp_date=3212&customer_id=3'
     \ -H 'accept: application/json' \ -d ''

Responce:

    Internal Server Error 500

All of the carts stuff does not seem to work, some of the endpoints listen in v2_manual_test_results.md and in ExampleFlows.md do not seem to exist and they all return 500 errors when called.



