
<!-- abc 
	================================================== -->
	<section id="product"><div class="container"><div class="row">
		<!-- .row -->

		<div class="col-lg-3"><div class="card box-shadow filter">
			<!-- .filter -->

			<h5>Filters:</h5>

			<div class="custom-control custom-checkbox">
				<input type="checkbox" class="custom-control-input" id="man"
				[(ngModel)]="man" (change)="filterByCategory('man', man)">
				<label class="custom-control-label" for="man">Man</label>
			</div>

			<div class="custom-control custom-checkbox">
				<input type="checkbox" class="custom-control-input" id="women"
				[(ngModel)]="women" (change)="filterByCategory('women', women)">
				<label class="custom-control-label" for="women">Women</label>
			</div>

			<!-- ./filter -->
		</div></div>


		<div class="col-lg-9">
			<!-- .data  -->

			<div *ngIf="items$ | async; let items; else loading"><div class="row">

				<div class="col-lg-4 col-md-4 col-sm-6" *ngFor="let item of items">
					<div class="card mb-4 box-shadow text-center">
						<img class="card-img-top" src="assets/MiracleSoap.jpg">
						<div class="card-body">
							<h5>{{ item.name }}</h5>
							<p>{{ item.description }}</p>
							<h5 class="text-primary">PKR {{ item.price }}</h5>
							
							<hr><div class="row">
								<div class="col-9 view-detail">
									<button class="detail" type="button" data-toggle="modal" data-target="#product-modal">View details</button>
								</div>
								<div class="col-3 add-cart">
									<button class="cart" type="button"><i class="fas fa-shopping-cart"></i></button>
								</div>
							</div>


						</div></div></div>


						<div class="col-lg-12 result" *ngIf='items.length === 0'>No results, try clearing filters</div>
					</div></div>

					<!--  ./data -->
					<ng-template #loading>
						<div class="col-lg-12"><app-spinner></app-spinner></div>
					</ng-template>
				</div>

				<!-- ./row -->
			</div></div></section>

/* Filter
================================================== */

.filter {
	padding: 1.5rem 1rem;
}

.custom-checkbox .custom-control-input:checked~.custom-control-label::before {
	background-color: var(--heading-color);
}




  items$: Observable<Item[]>;
  result$: Observable<Item[]>;
  //result$: any;

  private itemsCollection: AngularFirestoreCollection<Item>;

  //items: Observable<Item[]>;
  //results: Observable<Item[]>;
  //showSpinner: boolean = true;
 //items: any;
 //results: any;
 
// filter-able properties
//category: string;
//man: BehaviorSubject<boolean>;
//sizeFilter$: BehaviorSubject<string|null>;
man : boolean;
women: boolean;

//price: number;

// Active filter rules
//filters = {}

constructor(afs: AngularFirestore) {
  //this.man = new BehaviorSubject(false);
  this.itemsCollection = afs.collection<Item>('items');
  this.result$ = this.itemsCollection.valueChanges();
  //this.result$ = this.itemsCollection;
  this.items$ = this.result$;
}
/*
filterByCategory(category: string|null) {

  if(category == 'man') {
  this.items$ = _.filter(this.result$, ['category', 'man']);
  }  
}*/

// https://stackoverflow.com/questions/46423787/angular-4-rxjs-filter-data-in-observable-array
filterByCategory(property: string, rule: boolean) {
  if (property == 'man' && rule == true) {
    this.women = false;
    return this.items$ = this.result$.map(result$ => {
      return result$.filter((item: Item) => item.category === "man");
  });
  
/*
    return this.items$
    .map(items$ => {
      let fl = items$.filter(item => item.category === 'man');
      return (fl.length > 0) ? fl[0] : null;
    });*/

    //return this.items$.filter(item => item.category === 'man');
    //return this.items$ = Observable.of(_.filter(this.result$, ['category', 'man']));

    //return this.items$ = _.filter(this.result$, ['category', 'man']);

  } else if (property == 'women' && rule == true) {
    this.man = false;
    return this.items$ = this.result$.map(result$ => {
      return result$.filter((item: Item) => item.category === "women");
  });
  } else {
    return this.items$ = this.result$;
    //return this.items$.filter(item => item.category === 'woman');
    //return this.items$ = Observable.of(_.filter(this.result$, ['category', 'man']));

  }
}

}

import { Observable } from 'rxjs/Observable';
import { BehaviorSubject } from 'rxjs/BehaviorSubject';
import * as _ from 'lodash';

import { Item } from '../../shared/item.model';
//import { ItemService } from '../../shared/item.service';
import { AngularFirestore, AngularFirestoreCollection } from 'angularfire2/firestore';

export class Item {
  $id: string;
  name: string;
  description: string;
  imagePath: string;
  price: string;
  category: string;
  status: string;
  //timeStamp: number;
}

https://drive.google.com/open?id=1FlVy51UXRaCNgIXuSc_seaAAZ7ZiSc0x

https://drive.google.com/open?id=1bAukNQLatyvJZuzHUC-wFO2SWklXENWX
https://drive.google.com/file/d/1xSzLhNdyP9czw_IxDHkBJXR4fUVzcl94/view?usp=sharing

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
