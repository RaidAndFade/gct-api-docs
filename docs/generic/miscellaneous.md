Admittedly most of these are quite useless and were made for fun.

### Hash to MD5
__URL__
`GET /md5/hash/{$0}/...`

>Hash a given string `{$0}` with md5

>Hash multiple strings by adding more parameters to the url.

Example : 

Input : `/md5/hash/1/2/3`

Output : `{"1":"c4ca4238a0b923820dcc509a6f75849b","2":"c81e728d9d4c2f636f067f89cc14862c","3":"eccbc87e4b5ce2fe28308fd9f2a7baf3"}`

### Look for MD5
__URL__
`GET /md5/str/{$0}/...`

>Look for the original string of `{$0}` in the rainbow table.

>Search for multiple hashes by adding more parameters to the url.

>Returns either appropriate string, or `-1` if not found.d

Example :

Input : `/md5/str/c4ca4238a0b923820dcc509a6f75849b/c4ca4238a0b923820dcc509a6f75849d`

Output : `{"c4ca4238a0b923820dcc509a6f75849b":"1","c4ca4238a0b923820dcc509a6f75849d":-1}`

## Conversion API
__URL__ 
`GET /convert/{$0}/...`

>Convert the given string `{$0}` to it's Hex, Oct, Binary, and Decimal equivalents

>Also return letter frequency and list.

>Convert multiple strings by appending to url.

Example : 

Input : `/convert/hi`

Output : `{"hi":{"Letters":{"h":{"binary":"1101000","hexadecimal":"68","octadecimal":"150","decimal":"104","ascii":"h"},"i":{"binary":"1101001","hexadecimal":"69","octadecimal":"151","decimal":"105","ascii":"i"}},"lettercount":{"h":1,"i":1},"binary":"1101000 1101001 ","hexadecimal":"68 69 ","octadecimal":"150 151 ","decimal":"104 105 ","ascii":"h i "}}`

## Execute code
__URL__ `POST /exec/{lang?}`

__**Required Account Permissions:** EXECUTE__

>Execute a given code snippet in the language specified. 

POST ARGUMENTS (not required if `lang` supplied):

 Argument     | Description           
 --- | --- 
 `String` code         | The code that is being executed. 
 `String` lang         | The language that the given code is in. An error will be thrown if the language is unsupported. 
 `String` input        | A string that will be sent to STDIN


Output format: 

 Field | Description            
 --- | --- 
 `Int` status | The return status of the execution daemon.
 `String` res  | The text result of the code snippet.
 `Int` comp | Duration of time taken to run code in milliseconds.

## Ip Information
__URL__ `GET /ip/{ip}`

__**Required Account Permissions:** IP__

>Fetch information about any given ip.

Output Format:

Output will either be type 1 or type 2.

Type 1 (Range is special):

 Field | Description            
 --- | --- 
 `String` resp | String that is sent when something goes wrong or when data can't be provided
 `String` range | The ip range related to the response

Type 2 (Range is not special):

 Field | Description            
 --- | --- 
 `String` network | The ip range related to the response
 `String` asn | The ASN that provides or owns the IP address
 `Array<String>` | An array of flags related to the IP
 `Location` location | The approximate location of the IP

`Location` object:

 Field | Description            
--- | --- 
 `String` latitude | Approximate latitude
 `String` longitude | Approximate longitude
 `String` postal_code | Approximate postal code
 `Object` continent | Continent of IP {`code`:`String code`,`name`:`String name`}
 `Object` country | Country of IP {`code`:`String code`,`name`:`String name`}
 `Object` region | Region of IP {`code`:`String code`,`name`:`String name`}
 `Object` subregion | Either empty object or {`code`:`String code`,`name`:`String name`}
 `String` city | Approximate city of IP
 `String` time_zone | Time zone of IP

## Lookandsay
__URL__ `GET /lookandsay/{n}`

>Returns a list of all `lookandsay` elements up to the `n`th element... 

> where `n` <= 8 when not authenticated

> or 12 if authenticated

> or 24 if your account is flagged UPGRADED.

Example : 

Input : `/lookandsay/4`

Output : `["1","11","21","1211"]`


## Fibonacci
__URL__ `GET /fibonacci/{n}`

>Returns a list of all `fibonacci` elements up to the `n`th element...

> where `n` <= 250 when not authenticated

> or 500 if authenticated

> or 2500 if your account is flagged UPGRADED.

Example : 

Input : `/fibonacci/4`

Output : `[0,1,1,2]`
