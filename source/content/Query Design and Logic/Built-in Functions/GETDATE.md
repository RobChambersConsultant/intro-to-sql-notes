`GETDATE` gets the current `DATETIME` (of the system).

# Common Use Cases
This is very useful for labelling *when* something has happened - i.e. when a set of data has been processed, add a `processed_on` column and use `GETDATE` to assign the current date and time.

It is also often used alongside the [[DATEDIFF]] function - e.g. to return values or calculate statistics 'in the last week' or the 'last month'.
