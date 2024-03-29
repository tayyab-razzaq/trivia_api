# Full Stack Trivia API Backend

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

## Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

## Running the server

From within the `backend` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

Setting the `FLASK_ENV` variable to `development` will detect file changes and restart the server automatically.

Setting the `FLASK_APP` variable to `flaskr` directs flask to use the `flaskr` directory and the `__init__.py` file to find the application. 

## Tasks

One note before you delve into your tasks: for each endpoint you are expected to define the endpoint and response data. The frontend will be a plentiful resource because it is set up to expect certain endpoints and response data formats already. You should feel free to specify endpoints in your own way; if you do so, make sure to update the frontend or you will get some unexpected behavior. 

1. Use Flask-CORS to enable cross-domain requests and set response headers. 
2. Create an endpoint to handle GET requests for questions, including pagination (every 10 questions). This endpoint should return a list of questions, number of total questions, current category, categories. 
3. Create an endpoint to handle GET requests for all available categories. 
4. Create an endpoint to DELETE question using a question ID. 
5. Create an endpoint to POST a new question, which will require the question and answer text, category, and difficulty score. 
6. Create a POST endpoint to get questions based on category. 
7. Create a POST endpoint to get questions based on a search term. It should return any questions for whom the search term is a substring of the question. 
8. Create a POST endpoint to get questions to play the quiz. This endpoint should take category and previous question parameters and return a random questions within the given category, if provided, and that is not one of the previous questions. 
9. Create error handlers for all expected errors including 400, 404, 422 and 500. 

REVIEW_COMMENT
```
This README is missing documentation of your endpoints. Below is an example for your endpoint to get all categories. Please use it as a reference for creating your documentation and resubmit your code. 

Endpoints
GET '/categories'
GET ...
POST ...
DELETE ...

GET '/categories'
- Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Request Arguments: None
- Returns: An object with a single key, categories, that contains a object of id: category_string key:value pairs. 
{'1' : "Science",
'2' : "Art",
'3' : "Geography",
'4' : "History",
'5' : "Entertainment",
'6' : "Sports"}

```

API Endpoints Documentation
--------------------------------------------------------
GET `'/categories'`

- Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Request Arguments: None
- Returns: An object with a single key, categories, that contains a object of id: category_string key:value pairs.

```json5
{
    "categories": {
        "1": "Science",
        "2": "Art",
        "3": "Geography",
        "4": "History",
        "5": "Entertainment",
        "6": "Sports"
    },
    "success": true
}
```

GET `'/questions'`

- Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Fetches a list of questions in which each entry is question dictionary with the keys are answer, category, difficulty, id and question.
- Request Arguments: Page Number
- Returns: Dictionary of Categories, Current Category, List of questions and total number of questions.

```json5
{
	"categories": {
		"1": "Science",
		"2": "Art",
		"3": "Geography",
		"4": "History",
		"5": "Entertainment",
		"6": "Sports"
	},
	"current_category": null,
	"questions": [
		{
			"answer": "Apollo 13",
			"category": 5,
			"difficulty": 4,
			"id": 2,
			"question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
		},
		{
			"answer": "Tom Cruise",
			"category": 5,
			"difficulty": 4,
			"id": 4,
			"question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
		},
		{
			"answer": "Maya Angelou",
			"category": 4,
			"difficulty": 2,
			"id": 5,
			"question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
		},
		{
			"answer": "Edward Scissorhands",
			"category": 5,
			"difficulty": 3,
			"id": 6,
			"question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
		},
		{
			"answer": "Muhammad Ali",
			"category": 4,
			"difficulty": 1,
			"id": 9,
			"question": "What boxer's original name is Cassius Clay?"
		},
		{
			"answer": "Brazil",
			"category": 6,
			"difficulty": 3,
			"id": 10,
			"question": "Which is the only team to play in every soccer World Cup tournament?"
		},
		{
			"answer": "Uruguay",
			"category": 6,
			"difficulty": 4,
			"id": 11,
			"question": "Which country won the first ever soccer World Cup in 1930?"
		},
		{
			"answer": "George Washington Carver",
			"category": 4,
			"difficulty": 2,
			"id": 12,
			"question": "Who invented Peanut Butter?"
		},
		{
			"answer": "Lake Victoria",
			"category": 3,
			"difficulty": 2,
			"id": 13,
			"question": "What is the largest lake in Africa?"
		},
		{
			"answer": "The Palace of Versailles",
			"category": 3,
			"difficulty": 3,
			"id": 14,
			"question": "In which royal palace would you find the Hall of Mirrors?"
		}
	],
	"total_questions": 26,
	"success": true
}
```

DELETE `'/questions/<int:question_id>'`

- Delete question from the questions in database.
- Request Arguments: questions_id(Question Id)
- Returns: true with status 204 if successfully deleted.

```json5
{
    "success": true
}
```

POST `'/questions'`

- Create a new question
- Request Body: question, answer, difficulty and category.
- Returns: true and question id with status 201 if successfully created.

Request

```json5
{
    "question": "Test 1",
    "answer": "Answer 1",
    "category": 1,
    "difficulty": 1
}
```

Response

```json5
{
    "success": true,
    "id": 15
}
```

POST `'/questions/filter'`

- Searches for the questions
- Request Body: search term to search question on that.
- Returns: List of questions and total number of questions.

Request

```json5
{
    "searchTerm": "The"
}
```

Response

```json5
{
	"questions": [
		{
			"answer": "Maya Angelou",
			"category": 4,
			"difficulty": 2,
			"id": 5,
			"question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
		},
		{
			"answer": "Tom Cruise",
			"category": 5,
			"difficulty": 4,
			"id": 4,
			"question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
		},
		{
			"answer": "Edward Scissorhands",
			"category": 5,
			"difficulty": 3,
			"id": 6,
			"question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
		},
		{
			"answer": "Brazil",
			"category": 6,
			"difficulty": 3,
			"id": 10,
			"question": "Which is the only team to play in every soccer World Cup tournament?"
		},
		{
			"answer": "Uruguay",
			"category": 6,
			"difficulty": 4,
			"id": 11,
			"question": "Which country won the first ever soccer World Cup in 1930?"
		},
		{
			"answer": "Lake Victoria",
			"category": 3,
			"difficulty": 2,
			"id": 13,
			"question": "What is the largest lake in Africa?"
		},
		{
			"answer": "The Palace of Versailles",
			"category": 3,
			"difficulty": 3,
			"id": 14,
			"question": "In which royal palace would you find the Hall of Mirrors?"
		},
		{
			"answer": "The Liver",
			"category": 1,
			"difficulty": 4,
			"id": 20,
			"question": "What is the heaviest organ in the human body?"
		},
		{
			"answer": "Blood",
			"category": 1,
			"difficulty": 4,
			"id": 22,
			"question": "Hematology is a branch of medicine involving the study of what?"
		},
		{
			"answer": "Scarab",
			"category": 4,
			"difficulty": 4,
			"id": 23,
			"question": "Which dung beetle was worshipped by the ancient Egyptians?"
		}
	],
	"total_questions": 10,
	"success": true
}
```

POST `'/categories/<int:category_id>/questions'`

- To get questions based on category
- Request Arguments: category_id (Category Id).
- Returns: List of questions, total number of questions and current category.

for category 1 response is below

```json5
{
	"current_category": {
		"id": 1,
		"type": "Science"
	},
	"questions": [
		{
			"answer": "The Liver",
			"category": 1,
			"difficulty": 4,
			"id": 20,
			"question": "What is the heaviest organ in the human body?"
		},
		{
			"answer": "Alexander Fleming",
			"category": 1,
			"difficulty": 3,
			"id": 21,
			"question": "Who discovered penicillin?"
		},
		{
			"answer": "Blood",
			"category": 1,
			"difficulty": 4,
			"id": 22,
			"question": "Hematology is a branch of medicine involving the study of what?"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 24,
			"question": "Test 1"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 25,
			"question": "Test 1"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 26,
			"question": "Test 1"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 27,
			"question": "Test 1"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 28,
			"question": "Test 1"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 29,
			"question": "Test 1"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 31,
			"question": "Test 1"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 33,
			"question": "Test 1"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 35,
			"question": "Test 1"
		},
		{
			"answer": "Answer 1",
			"category": 1,
			"difficulty": 1,
			"id": 37,
			"question": "Test 1"
		}
	],
	"total_questions": 13,
	"success": true
}
```

POST `'/quizzes'`

- To get questions to play the quiz.
- Returns: Random question within the given category.

Request

```json5
{
    "quiz_category": {
        "id": 1
    },
    "previous_questions": []
}
```

Response

```json5
{
    "question": {
        "answer": "Blood", 
        "category": 1, 
        "difficulty": 4, 
        "id": 22, 
        "question": "Hematology is a branch of medicine involving the study of what?"
    },
    "success": true
}
```

Errors
--------------------------------------------------------

Bad Request `400`

```json5
{
  'success': false,
  'error': 400,
  'message': 'Bad Request'
}
```

Unauthorized `401`

```json5
{
  'success': false,
  'error': 401,
  'message': 'Unauthorized'
}
```

Forbidden `403`

```json5
{
  'success': false,
  'error': 403,
  'message': 'Forbidden'
}
```

Not Found `404`

```json5
{
  'success': false,
  'error': 404,
  'message': 'Not Found'
}
```

Method Not Allowed `405`

```json5
{
  'success': false,
  'error': 405,
  'message': 'Method Not Allowed'
}
```

Unprocessable Entity `422`

```json5
{
  'success': false,
  'error': 422,
  'message': 'Unprocessable Entity'
}
```

Internal Server Error `500`

```json5
{
  'success': false,
  'error': 500,
  'message': 'Internal Server Error'
}
```

## Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```