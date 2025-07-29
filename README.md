# FM_CustomFunctions

Some Custom Functions for FileMaker

## JSON

## SQL

### `JQL2JSON( query, fieldList, sqlParams )`

ExecuteSQL wrapper that returns a JSON array of elements instead of return delimited, comma seperated list.

### `SQLField( FMName )`

Gets the name of a field and pre-quotes it for ease of use in ExecuteSQL queries. Makes changing field names much less damaging if you look up the field name before the query string is constructed. Consider the scenario that you write a script to Exectute SQL with a hard-coded field name `Contacts::Name` in the query string (`"SELECT Contacts.Name FROM Contacts"`), but then later decide that the field name should be called `Contacts::FirstName`. If you use the hard coded option, then changing the field name breaks your script. If you instead use `"SELECT " & SQLField( Contacts::Name ) & " FROM Contacts"...`, Not only can you autocomplete the field name in the script editor, but you can also change the name at will without breaking the query string, since FileMaker will store the reference to the field, instead of the name in your script.

I have experienced issues with ExecuteSQL when the table name had underscores without putting quotes around the table and field names. This was also employed to solve that.

### `SQLTable( FMName )`

Same as the above but for the Table Name of the field you pass into it.

### `SQLFieldName( FMName )`

Same as `SQLField` Except it drops the Table qualifier, and just gives you the quoted fieldname.
