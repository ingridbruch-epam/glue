---
id: Glue Dictionary
title: glue Model Tables
---
| Create Table if NOT EXISTS| Primary Key ('id')|.|ENGINE = InnoDB|.|
|---|---|---|---|---|
|Table Name | Column Name| Data Type|PK Primary Key, NN-Not Null, Null|.|
||
| Address|`id` |BIGINT(12)| PK, NN|.|
| Address|`Primary`| TINYINT |NULL|.|
| Address|`po_box`| VARCHAR(45)| NULL|.|
| Address|`Addressline 1` |VARCHAR(45)| NULL|.|
| Address|`Addressline 2` |VARCHAR(45)| NULL|.|
| Address|`Street_Number`| INT| NULL|.|
| Address|`zip_code`| VARCHAR(45)| NULL|.|
| Address|`City` |BIGINT(12) |NULL|.|
| Address|`Country`| BIGINT(12)| NULL|.|
| Address|`Region` |BIGINT(12)| NULL|.|
| Address|`Latitude`| DECIMAL| NULL|.|
| Address|`Longitude`| DECIMAL |NULL|.|
| Address|`Person` |BIGINT(12)| NULL|.|
| Address|`Address_Type`| BIGINT(12)| NULL|.|
|For Table: ADDRESS:|
|CONSTRAINT|FOREIGN KEY|REFERENCES |ON DELETE|ON UPDATE|
|`Person_PII`|('Person')|`Person_PII` (`id`)|NO ACTION| NO ACTION|
|`Address_type`|('Address_type`)| `Address_Type` (`Id`)|NO ACTION| NO ACTION|
|`Country`|(`Country`)|`Country` (`id`)|NO ACTION| NO ACTION|
|`City`|(`City`)|`City` (`id`)|NO ACTION| NO ACTION|
|`Region`|(`Region`)|`Region` (`id`)|NO ACTION| NO ACTION|
|For Table: ADDRESS:|
|CREATE INDEX|ON|ASC|VISABLE|.|
|`Person_idx`|`Address`|(`Person` ASC)|VISIBLE;|.|
|`Address_type_idx`|`Address`|(`Address_Type` ASC)|VISIBLE;|.|
|`Country_idx`|`Address` |(`Country` ASC)|VISIBLE;|.|
|`City_idx`|`Address`|(`City` ASC)|VISIBLE;|.|
|`Region_idx`|`Address`|(`Region` ASC)|VISIBLE;|.|
||
|Table Name | Column Name| Data Type|PK Primary Key, NN-Not Null, Null|.|
||
|Address_Type	|`Id` |	BIGINT(12)	|PK, NN|.|
|Address_Type|`Name` |	VARCHAR(45)|	Null|.|
||
|Table Name | Column Name| Data Type|PK Primary Key, NN-Not Null, Null|.|
||
|`Asset_Classification_Node`|`id` |BIGINT(12)|PK, NN|.|
|`Asset_Classification_Node`|`Node_Name`| VARCHAR(45) |NULL|.|
|`Asset_Classification_Node`|`Regime` |BIGINT(12)| NULL|.|
|`Asset_Classification_Node`|`Asset_Classification_Regime_Structurecol`| BIGINT(12)| NULL|.|
|`Asset_Classification_Node`|`Benchmark`| BIGINT(12)| NULL|.|
|For Table: `Asset_Classification_Node`:|
|CONSTRAINT|FOREIGN KEY|REFERENCES |ON DELETE|ON UPDATE|
|`Regime`|(`Regime`)|`Asset_Classification_Regime` (`id`)|NO ACTION| NO ACTION|
|`NodeBenchmark`|(`Benchmark`)|`Benchmark` (`id`)|NO ACTION| NO ACTION|
|For Table: `Asset_Classification_Node`:|
|CREATE INDEX|ON|ASC|VISABLE|.|
|`Regime_idx`|`Asset_Classification_Node`|(`Regime` ASC)|VISIBLE;|.|
|`Benchmark_idx`|`Asset_Classification_Node`|(`Benchmark` ASC)| VISIBLE;|.|
||
|Table Name | Column Name| Data Type|PK Primary Key, NN-Not Null, Null|.|
||
|`Asset_Classification_Regime`|`id` |BIGINT(12)|PK, NN|.|
|`Asset_Classification_Regime`|`Name`| VARCHAR(45)| NULL|.|
|`Asset_Classification_Regime`|`Owner`| BIGINT(12)| NULL|.|
|`Asset_Classification_Regime`|`Depth`|INT| NULL|.|
||
|Table Name | Column Name| Data Type|PK Primary Key, NN-Not Null, Null|.|
||
|`Asset_Classification_Structure`|`id`| BIGINT(12)|PK, NN|.|
|`Asset_Classification_Structure`|`Parent`| BIGINT(12)| NULL|.|
|`Asset_Classification_Structure` |`Child` |BIGINT(12)| NULL|.|
|`Asset_Classification_Structure` |`Level`| INT| NULL|.|
|For Table:`Asset_Classification_Structure`|
|CONSTRAINT|FOREIGN KEY|REFERENCES |ON DELETE|ON UPDATE|
|`ACParent`|(`Parent`)|`Asset_Classification_Node` (`id`)|NO ACTION| NO ACTION|
|`ACChild`|(`Child`)|`Asset_Classification_Node` (`id`)|NO ACTION| NO ACTION|
|For Table:`Asset_Classification_Structure`|
|CREATE INDEX|ON|ASC|VISABLE|.|
|`Node_idx`|`Asset_Classification_Structure`|(`Parent` ASC)|VISIBLE;|.|
|`Child_idx`|`Asset_Classification_Structure`|(`Child` ASC)|VISIBLE;|.|
||
|Table Name | Column Name| Data Type|PK Primary Key, NN-Not Null, Null|.|
||
|`BP-Relationship_Type`|`id`| BIGINT(12)|PK, NN|.|
|`BP-Relationship_Type`|`Name`|BIGINT(12)|NULL|.|
||
|Table Name | Column Name| Data Type|PK Primary Key, NN-Not Null, Null|.|
||
|`Bank_Employee`|`id`| BIGINT(12)|PK, NN|.|
|`Bank_Employee`|`Job_Function`| BIGINT(12)| NULL|.|
|`Bank_Employee`|`Rank` |BIGINT(12)| NULL|.|
|`Bank_Employee`|`Person`| BIGINT(12)| NULL|.|
|For Table:`Bank_Employee`|
|CONSTRAINT|FOREIGN KEY|REFERENCES |ON DELETE|ON UPDATE|
|`BEPerson`|(`Person`)|`Person` (`id`)|NO ACTION| NO ACTION|
|For Table:`Bank_Employee`|
|CREATE INDEX|ON|ASC|VISABLE|.|
|`Person_idx`|`Bank_Employee`|(`Person` ASC)|VISIBLE;|.|
||
|Table Name | Column Name| Data Type|PK Primary Key, NN-Not Null, Null|.|
||
|`Benchmark`|`id` |BIGINT(12) |PK,NN|.|
|`Benchmark`|`Name` |VARCHAR(45)| NULL|.|
|`Benchmark`| `Is_Composit`| TINYINT |NULL|.|
||
|Table Name | Column Name| Data Type|PK Primary Key, NN-Not Null, Null|.|
|`Benchmark_Constituent`|`id`| BIGINT(12)| NPK, NN|.|
|`Benchmark_Constituent`| `Instrument`| BIGINT(12)| NULL|.|
|`Benchmark_Constituent`| `Weight`| DECIMAL |NULL|.|
|`Benchmark_Constituent`|`Benchmark`| BIGINT(12)| NULL|.|
|For Table:`Benchmark_Constituent`|
|CONSTRAINT|FOREIGN KEY|REFERENCES |ON DELETE|ON UPDATE|
|`ConstituentBenchmark`|(`Benchmark`)|`Benchmark` (`id`)|NO ACTION| NO ACTION|
|For Table:`Benchmark_Constituent`|
|CREATE INDEX|ON|ASC|VISABLE|.|
|`Benchmark_idx`|`Benchmark_Constituent`|(`Benchmark` ASC)| VISIBLE;|.|
