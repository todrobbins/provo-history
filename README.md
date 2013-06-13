Provo History
=============
This repo will serve as a collection of notes and structured data for the history of [Provo, Utah](https://en.wikipedia.org/wiki/Provo,_Utah)

Early Provo (Utah) Organizations/Locales
----------------------------------------

* Provo Dramatic Association
* Provo Martial Band
 * Founded by Dominicus Carter
* Provo Opera House

Data Schema
-----------
We will be utilzing the [Mormon-Primary-Sources](https://github.com/opensourcehistory/Mormon-Primary-Sources)/[Mormon-Missionaries](https://github.com/opensourcehistory/Mormon-Missionaries) ( [Open Source History](https://github.com/opensourcehistory) ) schema for documentation:

> Additional keys may be used and not all keys will be present in each document. This facilitates scaling the data as the repository grows and the variability between sources increases. The document-oriented structure of this system encourages providing as much data as desired, but each data value must have a key. The Indexing Syntax section describes how the information is to be encoded to allow for easy parsing by search indexers.

    /* Primary Information */
    "name": [object]
      "last": [string]
    	"first": [string]
    	"middle": [string]
    	"married": [string]
    	"suffix": [string]
    	"additional": [array]
    	"patronymic": [string]
    	"matronymic": [string]
    	"maternalSurname": [string]
    	"paternalSurname": [string]
    
    "aliases": [array] [string or name object]
    
    "birth": [object]
    	"year": [integer]
    	"month": [integer]
    	"day": [integer]
    
    "death": [object]
    	[date format; see "birth"]
    
    "family": [array]
    	"father": [object]
    	"mother": [object]
    	"sibling": [object]
    	"spouse": [object]
    	"child": [object]
    	
    	/* Families are confined to the immediate, nuclear family of the given person. Where the missionary worked 
    	directly with other extended family members, they may be listed here, but this database does not intend to 
    	contain a running genealogical pedigree of the whole family. */
    	
    	"grandfather": [object]
    	"grandmother": [object]
    	"aunt": [object]
    	"uncle": [object]
    	"cousin": [object]
    	"brotherInLaw": [object]
    	"sisterInLaw": [object]
    	"motherInLaw": [object]
    	"fatherInLaw": [object]
    	"nephew": [object]
    	"niece": [object]
    
    "missions": [array]
    	"start": [date]
    	"end": [date]
    	"companions": [array] [name keys and values]
    	"locations": [array]
    	"sources": [array] //documents or artifacts specific to a given mission; other documents are listed in a separate `sources` object
    	"recipients": [array]
    	"roles": [array] //if the missionary participated in a specific role, these are noted here - possible values are:
    		"President", "Counselor", "Apostle", "Seventy", "Elder", "Priest", "Teacher", "Deacon"
    
    "sources": [array]
    	"author": [name]
    	"title": [string]
    	"location": [object]
    		"city": [string]
    		"state": [string]
    	"date": [object] [date]
    	"venues": [array]
    		/* Contains known archives or libraries where this source is available */
    	
    	

### Syntax Example

    {
    	"name": {
    		"last": "Smith",
    		"first": "Samuel",
    		"middle": "Harrison"
    	},
    	"birth": {
    		"year": 1808,
    		"month": 3,
    		"day": 13
    	},
    	"death": {
    		"year": 1844,
    		"month": 7,
    		"day": 30
    	},
    	"family": [
    		{ "father": { "last": "Smith", "first": "Joseph", "suffix": "Sr." } },
    		{ "mother": { "last": "Mack", "first": "Lucy", "married": "Smith" } },
    		{ "spouse": { "last": "Bailey", "first": "Mary", "married": "Smith" } },
    		{ "spouse": { "last": "Clark", "first": "Levira", "married": "Smith" } },
    		{ "child": { "last": "Smith", "first": "Lucy" } },
    		{ "child": { "last": "Smith", "first": "Susannah" } },
    		{ "child": { "last": "Smith", "first": "Mary" } },
    		{ "child": { "last": "Smith", "first": "Samuel", "middle": "Harrison" } },
    		{ "child": { "last": "Smith", "first": "Lovisa", "middle": "C." } },
    		{ "child": { "last": "Smith", "first": "Lucy", "middle": "J. C." } },
    		{ "child": { "last": "Smith", "first": "Levira", "middle": "Annette" } },
    	],
    	"missions": [
    		{
    			"start": { "year": 1830, "month": 6, "day": 30 },
    			"end": { "year": 1830, "month": 8 },
    			"locations": [
    				{ "city": "Bloomfield", "state": "New York" },
    				{ "city": "Livonia", "state": "New York" }
    			],
    			"recipients": [
    				{ "last": "Greene", "first": "John", "middle": "Portineus" },
    				{ "last": "Beaman", "first": "Esquire" }
    			],
    			"sources": [
    				{
    					"author": { "last": "Mack", "first": "Lucy", "married": "Smith" },
    					"title": "Biographical sketches of Joseph Smith the prophet, and his progenitors for many generations",
    					"location": { "city": "Liverpool", "country": "Great Britain" },
    					"publisher": "S. W. Richards",
    					"date": { "year": 1853 }
    				}
    			]
    		},
    		{
    			"start": { "year": 1831, "month": 1, "day": 2 },
    			"end": { "year": 1831, "month": 2, "day": 27 },
    			"locations": [
    				{ "state": "New York" },
    				{ "state": "Ohio" }
    			],
    			"companions": [ { "last": "Pratt", "first": "Orson", "id": "Pratt-Orson_1811-1881" } ],
    			"sources": [
    				{
    					"author": { "last": "Pratt", "first": "Orson", "id": "Pratt-Orson_1811-1881" },
    					"title": "History of Orson Pratt",
    					"newspaper": "Millennial Star",
    					"volume": 26,
    					"pages": 55,
    					"date": { "year": 1863 }
    				},
    				{
    					"author": { "last": "Mack", "first": "Lucy", "married": "Smith" },
    					"title": "Biographical sketches of Joseph Smith the prophet, and his progenitors for many generations",
    					"location": { "city": "Liverpool", "country": "Great Britain" },
    					"publisher": "S. W. Richards",
    					"date": { "year": 1853 }
    				}
    			]
    		},
    		{
    			"start": { "year": 1832, "month": 1, "day": 25 },
    			"end": { "year": 1832, "month": 12, "day": 22 },
    			"locations": [
    				{ "state": "Ohio" },
    				{ "state": "New York" },
    				{ "state": "Pennsylvania" },
    				{ "state": "Connecticut" },
    				{ "state": "Rhode Island" },
    				{ "state": "Massachusetts" },
    				{ "state": "Maine" }
    			],
    			"companions": [ { "last": "Hyde", "first": "Orson", "id": "Hyde-Orson_1805-1878" } ]
    		}
    	],
    	"sources": []
    }

