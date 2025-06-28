create virtual environment
python -m venv vevv

activate virtual environment
Linux/mac -> source venv/bin/activate
Windows -> ./venv/Scripts/activate
Bash -> source venv/Scripts/activate

pip install fastapi uvicorn

create requirements file (It helps to store required package, so whenever next time any other person use they have to only go with requirements and all set.)
-> pip freeze > requirements.txt


Run the app

uvicorn main:app --reload

Now open localhost url of your project and do check your api is working or not 
for doing some operation like delete or insert is not possible through link so we can use Postman API 

But FAST API Provide SWAGGER INTEGRATION BY Default
Access through links just add "docs" in the end of localhost url
like this -> http://127.0.0.1:8000/docs

And it open Awesome UI you dont need Postman After using This.
