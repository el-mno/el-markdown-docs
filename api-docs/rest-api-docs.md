## API Documentation for a _(fictitious)_ Membership API


---

#### Create New Member

<details markdown="1"><summary markdown="span"><code>[POST] - Create new Member</code></summary>

<br />

**Endpoint:** `<base-url>/`

##### Description:

> Create a new Member record in the database. The record will be created with the parameters provided in the request body and assigned an auto-generated unique ID number.

##### Headers

> | name    | type     | data type | description                                                         |
> | ------- | -------- | --------- | ------------------------------------------------------------------- |
> | `token` | required | string    | Bearer token required to use API calls that modify member database. |

##### Query Parameters

`None`

##### Request Body

> | name    | type     | data type | description            |
> | ------- | -------- | --------- | ---------------------- |
> | `name`  | required | string    | Name of the Member     |
> | `email` | required | string    | Member's email address |
> | `age`   | required | number    | Age of the member      |

##### Responses

> | http code | content-type       | response                                                |
> | --------- | ------------------ | ------------------------------------------------------- |
> | `201`     | `application/json` | `{"message":"Member created successfully","id":<uuid>}` |
> | `400`     | `application/json` | `{"code":"400","message":"Bad Request"}`                |
> | `403`     | `application/json` | `{"code":"403","message":"Forbidden"}`                  |

##### Example cURL

> ```javascript
>  curl -X POST -H "Content-Type: application/json" -H --data input.json "Authorization: Bearer {token}" http://localhost:8080/
> ```

</details>

---

#### Retrieving Member Info

<details markdown="1"><summary markdown="span"><code>[GET] - Retrieve Member(s)</code></summary>

<br />

**Endpoint:** `<base-url>/members`

##### Description:

> Get all of the Members in the database.

##### Query Parameters

`None`

##### Responses

> | http code | content-type       | response      |
> | --------- | ------------------ | ------------- |
> | `200`     | `application/json` | `JSON Object` |

##### Example cURL

> ```javascript
>  curl -X GET -H "Content-Type: application/json" http://localhost:8080/members
> ```

##### Sample response

> ```javascript
> {
>   members: [
>        {
>            id: <unique uuid>
>            name: <string>
>            age: <number>
>            email: <string>
>        }
>    ]
> }
> ```

</details>

<details markdown="1"><summary markdown="span"><code>[GET] - Retrieve Member by ID</code></summary>

<br />

**Endpoint:** `<base-url>/{id}`

##### Description:

> Get the Member object corresponding to the `id` parameter provided.

##### Headers

`None`

##### Query Parameters

> | name | type     | data type     | description                  |
> | ---- | -------- | ------------- | ---------------------------- |
> | `id` | required | number (uuid) | The member unique identifier |

##### Responses

> | http code | content-type       | response      |
> | --------- | ------------------ | ------------- |
> | `200`     | `application/json` | `JSON Object` |

##### Example cURL

> ```javascript
>  curl -X GET -H "Content-Type: application/json" http://localhost:8080/{id}
> ```

##### Sample response

> ```javascript
> {
>   id: {id}
>   name: <string>
>   age: <number>
>   email: <string>
> }
> ```

</details>

<details markdown="1"><summary markdown="span"><code>[POST] - Find Member(s)</code></summary>

<br />

> **Endpoint:** `<base-url>/{id}`

##### Description:

> Retrieve all Member objects that match the parameters provided in the `Request Body`.

##### Headers

`None`

##### Query Parameters

`None`

##### Request Body

> `One parameter required`

> | name    | type     | data type     | description                  |
> | ------- | -------- | ------------- | ---------------------------- |
> | `id`    | optional | number (uuid) | The member unique identifier |
> | `name`  | optional | string        | The member's name            |
> | `email` | optional | string        | The member's email address   |

##### Responses

> | http code | content-type       | response                                 |
> | --------- | ------------------ | ---------------------------------------- |
> | `200`     | `application/json` | `JSON Object`                            |
> | `400`     | `application/json` | `{"code":"400","message":"Bad Request"}` |

##### Example cURL

> ```javascript
>  curl -X POST -H "Content-Type: application/json" --data @input.json http://localhost:8080/{id}
> ```

##### Sample response

> ```javascript
> {
>   members: [
>        {
>            id: <unique uuid>
>            name: <string>
>            age: <number>
>            email: <string>
>        },
>        {
>            id: <unique uuid>
>            name: <string>
>            age: <number>
>            email: <string>
>        }
>    ]
> }
> ```

</details>
<br />

---

#### Update Member

<details markdown="1"><summary markdown="span"><code>[PUT] - Update Member by ID</code></summary>

<br />

> **Endpoint:** `<base-url>/{id}`

##### Description

> Update the Member matching the `id` query parameter with the attributes in the `Request Body`.

##### Headers

> | name    | type     | data type | description                                                         |
> | ------- | -------- | --------- | ------------------------------------------------------------------- |
> | `token` | required | string    | Bearer token required to use API calls that modify member database. |

##### Query Parameters

> | name | type     | data type     | description                  |
> | ---- | -------- | ------------- | ---------------------------- |
> | `id` | required | number (uuid) | The member unique identifier |

##### Request Body

> | name    | type     | data type | description                |
> | ------- | -------- | --------- | -------------------------- |
> | `name`  | required | string    | The member's name          |
> | `email` | required | string    | The member's email address |

##### Responses

> | http code | content-type       | response                                                        |
> | --------- | ------------------ | --------------------------------------------------------------- |
> | `200`     | `application/json` | `{"code":"200","message":"Member: {id} updated successfully."}` |
> | `400`     | `application/json` | `{"code":"400","message":"Bad Request"}`                        |
> | `403`     | `application/json` | `{"code":"403","message":"Forbidden"}`                          |

##### Example cURL

> ```javascript
>  curl -X PUT -H "Content-Type: application/json" -H "Authorization: Bearer {token}" --data @input.json http://localhost:8080/{id}
> ```

##### Sample response

> ```javascript
> {
>   members: [
>        {
>            id: <unique uuid>
>            name: <string>
>            age: <number>
>            email: <string>
>        },
>        {
>            id: <unique uuid>
>            name: <string>
>            age: <number>
>            email: <string>
>        }
>    ]
> }
> ```

</details>
<br />

---

#### Delete Member Account

<details markdown="1"><summary markdown="span"><code>[DELETE] - Delete Member by ID</code></summary>

<br />

> **Endpoint:** `<base-url>/{id}`

##### Description

> Delete the Member record corresponding to the `id` provided.

##### Headers

> | name    | type     | data type | description                                                         |
> | ------- | -------- | --------- | ------------------------------------------------------------------- |
> | `token` | required | string    | Bearer token required to use API calls that modify member database. |

##### Query Parameters

> | name | type     | data type     | description                  |
> | ---- | -------- | ------------- | ---------------------------- |
> | `id` | required | number (uuid) | The member unique identifier |

##### Responses

> | http code | content-type       | response                                                         |
> | --------- | ------------------ | ---------------------------------------------------------------- |
> | `200`     | `application/json` | `{"code":"200","message":"Successfully deleted memberID: {id}"}` |
> | `400`     | `application/json` | `{"code":"400","message":"Bad Request"}`                         |
> | `403`     | `application/json` | `{"code":"403","message":"Forbidden"}`                           |

##### Example cURL

> ```javascript
>  curl -X DELETE -H "Content-Type: application/json" -H "Authorization: Bearer {token}" --data @input.json http://localhost:8080/{id}
> ```

</details>
