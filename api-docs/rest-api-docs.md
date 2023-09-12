---
title: API Documentation Sample
---

## API Documentation for a _(fictitious)_ Membership API

---

#### Create New Member

<details markdown="1"><summary markdown="span"><code>POST &emsp;/</code></summary>

##### Headers

> | name  | type     | data type | description                                                         |
> | ----- | -------- | --------- | ------------------------------------------------------------------- |
> | `token` | required | string    | Bearer token required to use API calls that modify member database. |

##### Parameters

> `None`

##### Responses

> | http code | content-type               | response                                 |
> | --------- | -------------------------- | ---------------------------------------- |
> | `201`     | `text/plain;charset=UTF-8` | `Member created successfully`            |
> | `400`     | `application/json`         | `{"code":"400","message":"Bad Request"}` |
> | `403`     | `application/json`         | `{"code":"403","message":"Forbidden"}`   |

##### Example cURL

> ```javascript
>  curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer {token}" http://localhost:8080/
> ```

</details>

---

#### Retrieving Member Info

<details markdown="1"><summary markdown="span"><code>GET &emsp;/ &emsp;&emsp;&emsp;&emsp;&emsp;Retrieve all Members</code></summary>

##### Parameters

> `None`

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

<details markdown="1"><summary markdown="span"><code>GET&emsp;/{id} &emsp;&emsp;Retrieve a single Member</code></summary>

##### Parameters

> `None`

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

---

#### Finding Members

<details markdown="1"><summary markdown="span"><code>POST &emsp;/ &emsp;&emsp;&emsp;&emsp;Find Member(s)</code></summary>

##### Parameters

> `One parameter required`

> | name    | type     | data type     | description                  |
> | ------- | -------- | ------------- | ---------------------------- |
> | `id`    | optional | number (uuid) | The member unique identifier |
> | `name`  | optional | string        | The member's name            |
> | `email` | optional | string        | The member's email address   |

##### Responses

> | http code | content-type               | response                                 |
> | --------- | -------------------------- | ---------------------------------------- |
> | `200`     | `text/plain;charset=UTF-8` | `JSON Object`                            |
> | `400`     | `application/json`         | `{"code":"400","message":"Bad Request"}` |
> | `405`     | `text/html;charset=utf-8`  | `None`                                   |

##### Example cURL

> ```javascript
>  curl -X GET -H "Content-Type: application/json" --data @input.json http://localhost:8080/
> ```

##### Example output

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

---

#### Update Member

<details markdown="1"><summary markdown="span"><code>PUT &emsp;/{id} &emsp;Update Member(s)</code></summary>

##### Parameters

> | name  | type     | data type     | description                                                         |
> | ----- | -------- | ------------- | ------------------------------------------------------------------- |
> | `id`  | required | number (uuid) | The member unique identifier                                        |
> | `token` | required | string        | Bearer token required to use API calls that modify member database. |

##### Responses

> | http code | content-type               | response                                 |
> | --------- | -------------------------- | ---------------------------------------- |
> | `200`     | `text/plain;charset=UTF-8` | `JSON Object`                            |
> | `400`     | `application/json`         | `{"code":"400","message":"Bad Request"}` |
> | `403`     | `application/json`         | `{"code":"403","message":"Forbidden"}`   |
> | `405`     | `text/html;charset=utf-8`  | `None`                                   |

##### Example cURL

> ```javascript
>  curl -X GET -H "Content-Type: application/json" --data @input.json http://localhost:8080/
> ```

##### Example output

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
