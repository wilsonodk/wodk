# Wodk Library

+ [DB](./#db-class)
> A MySQLi wrapper class with query formatting, table prefixing and "prepared" queries. 

+ [Logger](./#logger-class)
> A very simple logger that writes to disk.

+ [Twig Extensions](./#twigextensions-class)
> A few Twig filters that help with the Wodk Web App


## DB Class

A subclass of [MySQLi][]. It includes a few helper methods that assist with query formatting. Query formatting allows for a statement
to be written like `SELECT * FROM {{table}} WHERE id = %s`, then transformed into `SELECT * FROM myapp_table WHERE id = 1`.

* qry
> This will execute a SQL statement, but is extended to take arguments ala [sprintf][].
>
> @param — The first argument is the SQL statement.
>
> @param `...` — The following arguments are items to be formatted into the SQL statement.
>
> @returns — The query with all argments formatted.

* getInsertId
> @returns — Returns the insert id from the last INSERT query.

* setPrefix
> Will set the prefix to be used when formatting a query. Will determine if we need to use a prefix based on what is passed in.
>
> @param $prefix — A string to use a the prefix for tables in SQL statements.
>
> @returns — DB instance for chaining.

* setPrefixPattern
> Set the Regular Expression to used for prefix replacement. The default RegEx is `'/{{(\w+)}}/'`. See [preg_replace][] for more information.
>
> @param $pattern — A string of a RegEx pattern.
>
> @returns — DB instance for chaining.

* setQuery
> Set a "prepared" query for use later.
>
> @param — The name of the query for use later.
>
> @param — The SQL query.
>
> @param `...` — The arguments to be formatted into the query.
>
> @returns DB instance for chaining.

* unsetQuery
> Delete a "prepared" query.
>
> @param $name — The name of the query to remove.
>
> @returns — DB instance for chaining.

* getQuery
> Get a "prepared" query.
>
> @param $name — The name of the query to return.
>
> @returns — The formatted query.

* useQuery
> Call a previously "prepared" query.
>
> @param $name — The name of the query to use.

* getLastQuery
> Return the last query in it's "prepared" format.
>
> @returns — The formatted query that was last run.

* formatQuery
> Public "interface" for prepareQuery.
>
> @param — The SQL query.
>
> @param `...` — The arguments to be formatted into the query.
>
> @returns — Formatted query.

* prepareQuery
> Do the formatting of a query.
>
> @param $args — An array of items to format. First item is the SQL statement. Remaining items are to be formatted into SQL statement.
>
> @returns — The formatted query.


## Logger Class

A very simple logging class. The purpose of this class is to provide a
simple log file that can then be displayed to an administrative user of
the web app.

* log
> Record a particular message in the file. There are two ways to use it, simple or complex.
>
> Simple logging takes one argument, the log message. Writes an entry to the log as `[$timestamp] message`.
>
>> @param — The message.
>>
>> @returns — Logger instance for chaining.
>
> Complex logging takes at least two arguments. The first is the `type` of message. The remaining arguments are messages to log with that `type`. 
> Writes as entry to the log as `[$timestamp] ($type) $message`.
>
>> @param — The type of message; typically `error` or `message`. Any value is allowed.
>>
>> @param `...` — The messages to log as this `type`.
>>
>> @returns — Logger instance for chaining.

* error
> Log an error message with [sprintf][] formatting. Writes an entry to the log as `[$timestamp] ($type) $message`.
>
> @param — The message to use formatting.
>
> @param `...` — Arguments to format into the `$format` string.
>
> @returns — Logger instance for chaining.

* message
> Log a message with [sprintf][] formatting. Writes an entry to the log as `[$timestamp] ($type) $message`.
>
> @param — The mesage to use formatting.
>
> @param `...` — Arguments to format into the `$format` string.
>
> @returns — Logger instance for chaining.

* warn
> Log a warning with [sprintf][] formatting. Writes an entry to the log as `[$timestamp] ($type) $message`.
>
> @param — The mesage to use formatting.
>
> @param `...` — Arguments to format into the `$format` string.
>
> @returns — Logger instance for chaining.

* read
> Get the contents of the log, useful for passing from a Controller to a View.
>
> @param $as_array — Return the log file as a `string` or an `array`. Defaults to `string`.
>
> @param $reverse — What order to return the array. The default is oldest first.
>
> @returns — Either an array or string of the log file.

* writable
> Checks if the log file is writable.
>
> @returns — Boolean status of writability


## TwigExtensions Class

Two simple extensions to the [Twig][] template language.

* one_space 
> Converts all multi-spaces inside a string to a single string. This is really to cleanup the output of a Twig template. Very handy for whitespace sensive contexts.

* log_style
> Style a single line of Wodk\Logger output. Great for complex output. The `timestamp` is given the css class `stamp`. The `message` is given the css class of `type`.

* get_day
> Returns the day of the week in short format.

* no_wspace
> Removes all whitespace.


## Author

Wilson Wise

(c) 2012 Wilson Wise. All rights reserved.



[MySQLi]: http://us1.php.net/manual/en/book.mysqli.php
[sprintf]: http://us1.php.net/manual/en/function.sprintf.php
[preg_replace]: http://php.net/manual/en/function.preg-replace.php
[Twig]: http://twig.sensiolabs.org/
