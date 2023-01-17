## Introduction

In this exercise you will create two database tables to store the **travel** and **booking** data. You'll also create a little helper class to populate some sample data into both tables.

The data model in this workshop consists of two transactional tables (**travel** and **booking**) as well as some master data that we will re-use from the already existing demo content (**Agency**, **Customer** and **Flight**), as well as a few more.

![Data Model](https://github.com/Krishna-Alani/S4HANATraining-RAP/blob/main/exercises/ex1/images/datamodel01.png)

## Exercise 1.1 - Create the Travel database table
A Travel entity defines general travel data, such as the agency ID or customer ID, the overall status of the travel and the price of travel.   
1. Right click on your package **`ZRAP_TRAVEL_####`** (where `####` is your group ID), choose **_New > Other ABAP Repository Object_** from the context menu.   

   ![Create Database Table](https://github.com/Krishna-Alani/S4HANATraining-RAP/blob/main/exercises/ex1/images/traveltable01.png)

2. Enter `database` in the search field, choose **Database table** in the list and then choose **Next**.  

   ![Create Database Table](https://github.com/Krishna-Alani/S4HANATraining-RAP/blob/main/exercises/ex1/images/traveltable02.png)

3. Provide **`ZRAP_ATRAV_####`** (where `####` is your group ID) as name and a description (e.g. *Travel data*) in the appearing dialog and choose **Next**.  

   ![Create Database Table](https://github.com/Krishna-Alani/S4HANATraining-RAP/blob/main/exercises/ex1/images/traveltable03.png)

4. Assign a transport request and choose **Finish**. The table is created and a new editor with the defaulted content is opened. The table-specific technical settings are specified using annotations at the top.  

   ![Create Database Table](https://github.com/Krishna-Alani/S4HANATraining-RAP/blob/main/exercises/ex1/images/traveltable04.png)  

5. Replace the source code with the code snippet provided below and replace all occurrences of `####` with your group ID. You can make use of the Replace All feature (**Ctrl+F**) in ADT for this purpose. 

    <pre>
    @EndUserText.label : 'Travel data'
    @AbapCatalog.enhancementCategory : #NOT_EXTENSIBLE
    @AbapCatalog.tableCategory : #TRANSPARENT
    @AbapCatalog.deliveryClass : #C
    @AbapCatalog.dataMaintenance : #RESTRICTED
    define table zrap_atrav_#### {
      key client            : mandt not null;
      key travel_uuid       : sysuuid_x16 not null;
      travel_id             : /dmo/travel_id;
      agency_id             : /dmo/agency_id;
      customer_id           : /dmo/customer_id;
      begin_date            : /dmo/begin_date;
      end_date              : /dmo/end_date;
      @Semantics.amount.currencyCode : 'zrap_atrav_####.currency_code'
      booking_fee           : /dmo/booking_fee;
      @Semantics.amount.currencyCode : 'zrap_atrav_####.currency_code'
      total_price           : /dmo/total_price;
      currency_code         : /dmo/currency_code;
      description           : /dmo/description;
      overall_status        : /dmo/overall_status;
      created_by            : syuname;
      created_at            : timestampl;
      last_changed_by       : syuname;
      last_changed_at       : timestampl;
      local_last_changed_at : timestampl;
    }
    </pre>

   ![Create Database Table](images/traveltable05.png)  

    **Short explanation:**  
    - Some data elements from the ABAP Flight Reference Scenario (namespace `/DMO/`) are used.  
    - The table key consists of the `CLIENT` field and the `TRAVEL_UUID` field which is a technical key (16 Byte UUID).   
    - A human-readable travel identifier: `TRAVEL_ID`  
    - The field CURRENCY_CODE is specified as currency key for the amount fields `BOOKING_FEE` and `TOTAL_PRICE` using the semantic annotation `@Semantics.amount.currencyCode`   
    - Some standard administrative fields are defined: `CREATED_BY`, `CREATED_AT`, `LAST_CHANGED_BY`, `LAST_CHANGED_AT` and `LOCAL_LAST_CHANGED_AT`.  
  
6. Save ![save icon](images/adt_save.png) and activate ![activate icon](images/adt_activate.png) the changes.  

## Exercise 1.2 - Create the Booking database table
A Booking entity comprises general flight and booking data, the customer ID for whom the flight is booked as well as the travel ID to which the booking belongs to – and some admin fields.  
  
1. Right click on the **Database Tables** folder, choose **New Database Table** from the context menu.  

   ![Create Database Table](https://github.com/Krishna-Alani/S4HANATraining-RAP/blob/main/exercises/ex1/images/bookingtable01.png)

2. Maintain **`ZRAP_ABOOK_####`** (where `####` is your group ID) as name and a description (e.g. **_Booking data_**) in the appearing dialog and choose **Next**. 

   ![Create Database Table](https://github.com/Krishna-Alani/S4HANATraining-RAP/blob/main/exercises/ex1/images/bookingtable02.png)

3. Assign a transport request and choose **Finish**. The table is created and a new editor with the defaulted content is opened.

   ![Create Database Table](https://github.com/Krishna-Alani/S4HANATraining-RAP/blob/main/exercises/ex1/images/bookingtable03.png)

4. Replace the default source code with the code snippet provided below and replace all occurrences of  `####` with your group ID. You can make use of the Replace All feature (shortcut **Ctrl+F**) in ADT for this purpose.  

    <pre> 
    @EndUserText.label : 'Booking data'
    @AbapCatalog.enhancementCategory : #NOT_EXTENSIBLE
    @AbapCatalog.tableCategory : #TRANSPARENT
    @AbapCatalog.deliveryClass : #C
    @AbapCatalog.dataMaintenance : #RESTRICTED
    define table zrap_abook_#### {
      key client            : mandt not null;
      key booking_uuid      : sysuuid_x16 not null;
      travel_uuid           : sysuuid_x16 not null;
      booking_id            : /dmo/booking_id;
      booking_date          : /dmo/booking_date;
      customer_id           : /dmo/customer_id;
      carrier_id            : /dmo/carrier_id;
      connection_id         : /dmo/connection_id;
      flight_date           : /dmo/flight_date;
      @Semantics.amount.currencyCode : 'zrap_abook_####.currency_code'
      flight_price          : /dmo/flight_price;
      currency_code         : /dmo/currency_code;
      created_by            : syuname;
      last_changed_by       : syuname;
      local_last_changed_at : timestampl;
    }
    </pre>   

    ![Create Database Table](images/bookingtable04.png)
  
    **Short explanation:**
    - The table key consists of the `CLIENT` field and the `BOOKING_UUID` field which is a technical key (16 Byte UUID).   
    - A human-readable travel identifier: `BOOKING_ID`  
    - Some standard administrative fields are defined: `CREATED_BY`, `LAST_CHANGED_BY`, and `LOCAL_LAST_CHANGED_AT`.  
  
5. Save ![save icon](images/adt_save.png) and activate ![activate icon](images/adt_activate.png) the changes.  
  
