
<table border="0" width="100%">
  <tr>
    <td>
    <img src="https://github.com/dragos-constantin-stoica/ifact/blob/offline/Logo.png" alt="Logo"></img>
    </td>
    <td>
    <p align="right"><small>"Invoicing made simple"</small></p>
    <p align="right"><em>for simple people!</em></p>
    </td>
  </tr>
</table>

This repository contains [PouchDB](https://pouchdb.com/) based code and is available for offline demo [iFact offline](https://dragos-constantin-stoica.github.io/ifact-pouchdb/). All changes that you made will be stored in local browser storage.

You do not need an user name and a password to access the application.


Please find blog article here [Webix blog](https://blog.webix.com/ifact-webix-based-invoicing-application/) including screenshots.

# iFact

**iFact** is an invoicing web application that I wrote in some spare moments, between projects. This is a personal tool to help me create my invoices and with minimal invoice management, like: marking them payed, reporting overdued invoiced, see anual revenue, export to a spreadsheet via [SheetJS](http://sheetjs.com/).  

This is a **S**ingle **P**age **A**pplication web applicaion written with [Webix](https://webix.com/) framework, running  directly from your browser. 
The invoices are generated as PDF files via [PDFmake](http://pdfmake.org/) framework using [Handlebar](http://handlebarsjs.com/) framework for templating. All data is stored in JSON format.

## Install and Setup

Pre-requisites:

* Web browser

The application should be availble at: https://dragos-constantin-stoica.github.io/ifact-pouchdb/ 

Congratulations!  

The home page is the from where you fill in your profile. You should provide identification information about your company. This information includes: company name, address, identification nubmers and fiscal data, also you can add several bank accounts. Normally you are supposed to fill in this page only once. Also fill in the series and the starting serial number for your invoices.

On the left side you have a drawer menu that will allow you to define the other entityes: customers, contracts, invoices and payments.

A **customer** is an entity similiar to yours and will be the your business partner, the one you will invoice. The input data is similar to yours, the only diference is that there are multiple customers and you are the only supplier. Customers are created once and they can not be deleted.

Once you defined a customer then you may create **contracts**. The contract is a legal basis on which you will perform business with your customers. Please keep the copy of the contract in a safe place. Contracts have an expiry date. Once they are created they can not be deleted.

The next step is to deliver the services or goods you signed the contrat for and start invoicing!

## Create an invoice

The next important step is to emit invoices for your services according to the contract. The application is based on **PDFMake** to produce the actual electronic inovice.

There are two templates to choose form: EN and RO. They correspond to English/European and Romanian invoice templates. The templates contain a couple of fields that can be filled in by the user. You must provide a minimum amount of information:

* the bank account that you want the invoice to be payed to
* the customer
* VAT value as a percent
* the date of issue
* the description of the services provided
* a formula to compute the value or the actual value of the invoice line

Pleas use _Preview_ button to inspect the inovice. You will see a draft PDF in the right panel, please note that the invoice number is the last valid number that is in the database. If you are happy with the result, then press _Create Invoice_ button, this time you will see the new invoice on the right panel with a diferent invoice number - a real, valid, invoice number.

## Reporting

In order to close the cycle you need to keep track of the payed invoices. The **Payments** will allow you to visualize the state of your invoices. Invoices are _New_ once you created them. They will become _Due_ if the current date is greater or equal to invoice due date and the invoice was not entirely payed. Once the invoice is entirely payed it will become _Payed_.

**Payments** allows you to keep trak of your invoices and to figure out your future cash flow. You may edit the invoice, please use this feature being fully aware of what you are doing. Once the invoice enters the legal process, I do not recommed to use edit functionality. There is a view button allowing you to get another copy of the invoice.

The **Dashboard** is the place to look from time to time in order to understand the overall situation of your business. Basicaly you have a summary of the Year to Date invoiced, payed and due sums. You have two graphs showing the Year to Date income (invoiced vs. payed) and the other graph, showing the comparative Monthly invoiced for each year of activity.

## Communication with external systems

**iFact** has data export and import facilities. On the **Supplier** view, right side you will find a couple of buttons allowing you to work outside the box. You can export data, like a financial statement: invoiced vs. payed per invoice, in Excel. You can export the entire database - only data, without the application, in JSON format - like an old database dump, and import data in JSON format (see file iFact_DEMO.json).

> Actually I do recommend to start with an empty database and import the iFact_DEMO.json file in order to play with the application.

You can synchronize the application and data with another CouchDB compatible system, like Cloudant or CouchBase or PouchDB Server. I tested succesfully the replication with Cloudant and CoucDB 2.0.

_Have fun and enjoy life!_
