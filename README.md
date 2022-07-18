Backend-work-ALL-actions-for-login-users

Proyecto backend (A utilizar con postman y navegador) que permite:

·Registrarse (user, email, password, image) ·Logearse(Obtencion de token) ·Editar ·Cambiar contraseña(uso de tokens y confirmacion via mail) ·Posteo(con token) ·Borrar usuario ·Mostrar lista de usuarios ·Mostrar lista de usuarios con id ·Mostrar posteos ·Mostrar posteos con palabras clave

Verificaciones

Todas las acciones requieren de un pase por validaciones para poder ser aceptadas Ej: para editar postear es requerido un token entregado al usuario al registrarse

Ejecusion de acciones Postman

Getusers => GET - http://localhost:3000/users

GetusersById => GET - http://localhost:3000/users/NUMERO_ID

Register => POST - http://localhost:3000/users/register (con form-data ya que se puede cargar una imagen, no obligatoria)

Login => POST - http://localhost:3000/users/login (Formato JSON, email y password) 
Ej: { "email" : "babs@batgirl.com", "password" : "as47d65a4sd" }

DeleteUser => DELETE - http://localhost:3000/users/NUMERO_ID

EditUserById => PATCH - http://localhost:3000/users/NUMERO_ID (Con form data si se quiere cambiar imagen)

ForgotPassword => POST - http://localhost:3000/users/forgot-password (Envia mail via mailtrap, se requiere cambiar los datos en el .env, esto envia a pagina laburada desde el fronted para cambiar la contraseña, requiere token y hacerlo en menos de 15min)

CreatePost => POST - http://localhost:3000/posts (Con raw y json) 
EJ: { "title" : "Jack white, el archienemigo de Jack Black", "body": "kasdkahsdkhasdh A.K.A jack white (nombre artistico) alguna vez estuvo casado con Meg White, dandole vida asi al duo de rock Whites Stripes" }

GetAllPosts - GET - http://localhost:3000/posts

GetPostWithKeyWords - Get - http://localhost:3000/posts?title=PALABRA_CLAVE_EN_TITULO

////////////////////////////////////////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////////////////////////////////////////
.env////////////////Laburar con usuario de mailtrap y contraseña propia en el archivo .env////////////////// 
////////////////////////////////////////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////////////////////////////////////////

port = 3000 db_host = localhost db_name = api_2 db_user = root db_pass = public_url = http://localhost:3000 jwt_secret =%Pr1v4t3*KEy@ mailtrap_user = mailtrap_pass=

////////////////////////////////////////////////////////////////////////////////////////////////////////////
//////////////////////////////////////////////////////////////////////////////////////////////////////////// 
DATABASE////////////////////////////////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////////////////////////////////////////

CREATE DATABASE api_2;

USE api_2;

CREATE TABLE users ( id int(11) AUTO_INCREMENT PRIMARY KEY, name varchar(90) NOT NULL, email varchar(255) NOT NULL UNIQUE, password varchar(255) NOT NULL, image varchar(255) );

insert into users values(null, "Leanne Graham", "sincere@april.biz", "Bret123"); insert into users values(null, "Shanna Leona Williams", "shanna@melissa.tv", "antonette"); insert into users values(null, "Clementine Bauch", "nathan@yesenia.net", "kukiIceCream"); insert into users values(null, "Patricia Lebsack", "julianne.oconner@kory.org", "12_annieRuOk"); insert into users values(null, "Miguel Ángel Jackson", "lucio_hettinger@annie.ca", "smoothCRIMINAL"); insert into users values(null, "Juan Antonio Ferreyra", "karley_dach@jasper.info", "riffSeveN"); insert into users values(null, "Kurtis Weissnat", "Telly.hoeger@billy.biz", "Elwyn.Skiles"); insert into users values(null, "Luciano Nicolás Pavarotti", "sherwood@rosamond.me", "BBPIe44"); insert into users values(null, "Glenna Reichert", "chaim_mcdermott@dana.io", "DOLP-phine_800"); insert into users values(null, "Clementina DuBuque", "rey.padberg@karina.biz", "BLACKhole*SUN");

CREATE TABLE posts ( id int(11) AUTO_INCREMENT PRIMARY KEY, userid int(11), title varchar(124), body text, FOREIGN KEY (userid) REFERENCES users (id) )

INSERT INTO posts VALUES(null, 1, "sunt aut facere repellat provident occaecati excepturi optio reprehenderit", "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"); INSERT INTO posts VALUES(null, 2, "qui est esse", "est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla");
