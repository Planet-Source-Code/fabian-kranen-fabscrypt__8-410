<div align="center">

## FabsCrypt


</div>

### Description

Crypt and decrypt a string without the standard PHP functions.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Fabian Kranen](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/fabian-kranen.md)
**Level**          |Intermediate
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Security](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/security__8-14.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/fabian-kranen-fabscrypt__8-410/archive/master.zip)





### Source Code

```
<?
	// This script is (c)2001 F.Kranen http://www.odsync.net/
	// USE AT OWN RISK!
	// This is the standard crypt key. To make it real hard for others to decode, use a long string with weird characters.
	define ( "FABS_CRYPT_STRING", "F@B$CrYpT1$D@B0mB");
	//! FabsCrypt class
	class FabsCrypt
	{
		//! This function takes a string, encodes it and returns the crypted string
		function crypt ( $str )
		{
			$crypted			= "";
			$cryptString		= FABS_CRYPT_STRING;
			for ( $i=0; $i<strlen($str); $i++ )
			{
				$iC					= $i % strlen ( $cryptString );
				$crypted			.= chr ( myabs ( ord ( $str[$i] ) + ord ( $cryptString[$iC] ) ) );
			}
			return $crypted;
		}
		//! This function takes a string, decodes it and returns the decrypted string
		function decrypt ( $str )
		{
			$decrypted			= "";
			$cryptString		= FABS_CRYPT_STRING;
			for ( $i=0; $i<strlen($str); $i++ )
			{
				$iC					= $i % strlen ( $cryptString );
				$decrypted			.= chr ( myabs ( ord ( $str[$i] ) - ord ( $cryptString[$iC] ) ) );
			}
			return $decrypted;
		}
	}
	//! Function needed by crypt and decrypt
	function myabs ( $i )
	{
		if ( $i > 255 )
			return $i - 255;
		else
			return $i;
	}
	$fabscrypt		= new FabsCrypt ( );
	$original		= "This is a string wich will be encrypted and hopefully decrypted :P";
	$crypted		= $fabscrypt->crypt ( $original );
	$decrypted		= $fabscrypt->decrypt ( $crypted );
	echo "Original: $original<BR>Crypted: $crypted<BR>Decrypted: $decrypted"
?>
```

