# Delivery Task Processing System

Delivery Task Processing System(DTPS) is a food delivery platform.

### Models

Task
- title
- priority (high, medium, low)
- creation_date
- created_by(FK)
- assigned_to(FK)
- state(FK)

StoreManager (User)
DeliveryPerson (User)

TaskStateHistory
- previous_state(FK)
- state(FK)
- task_id(FK)
- enter_time
- exit_time

State
- name 


### State Movement
- new
- accepted
- completed
- declined
- cancelled

new -> accepted
new -> cancelled (END STATE)

new -> accepted -> completed (END STATE)
new -> accepted -> declined
new -> accepted -> declined -> new

### API DOCUMENTATION
```http
GET /tasks
```
Parameters:
| Parameter | Type |
| :--- | :--- |
| `manager_id` | `int` |
Response:
```javascript
{
  "success" : bool,
  "task_list"    : [{}]
  "error": None
}
```
```http
GET /tasks/id
```
Parameters:
| Parameter | Type | 
| :--- | :--- |
| `task_id` | `int` | 
Response:
```javascript
{
  "success" : bool,
  "task_data"    : {}
  "error": None
}
```
```http
GET /tasks/pending
```
Parameters:
| Parameter | Type |
| :--- | :--- |
| `manager_id` | `int` |
Response:
```javascript
{
  "success" : bool,
  "tasks"    : [{}] //Max 3, and in prioritized order
  "error": None
}
```
```http
POST /tasks/add
```
Parameters:
| Parameter | Type |
| :--- | :--- |
| `title` | `string` |
| `priority` | `string`|
| `created_by` | `string` |
Response:
```javascript
{
  "success" : bool,
  "error": None
}
```
```http
POST /tasks/accept
```
Parameters:
| Parameter | Type |
| :--- | :--- |
| `task_id` | `int` |
Response:
```javascript
{
  "success" : bool,
  "error": None
}
```
```http
POST /tasks/cancel
```
Parameters:
| Parameter | Type |
| :--- | :--- |
| `task_id` | `int` |
Response:
```javascript
{
  "success" : bool,
  "error": None
}
```
```http
POST /tasks/decline
```
Parameters:
| Parameter | Type |
| :--- | :--- |
| `task_id` | `int` |
Response:
```javascript
{
  "success" : bool,
  "error": None
}
```
