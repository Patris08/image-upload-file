## Setup
To run project:

1) Clone this repository

```
git clone git@github.com:Patris08/image-upload-file.git

```
2) Change location to project folder using command:
```
cd upload_file
```

3) In location where docker-compose.yml is run command:

```
docker-compose up
```

Note: If there is a problem with server, just press CTRL + C in terminal and run (docker-compose up) command once again - that should help.

4) With running docker container open second terminal window and paste this command (To create superuser):

```
docker-compose exec web python manage.py createsuperuser

```
* Enter your Username,
* Email (optional), 
* And Password.


## LOGIN:
### If you using browser go directly to: http://0.0.0.0:8000/
* Login as a superuser you created
* Create an account (admin panel)
* You can change membership for each user in "Profiles" (admin panel) default membership = BASIC.
* Upload image, you can pick up some.
* See result on: (http://0.0.0.0:8000/   +   small_image_link), or just (CTRL + right mouse button on link in postman)

### If you use postman go to: http://0.0.0.0:8000/api-auth/login/
* send GET request to recive token
* in HEADERS create 

(KEY: X-CSRFToken VALUE: >TokenYouRecived<

* in BODY/form-data create

(KEY: username VALUE: yourusername)

(KEY: password VALUE: yourpassword)
* send POST request

If You login successfully you will be redirected to the adress: accounts/profile/ (that does not exist)
* you can now visit http://0.0.0.0:8000/


## To see binary data you must generate expiring token

### Visit: http://0.0.0.0:8000/api-token-auth/

#### In postman set: body/raw/JSON
* Send username and password as POST request, example:


{
    "username":
        "Yourusername",
    "password":
        "yourpassword" 
}




You will recive New Token.

### Visit: http://0.0.0.0:8000/binary/

### In Headers:
* Create (KEY: Authorization  VALUE: Token >token_you_received<)
* Send that token as GET request, example:

* KEY: Authorization VALUE: Token dv284f7f96cd92345435fdg4352f33e13432d




Token expires afetr time set via uploading photo (default=300, max =30000 seconds)

