# sql notes

https://docs.oracle.com/cd/B19306_01/appdev.102/b14261/tuning.htm

The values at the time of compilation of the PLSQL_CCFLAGS, PLSQL_CODE_TYPE, PLSQL_DEBUG, PLSQL_OPTIMIZE_LEVEL, PLSQL_WARNINGS, and NLS_LENGTH_SEMANTICS initialization parameters are stored with the unit's metadata. You can view information about the settings of these parameters with the ALL_PLSQL_OBJECT_SETTINGS view.

In rare cases, if the overhead of the optimizer makes compilation of very large applications take too long, you might lower the optimization by setting the initialization parameter PLSQL_OPTIMIZE_LEVEL=1 instead of its default value 2. Setting PLSQL_OPTIMIZE_LEVEL=0 prevents the code from being rearranged at all. For information on the PLSQL_OPTIMIZE_LEVEL initialization parameter,

When to Tune PL/SQL Code

rograms that do a lot of mathematical calculations
Functions that are called from PL/SQL queries, where the functions might be executed millions of times. You will want to look at all performance features to make the function as efficient as possible, and perhaps a function-based index to precompute the results for each row and save on query time.
Programs that spend a lot of time processing INSERT, UPDATE, or DELETE statements, or looping through query results. You will want to investigate the FORALL statement for issuing DML, and the BULK COLLECT INTO and RETURNING BULK COLLECT INTO clauses for queries.
Older code that does not take advantage of recent PL/SQL language features. With the many performance improvements in Oracle Database 10g, any code from earlier releases is a candidate for tuning.
Any program that spends a lot of time doing PL/SQL processing, as opposed to issuing DDL statements like CREATE TABLE that are just passed directly to SQL. You will want to investigate native compilation. Because many built-in database features use PL/SQL, you can apply this tuning feature to an entire database to improve performance in many areas, not just your own code.
