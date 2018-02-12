
https://drive.google.com/open?id=0B0anNhb3Xf1JWHZLbDlBUHM4X1k
https://drive.google.com/open?id=1vL-gXAEZ0qkxVESVjGYiz7yr97YPqGHt

'use strict';

var request = require("request");
var cheerio = require("cheerio");
var fs  = require("fs");



let jsonData = require('./student.json');
//console.log(jsonData);  
jsonData.name = 'Saeed';

//console.log(jsonData);  

let data = JSON.stringify(jsonData);  
//console.log(data);  
fs.writeFileSync('./student.json', data);

/*
let student = {  
    name: 'Mike',
    age: 23, 
    gender: 'Male',
    department: 'English',
    car: 'Honda' 
};

let data = JSON.stringify(student);  
fs.writeFileSync('student.json', data);  

/*
fs.readFile('./student.json', (err, data) => {  
    if (err) throw err;
    let student = JSON.parse(data);
    console.log(student);
});


let student = {  
    name: 'Mike',
    age: 23, 
    gender: 'Male',
    department: 'English',
    car: 'Honda' 
};

let data = JSON.stringify(student, null, 2);

fs.writeFile('student.json', data, (err) => {  
    if (err) throw err;
    console.log('Data written to file');



});

console.log('This is after the write call');  */

/*
var data = fs.readFileSync('no.txt', 'utf8');
console.log(data);

var words = JSON.parse(data);
//var bodyparser=require('body-parser');
console.log(words);*/


/*
var inputText = "'foofo21' 'bar432' 'foobar12345'";
function processText(inputText) {
    var output = [];
    var json = inputText.split(' ');
    json.forEach(function (item) {
        output.push(item.replace(/\'/g, '').split(/(\d+)/).filter(Boolean));
    });
    return output;
}

console.log(JSON.stringify(processText(inputText)));*/

//var adr = '';
//var array = fs.readFileSync(path).toString().split('\n');
/*
function s(age) {
    return age != 0;
}

function checkAdult(age) {
    return age != 0;
}

const readFileAsArray = function(file, cb = () => {}) {
  return new Promise((resolve, reject) => {
    fs.readFile(file, function(err, data) {
      if (err) {
        reject(err);
        return cb(err);
      }
    //console.log('Data:', data.toString().trim().split(/(\d+)/).filter(n => n.length === 6));
  //String[] splited = str.split("\\s+");

      const lines = data.toString().trim().split(/(\d+)/).filter(n => n.length === 6);
      resolve(lines);
      cb(null, lines);
    });
  });
};

async function countOdd () {
  try {
    const lines = await readFileAsArray('./numbers.txt');
    const numbers = lines.map(Number);
    console.log('Numbers:', numbers);
    const oddCount = numbers.filter(n => n%2 === 1).length;
    //console.log('Odd numbers count:', oddCount);
  } catch(err) {
    console.error(err);
  }
}
countOdd();




request({
  uri: "",
}, function(error, response, body) {

  if (error) 
    return console.error(error)

  var $ = cheerio.load(body);
  console.log($.html())

});*/

/*
fs.readFile('', function(err, data) {
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.write(data);
    res.end();
  });*/


/*
try {  
    var data = fs.readFileSync(adr, 'utf8');
    console.log(data);    
} catch(e) {
    console.log('Error:', e.stack);
}*/

/*
var url = require('url');
//Parse the address:
var q = url.parse(adr, true);
console.log(q);*/



/*
request({
  uri: "t",
}, function(error, response, body) {

  if (error) 
    return console.error(error)

  var $ = cheerio.load(body);
  console.log($.html())

});*/

/*
request({
  uri: "",
}, function(error, response, body) {

  if (error) 
    return console.error(error)

  var $ = cheerio.load(body);

  $("a").each(function() {
    var link = $(this);
    var text = link.text();
    var href = link.attr('href');
    var ref = link.attr('rel');
    //console.log(ref);

    var pathURLs = []
    if (ref == 'noopener noreferrer') {
      //pathURLs.push(domain + href);
      console.log('Rs.100 : '+text+' : '+href);
    }
  });

});*/


/*

var domain = ''
request(domain, gotHTML)

//function gotHTML(err, resp, html) {
function gotHTML(error, response, body) {

  if (error) 
    return console.error(error)
  
  var parsedHTML = $.load(html)
 
//console.log(parsedHTML.html())


  // get all img tags and loop over them
  var imageURLs = []
  parsedHTML('a').map(function(i, link) {



    var href = $(link).attr('href')
console.log(href.html)

//var link = $(this);
  //  var text = link.text();
   // var href = link.attr("href");

    if (!href.match('.txt')) 
      return
    imageURLs.push(domain + href)
  })

//console.log(imageURLs)

}

*/

//var https = require('follow-redirects').https;
//var querystring = require('querystring');
//var extend = require('util')._extend;
//var firebase = require('firebase-admin');


//var $ = require("cheerio");
//var request = require("request");

// https://www.sitepoint.com/web-scraping-in-node-js/
// https://maxogden.com/scraping-with-node.html
// https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction
// http://expressjs.com/en/starter/hello-world.html
// console.log("Hello, World!");
/*
var html = "<ul><li>foo</li><li>bar</li></ul>";
var $ = cheerio.load(html);
var list = $("ul");

console.log(list.html());*/

/*
function gotHTML(err, resp, html) {
  if (err) 
  	return console.error(err)
  
  var parsedHTML = $.load(html)
 
//console.log(parsedHTML.html())


  // get all img tags and loop over them
  var imageURLs = []
  parsedHTML('a').map(function(i, link) {



    var href = $(link).attr('href')
console.log(href.html)

//var link = $(this);
  //  var text = link.text();
   // var href = link.attr("href");

    if (!href.match('.txt')) 
    	return
    imageURLs.push(domain + href)
  })

//console.log(imageURLs)

}

var domain = ''
request(domain, gotHTML)
*/
/*
request({
  uri: "http://www.sitepoint.com",
}, function(error, response, body) {
  var $ = cheerio.load(body);

  $(".entry-title > a").each(function() {
    var link = $(this);
    var text = link.text();
    var href = link.attr("href");

    console.log(text + " -> " + href);
  });
});


var cheerio = require('cheerio'),
    $ = cheerio.load('<h2 class = "title">Hello world</h2>');

$('h2.title').text('Hello there!');
$('h2').addClass('welcome');

$.html();*/
