Assuming ```src``` contains the following string:

```
{
  "str": "hello!",
  "num": 123,
  "innerObj": { "field": "test" },
  "array": [ { "index": 0 }, { "index": 1 } ],
}
```

...you can access individual fields by using:

```c#
// Initialize with the root object.
JsonObject rootObj = new JsonObject(src);

// Get field values.
string str = rootObj["str"].AsString();
int num = rootObj["num"].AsInt();

// Get an inner object and its values.
JsonObject innerObj = rootObj["innerObj"];
string objField = innerObj["field"].AsString();

// Get array elements by index...
JsonObject array0 = rootObj["array"][0];
JsonObject array1 = rootObj["array"][1];
JsonObject array2 = rootObj["array"][2]; // null is returned on out-of-bounds

int index0 = array0["index"].AsInt();
int index1 = array1["index"].AsInt();

// ...or by iterating.
JsonObject array0 = rootObj["array"][0];
JsonObject array1 = array0.Next();
JsonObject array2 = array1.Next(); // null is returned after end of array

int index0 = array0["index"].AsInt();
int index1 = array1["index"].AsInt();

```
