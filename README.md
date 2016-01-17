# Reto1Backend
var express = require('express');
var app = express();
var faker = require('faker');
var _ = require('lodash');

var generarUsuario = function(){
  var randomId = faker.phone.phoneNumber();
  var randomName = faker.name.findName();
  var randomlorem = faker.lorem.sentence();
  var randomDate = faker.date.recent();
  var randomEmail = faker.internet.email();
  var randomImage = faker.image.avatar();
  return {
    Id: randomId,
    nombre: randomName,
    Contenido: randomlorem,
    Fecha: randomDate,
    email: randomEmail,
    imagen: randomImage
  }

}

app.get('/', function (req, res) {
  res.send('Mi primer servidor!');
})

app.get('/posts', function (req, res) {
  var cantidad = _.random(5,10)
  var usuarios = _.times(cantidad, generarUsuario)
  res.json(usuarios);
})

app.get('/amigos', function (req, res) {
  res.send('Mis amigos');
})


app.listen(3000);
