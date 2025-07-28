# Cookies and Sessions Lab
This lab builds out a paywall feature by using session to keep track of how many page views a user has made. If a user tries to view more than three pages, access is blocked and they recieve a message stating they have viewed the maximum number of pages.

### Getting Started
* Create a virtual environment
    ```bash
    virtualenv venv
    source venv/bin/activate
    ```
* Install all Necessary Dependencies 
    ```bash
    pip install flask-sqlalchemy flask-migrate
    pip install marshmallow
    pip install faker
    npm install --prefix client
    ```
* Upgrade and Seed the Database
    ```bash
    cd server
    flask db upgrade
    python seed.py
    ```

### Running the Application
* Run the Flask server
    ```bash
    python app.py
    ```
* Run the React App <br>
`in a second terminal`
    ```bash
    npm start --prefix client
    ```

### API Endpoints
* `GET /articles` <br>
Gets a list of all of the articles
* `GET /articles/<int:id>` <br>
Gets a single article <br>
**Example Response:**
```JSON
  {
      "author": "Shirley Patterson",
      "content": "Sing moment include because affect time...",
      "date": "2025-07-28T15:24:09",
      "id": 1,
      "minutes_to_read": 20,
      "preview": "Sing moment include becau...",
      "title": "Accept these test.",
      "user": {
          "id": 1,
          "name": "Rose Baker"
      }
  }
```
After viewing three articles, if the user tries to view a fourth, they will recieve this message:
```JSON
{
    "message": "Maximum pageview limit reached"
}
```
* `/clear` <br>
clears the session so more articles can be viewed <br>
**Example Response:**
```JSON
{
    "message": "200: Successfully cleared session data."
}
```

