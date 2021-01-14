---
title: "Lightning Record Table"
permalink: /docs/lightning-record-table/
excerpt: "How to make a lightning record table"
toc: true
---
## Requirements

Given a record, the client would like to display all child records of a specific object type in a table with the following requirments: <br/>

1. The table component should work inside of a flow for additional functionality to be developed later on
2. The fields displayed in the table should be editable, with edits saved to the database
3. The table should allow for users to delete and add records in the database

<figure>
  <img src="{{ '/assets/images/Lightning-Component.gif' | relative_url }}" alt="Final Component Design">
  <figcaption>The final component design</figcaption>
</figure>

## Declarative Configuration
There are two declarative configurations required in this project:

First, we will need to create an object model that matches the requirements of the client. In this case I created two custom objects that are related via a master-detail lookup, however, you can just as easily tailor this project to existing standard objects like Account-Contact, Opportunity-Quote, etc. 

The second configuration will be the creation of the flow in which this lightning component will sit. Not only will the flow act as the container for the lightning component but it will also provide the required functionality to update records based on user input.

### Object Model
As discussed above, this component will work for any parent-child object model, Account and Contact for example. For this example, however, I created two custom objects, `Parent_Object__c` and `Child_Object__c`, with a Master-Detail lookup field on `Child_Object__c` looking up to `Parent_Object__c`.

`Child_Object__c` has three fields, one is the previously discussed Master-Detail, I have also include two additional fields simply for testing purposes, `Amount__c` and `Location__c`.

<figure>
  <img src="{{ '/assets/images/object-model.png' | relative_url }}" alt="Object Model">
  <figcaption>The example object model used for this project</figcaption>
</figure>

### Flow
The flow that houses our lightning component it extremely bare bones in functionality. Outside of the update records functionality, there isn't much to it but the client wants the component to function within a screen flow as they will have admins adding additional functionality to the flow later on. 


Node Name | Function |
---------|----------|
 Get Child Objects | Given the record ID of a `Parent_Object__c` record, retrieve all related `Child_Object__c` records|
 Display Child Records | Screen Component that display our custom lightning component |
 Set Collection Variable | Takes the edited child objects from the component and puts them into a flow collection variable which will then be iterated over in the next node |
 Loop Through Table Records| Iterates over the collection variable of edited child objects |
 Was the Record Deleted? | Checks if the record was deleted before updating, if it was deleted then don't bother updating the record |
 Update Record | Update the record if a change occurred |
 Finished | Final screen letting the user know their edits have been saved |

<figure>
  <img src="{{ '/assets/images/flow-design.png' | relative_url }}" alt="Flow Design">
  <figcaption>The screenflow that houses our lightning component</figcaption>
</figure>

## Code
We will use one lightning component and an apex controller

### Lightning Web Component
The LWC contains an html file, javascript controller, and a metadata file
#### HTML

#### JavaScript Controller
```
System.debug("This is apex code");
List<Account> newList = new List<Account>();

insert newList;
javaaaaaaaaaaaaaaa
```
Connected Callback
```
System.debug("This is apex code");
List<Account> newList = new List<Account>();

insert newList;
javaaaaaaaaaaaaaaa
```


#### Metadata File


### Apex Controller

```
System.debug("This is apex code");
List<Account> newList = new List<Account>();

insert newList;
javaaaaaaaaaaaaaaa
```