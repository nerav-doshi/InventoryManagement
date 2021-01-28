# InventoryManagement

In this project a Decision Optimization (DO) is used to improve the inventory management of 
protective masks in a network of warehouses and agencies.

![Alt text](https://github.com/nerav-doshi/InventoryManagement/blob/main/images/MaskSupplyChain.gif "Title text")

# Input tables
To perform the DO experiment we use these input data tables:
* __Mask__ : each type of mask as an id, and a unit weight (used for computing transportation costs). 

   Note: For simplicity only one type of mask (FFP2) is considered here.
* __Period__ : The inventory is managed for a planning horizon corresponding to a set of periods
* __Agency__ : Masks are distributed by agencies. Agencies receive masks from warehouses.
* __AgencyRequest__ : for each period, an agency forecasts the demand for masks and defines the target inventory expected at the end of the period
* __AgencyInitialInventory__ : each agency defines its initial inventory at the start of the first period
* __Warehouse__ : Main inventory of masks is managed at some warehouses. A warehouse receives masks from factories and provides masks to agencies.
* __WarehouseTargetInventory__ : for each period, a warehouse specifies the target inventory expected at the end of the period 
* __WarehouseInitialInventory__ : each warehouse defines its initial inventory at the start of the first period
* __Factory__ : Masks are delivered to warehouses by factories
* __FactoryOffer__ : For each period, a factory defines its capacity of mask delivery and the unit price of these masks
* __FactoryWarehouseTransportCost__ : This table defines the unit cost to transport masks between each factory and each warehouse. In order to avoid too small deliveries, it also define a minimum cost of transportation.
* __PlanParameters__ : It collects useful global settings for planning, as the first and the last period


# DO experiment

The project contains a DO experiment named __InventoryOptimization__ with  3 scenarios. In this project, all scenarios share the same intent, that is a high level prescriptive rule specifying the main decisions we want to take.
```
Decide inventory of Masks at Warehouses and Agencies on each Periods and decide orders to Factories.
```
Each scenario is defined by a set of prescriptive rules - objectives and constraints - , some settings and a data schema 
defining data structure and also semantic logic derived from the rules.

Prescriptive rules prefixed by `(Implicit rule)` are rules that are automatically added as required by other rules. They cannot be removed or disabled directly, e.g. : 
```
(Implicit rule) No Masks lost in inventory at Warehouse
```
 

# Scenarios

## Base scenario - no cost
Defines general prescriptive rules aka objectives and constraints without taking into account costs

## With costs - no min transport
Created from `Base scenario - no cost`, this scenario adds some cost objective and constraints 

## With costs and min transport
Created from `With costs and min transport`, this scenario adds minimum cost for transportation, limiting small deliveries


# Solutions

Each scenario has already been solved. The solutions can be seen as a set of tables in the `Explore solution` section
 and with visual charts in `Vizualization` section.
 
# Do more
Create new scenarios from an existing one to capture additional constraints and objectives with the Modeling Assistant
or to play with the weight of each objective.

As an OR expert you can also export the Python Notebook associated to a scenario and extends it,  should you want to test some advanced constraints, objectives or solving strategies.
