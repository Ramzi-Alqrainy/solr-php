solr-php
========

A PHP library for indexing and searching documents within an Apache Solr installation.



Features : 
-------------------------------------------------
1. Comapatable with Solr 7.x
2. Quering, deleting, optimizing.
3. Fast by using curl instead of file_get_content
4. Using json for indexing instead of xml and you can use xml.



Installation : 
-------------------------------------------------
Install Composer In Your Project

``` curl -sS https://getcomposer.org/installer | php ```

Install Solr PHP Client Library In Your Project

``` vim composer.json ```

``` 
"require": {

    "Ramzi-Alqrainy/solr-php": "dev-master",
    
}
```

``` $ php composer.phar install ```

How to use it : 
-------------------------------------------------
Normal querying of Solr is very simple with this library to show an example:

```php
		// Build Solr query
		$options = array (
				'qf' => 'contact_ss ',
				'q.op' => 'OR',
				'defType' => 'edismax',
				'sort' => 'contact_id desc',
		);
Yii::$app->solr->get ( $query, $offset, $limit, $options );
var_dump($results->response->numFound);
```

That is what it takes to query Apche Solr.
should use `Yii::$app->solr` (or whatever you have called the Solr application component in your configuration).

To setup the application you merely add it to your configuration. As an example:

```php
    'components' => [
    	'solr'=>[
    		'class'=>'common\components\ApacheSolr',
    		'host'=>'localhost',
    		'port'=>8983,
    		'indexPath'=>'/solr/collection1'
    	],
```

