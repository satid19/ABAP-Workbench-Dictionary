# Exercise 1 - Domain And Types

# Domain

## Definition
A domain defines a value range. A domain is assigned to a data element. All table fields or structure components that use this data element have the value range defined by the domain. The relationship between the field or component and the domain is defined by the data element of the field or component.

SAP Help Link for  [SAP ABAP Domain](https://help.sap.com/saphelp_SCM700_ehp02/helpdata/en/cf/21ede5446011d189700000e8322d00/content.htm?no_cache=true)

## Creating Domains
### Prerequisites
Before creating a new domain, check whether a domain that defines the same value range already exists. In this case you must use the existing domain if possible.
In very few cases we have to create domain.

### Procedure
1. Open Transaction SE11. 
2. Give Name And Press Enter 
![Domain1](https://github.com/satid19/ABAP-Workbench-Dictionary/blob/main/Exercises/EX1/Domain1.PNG)

3. Give Discription and Select a DATA type 
![Doamin2](https://github.com/satid19/ABAP-Workbench-Dictionary/blob/main/Exercises/EX1/Domain_2.PNG)

4.Give Proper length and Output length
![Domain3](https://github.com/satid19/ABAP-Workbench-Dictionary/blob/main/Exercises/EX1/Doamin_3.PNG)

5. Give package name and TR Created Earlier
![Doamin4](https://github.com/satid19/ABAP-Workbench-Dictionary/blob/main/Exercises/EX1/Doamin_4.PNG)

6. If you want any specific Vlaue Range please define in Value range Tab

# Types
## Definition
User-defined data types can be stored for all programs in the ABAP Dictionary. This central definition of types that are used more than once in the ABAP Dictionary allows them to be changed centrally. The active ABAP Dictionary ensures that such changes are made at all the relevant locations. 

SAP Help Link for [Dictinory Types](https://help.sap.com/saphelp_SCM700_ehp02/helpdata/en/cf/21ede5446011d189700000e8322d00/frameset.htm)

## DATA Element

1. SE11-> Data Type 
2. Give Proper name like Z_NAME_1234 And select Data Element in next screen
![DataE1](https://github.com/satid19/ABAP-Workbench-Dictionary/blob/main/Exercises/EX1/Data_E_1.PNG)

2. Give Doamin Name Earlier created and selected package
![DataE2](https://github.com/satid19/ABAP-Workbench-Dictionary/blob/main/Exercises/EX1/Data_E_2.PNG)

3. Give Proper Field Lavels  
![DataE3](https://github.com/satid19/ABAP-Workbench-Dictionary/blob/main/Exercises/EX1/Data_E_3.PNG)
