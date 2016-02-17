# Warehouse
Class library to manage inventory in a warehouse.
## Usercase
### Received ItemWithQuantity to Warehouse
Receiving item X with quantity Y into the warehouse increases the quantity of the item X to the original quantity plus Y. Additionally the warehouse will assign a location to the items.
```c++
Warehouse BigHouse;  // Create empty warehouse with no location plan.
QuantityOfMeasure qty(3, "each");
UniquePartId id("12345", "A");
ItemWithQuantity Item(id, qty);

BigHouse.receive(Item);

ASSERT_THAT(BigHouse.quantityOf(id), Eq(qty));
ASSERT_THAT(BigHouse.locationOf(id), Eq(BigHouse.location());
```


## Classes

### Location Manager
Class which manages the locations of a warehouse.

### Location
Class which holds unique items.
