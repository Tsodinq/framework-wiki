# Datastores

Datastores are the storage backends for Cosmic servers. Datastores exist on the Framework API, and are used to store and retrieve data for use in your game.

API rate limits are enforced on datastores. If you exceed the rate limit, your requests will be throttled.

---

## Rate Limits

- `Datastores.setAsync` is limited to 150 requests per minute. This limit is shared across all datastores as requests are tied to the origin of the request.
- `Datastores.getAsync` is limited to 150 requests per minute. This limit is shared across all datastores as requests are tied to the origin of the request.

---

To get started, create a datastore for your game on the Framework website:

- Go to the [Invent](https://framework.soodam.rocks/invent) page
- Find the game you'd like to create a datastore for (and has a Cosmic server configured for)
- Click on the triple-dots and click **Edit**
- Go to the **Datastores** tab
- Click **Create a new datastore** and fill out the necessary fields
- Once your datastore is created, copy it's ID (shown below)

![image|269x85, 100%](https://discourse.soodam.rocks/uploads/default/original/1X/d3f895e9a5da5ec4c115b9539ccf5ce09196c378.png)

---

Once you've retrieved your datastores ID, we can get started with the code. Create a new script in your Cosmic project. We'll name ours `data.ts`.

## `Datastores.setAsync`

### Definition

```ts
setAsync: (storeId: string, key: string, value: object) => Promise<boolean>;
```

The `setAsync` function allows you to store a value in a specified datastore identified by its `storeId`. The `key` argument is used to uniquely identify the value within the datastore, and the `value` argument is the data you want to store. The function returns a promise that resolves to a boolean indicating whether the value was successfully set in the datastore. If an entry does not exist with the specified `key`, one will be created.

### Usage

To use the `setAsync` function, pass it a string `storeId` representing the ID of the datastore you want to manipulate, a string `key` that uniquely identifies the value within the datastore, and an `value` object representing the data you want to store. The function will return a promise that resolves to a boolean indicating whether the value was successfully set in the datastore.

```ts
// This will set user-123's coins to 500 and then
// write to the console after it finishes.
Datastores.setAsync("myStore", "user123", {
  name: "John",
  age: 30,
}).then(() => {
  console.log("Set user");
});
```

---

## `Datastores.getAsync`

### Definition

```ts
getAsync<T>(
  storeId: string,
  key: string
): Promise<{
  id: string;
  key: string;
  value: T;
  gameDatastoreId: string;
}>;
```

The `getAsync` function retrieves a value from a specified datastore identified by its `storeId`. The `key` argument is used to uniquely identify the value within the datastore. The function returns a promise that resolves to an object containing the following properties:

- `id`: a string representing the ID of the value within the datastore
- `key`: a string representing the key used to retrieve the value
- `value`: the data stored in the datastore, of type `T`
- `gameDatastoreId`: a string representing the ID of the datastore

### Usage

To use the `getAsync` function, pass it a string `storeId` representing the ID of the datastore you want to retrieve a value from, and a string `key` representing the unique key used to identify the value within the datastore. The function will return a promise that resolves to an object containing the ID, key, value, and datastore ID of the retrieved value.

```ts
Datastores.getAsync<{
  name: string;
  age: number;
}>("myStore", "user123").then((result) => {
  console.log(result);
  // Output:
  //  {
  //    id: '123',
  //    key: 'user123',
  //    value: {
  //      name: 'John',
  //      age: 30
  //    },
  //    gameDatastoreId: 'myStore'
  //  }
});
```
