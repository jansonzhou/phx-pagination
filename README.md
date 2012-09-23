# phx-pagination

> ExpressJS + Mongoose ORM (ExpressJS/NodeJS/MongoDB) Document Query Pagination

## Installation

```bash
$ npm install phx-pagination
```

## Usage 

```javascript

/**
 * basic example usage of `phx-pagination`
 **/
require('phx-pagination').init(app);

/** 
 * Action wich display a country list page
 */	
app.get('/', function (req, res) {
   var page = req.param('page') || 1;
   Country.paginate({limit: 15, page: page}, function (error, countries) {
     if (error) {
        console.error(error);
     } else {
        res.render('countries/index', { title: 'Country List', countries: countries });		
     }
   });
});

```

```html

<div id="main">
   <% countries.forEach(function (country) { %>
      <div class="span-two-thirds">
           country: <%= country.name %> 
      </div>
      <div class="span-one-third">
	<a href="/show/<%= country.id %>">Show</a>
	<a href="/delete/<%= country.id %>" onclick="return confirm('Are you sure you want to delete?')">Delete</a>
      </div>
    <% }); %>
    <%- paginate(countries) %>
</div>

```

## Author: [Physalix][0]

[0]: http://www.physalix.com/

## License

MIT