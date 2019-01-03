# Datatable server configuration

## Features
 - Search
	 - On all columns
	 - On each column
 - Sort
 - Search & sort on relations
 - Server-side pagination

## Frameworks
 - [x] Vue
 - [x] Laravel
 - [ ] Django

## To Do

 - [ ] Modify date search for jalali
 - [ ] Export all data

## Vue

 - Include jquery datatable (it's easier with CDN)
 - Add name field to each column
 - Does not work for merged columns (like name = first_name + last_name)

		let tableId = '#table-id';
		this.table = $(tableId).DataTable({
			ajax: this.endpoint("apiUrl?token=" + this.token),
			processing: true,
	       serverSide: true,
	       ...datatableOptions
		});

		this.table.on("init", () => {
		  $(tableId + " thead th").each(function() {
		    var title = $(this).text();
		    if (title == "") {
		      return;
		    }
		    $(tableId + " thead tr")
		      .first()
		      .append(
		        "<th><input class='form-control' type='text' placeholder='فیلتر" + title + "' /></th>"
		      );
		  });
		  this.table.columns().every(function() {
		    var that = this;
		    $(
		      "input",
		      $(tableId + " thead tr th").eq($(this.header()).index())
		    ).on("keyup change", function() {
		      if (that.search() !== this.value) {
		        that.search(this.value).draw();
		      }
		    });
		  });
		});


## Laravel
```
composer require yajra/laravel-datatables-oracle:^8.0
```
	$query = users:all(); // Do anything you want
	return DataTables
	    ::of($query)
        ->toJson();




> Written with [StackEdit](https://stackedit.io/).
