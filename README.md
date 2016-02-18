# Warehouse
Class library to manage inventory in a warehouse.
## Usercase
### Received ItemWithQuantity to Warehouse
Receiving item X with quantity Y into the warehouse increases the quantity of the item X to the original quantity plus Y. Additionally the warehouse will assign a location to the items.
```c++
Warehouse _house;  // Create empty warehouse with no location map.
QuantityOfMeasure qty(3, "each");
UniquePartId id("12345", "A");
ItemWithQuantity Item(id, qty);

_house.receive(Item);

ASSERT_THAT(_house.quantityOf(id), Eq(qty));
ASSERT_THAT(_house.locationOf(id), IsWithin(_house.location());
```

### Warehouse has LocationsMap and receives ItemWithQuantity
```c++
LocationMap _map;
  _map.addLocation(new Location("Location A"));
  
Warehouse _house(_map); // Create empty warehouse with location map.
QuantityOfMeasure qty(3, "each");
UniquePartId id("12345", "A");
ItemWithQuantity Item(id, qty);

_house.receive(Item).toLocation(_house.location("Location A"));
ASSERT_THAT(_house.locationOf(id), Eq(_house.location("Location A"));

```


## Classes

### Location Manager
Class which manages the locations of a warehouse.

### Location
Class which holds unique items.
