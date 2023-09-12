## API Documentation for a _(fictitious)_ Membership API

---

#### Create New Member

<details>
 <summary><code>POST</code> <code><b>/</b></code></summary>

##### Headers

> | name  | type     | data type | description                                                         |
> | ----- | -------- | --------- | ------------------------------------------------------------------- |
> | token | required | string    | Bearer token required to use API calls that modify member database. |

##### Parameters

> None

##### Responses

> | http code | content-type               | response                                 |
> | --------- | -------------------------- | ---------------------------------------- |
> | `201`     | `text/plain;charset=UTF-8` | `Configuration created successfully`     |
> | `400`     | `application/json`         | `{"code":"400","message":"Bad Request"}` |
> | `405`     | `text/html;charset=utf-8`  | None                                     |

##### Example cURL

> ```javascript
>  curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer {token}" http://localhost:8080/
> ```

</details>

---

#### Retrieving Member Info

<details>
 <summary><code>GET</code> <code><b>/</b></code> <code>Retrieve all Members</code></summary>

##### Parameters

> None

##### Responses

> | http code | content-type               | response      |
> | --------- | -------------------------- | ------------- |
> | `200`     | `text/plain;charset=UTF-8` | `JSON Object` |

##### Example cURL

> ```javascript
>  curl -X GET -H "Content-Type: application/json" http://localhost:8080/
> ```

##### Example output

> ```javascript
> {
>   members: [
>       {
>            id: <unique uuid>
>            name: <string>
>            age: <number>
>            email: <string>
>        }
>    ]
> }
> ```

</details>

<details>
 <summary><code>GET</code> <code><b>/{id}</b></code> <code>Retrieve a single Member</code></summary>

##### Parameters

> None

##### Responses

> | http code | content-type               | response      |
> | --------- | -------------------------- | ------------- |
> | `200`     | `text/plain;charset=UTF-8` | `JSON Object` |

##### Example cURL

> ```javascript
>  curl -X GET -H "Content-Type: application/json" http://localhost:8080/{id}
> ```

##### Example output

> ```javascript
> {
>   id: {id}
>   name: <string>
>   age: <number>
>   email: <string>
> }
> ```

</details>
