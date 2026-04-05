from flask import Flask

app = Flask(__name__)


@app.route("/")
def home():
    return "Flask App is now running ;)"


@app.route("/about")
def about():
    return """
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>My Flask App</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                text-align: center;
                padding: 50px;
                background-color: #f4f4f4;
            }
            h1 {
                color: #333;
            }
        </style>
    </head>
    <body>
        <h1>Welcome to My Flask App!</h1>
        <p>This is a very basic home page.</p>
        <p>Server is running successfully </p>
    </body>
    </html>
    """


if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000, debug=True)
