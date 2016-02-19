# Warehouse
Class library to manage inventory in a warehouse.
## Usercase
### Warehouse can be made with no Location Plan
A new warehouse can be made with no location plan will have a default inventory location and staging location.
```c++
Warehouse warehouse_;

ASSERT_TRUE(warehouse_.hasLocation("Inventory"));
ASSERT_TRUE(warehouse_.hasLocation("Staging"));
```

### Warehouse can be made with a Location Plan
A new warehouse provided with a location plan will have the locations provided. It will not have the default Inventory or Staging locations.
```c++
Location locationPlan_;
    locationPlan_.add("A");
    locationPlan_.add("B");

Warehouse warehouse_(locationPlan_);

ASSERT_TRUE(warehouse_.hasLocation("A"));
ASSERT_TRUE(warehouse_.hasLocation("B"));
ASSERT_FALSE(warehouse_.hasLocation("Inventory"));
ASSERT_FALSE(warehouse_.hasLocation("Staging"));
```

### Warehouse has no Locations and receives Item with Quantity
Receiving item X with quantity Y into the warehouse increases the quantity of the item X to the original quantity plus Y. The location of the received item will be in the warehouse's staging area.
```c++
Warehouse warehouse_;

string itemId("PartABC");
Quantity itemQuantity_(3, "each");
ItemWithQuantity itemWithQuantity_(itemId_, itemQuantity_);

warehouse_.receive(itemWithQuantity_);

ASSERT_THAT(warehouse_.locationOf(itemId_), Eq(warehouse_.location("Staging")));
ASSERT_ThAT(warehouse_.quantityOf(itemId_), Eq(itemQuantity_);
```


### Warehouse has Locations and receives Item with Quantity



## Classes

### Location Manager
Class which manages the locations of a warehouse.

### Location
Class which holds unique items.
