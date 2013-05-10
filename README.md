CompilerServiceProvider
=======================

A css compiler for silex

Installation
------------

	cd path/to/your/application
	git clone git@github.com:doddsey65/CompilerServiceProvider.git vendor/cjmarkham/src/Cjmarkham/CompilerServiceProvider

Registering
-----------

In composer.json add to your autoload psr

	"Cjmarkham" : "vendor/cjmarkham/src"

Then to register

	$app->register(new Cjmarkham\CompilerServiceProvider\CompilerServiceProvider());

Options
-------

* ```compiler.shorten_hex``` - Shorten hexadecimal values. Default `false`
* ```compiler.short_values``` - Shorten values. Eg\ `margin:10px 0 10px 0` to `margin:10px 0` Default `true`
* ```compiler.remove_empty``` -Removes empty rules. Default `false`
* ```compiler.remove_units``` - Remove un-needed units. Eg\ `0px` to `0` Default `true`
* ```compiler.rgb_to_hex``` - Converts rgb values to hex values. Default `false`
* ```compiler.input_dir``` - The directory containing your css. `Required`
* ```compiler.output_path``` - The path to save compiled css to. Default `compiler.input_dir / compiled.css`

Usage
-----

	$app->register(new Cjmarkham\CompilerServiceProvider\CompilerServiceProvider(), array(
	    'compiler.shorten_hex' => true,
	    'compiler.rgb_to_hex' => true,
	    'compiler.remove_empty' => true,
	    'compiler.input_dir' => __DIR__ . '/css',
	    'compiler.output_path' => __DIR__ . '/css/compiled.css'
	));

	$app['compiler']->compile();