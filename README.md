# Anjs
<!DOCTYPE html>

<html ng-app="todoApp">

<head>

<title>AngularJS Todo List</title>

<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.2/angular.min.js"></script>

</head>

<body ng-controller="todoController">

<h1>Todo List</h1>

<!-- Form for adding a new task -->

<form ng-submit="addTask()">

Task:

<input type="text" ng-model="newTask" required>

<button type="submit">Add Task</button>

</form>

<br>

<!-- Table to display task information -->

<table>

<thead>

<tr>

<th>Task</th>

<th>Action</th>

</tr>

</thead>

<tbody>

<tr ng-repeat="task in tasks">

<td>{{ task }}</td>

<td>

<button ng-click="editTask($index)">Edit</button>

<button ng-click="deleteTask($index)">Delete</button>

</td>

</tr>

</tbody>

</table>

<!-- Edit Task Modal -->

<div ng-if="editingTaskIndex !== null">

<h2>Edit Task</h2>

Task:

<input type="text" ng-model="tasks" required>

<br>

</div>

<script>

var app = angular.module('todoApp', []);

app.controller('todoController', function ($scope) {
  $scope.tasks = [

'Task 1',

'Task 2',

'Task 3'

];

$scope.newTask = '';

$scope.editingTaskIndex = null;

$scope.addTask = function () {

$scope.tasks.push($scope.newTask);

$scope.newTask = '';

};

$scope.editTask = function (index) {

// Prompt for updated task with validation

var updatedTask = prompt('Enter updated task:');

// Check if the user pressed cancel

if (updatedTask !== null) {

// Update the task

$scope.tasks.splice(index, 1, updatedTask);

}

};

$scope.deleteTask = function (index) {

$scope.tasks.splice(index, 2);

};

});

</script>

</body>

</html>
2222222222222222
<!DOCTYPE html>

<html ng-app="crudApp">

<head>

<title>AngularJS CRUD Application</title>

<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.2/angular.min.js"></script>

</head>

<body ng-controller="crudController">

<h1>User Management</h1>

<!-- Form for adding a new user -->

<form ng-submit="addUser()">

Name:

<input type="text" ng-model="name" required>

<br>

Age:

<input type="number" ng-model="age" required>

<br>

<button type="submit">Add User</button>

</form>

<br>

<!-- Table to display user information -->

<table>

<thead>

<tr>

<th>Name</th>

<th>Age</th>

<th>Action</th>

</tr>

</thead>

<tbody>

<tr ng-repeat="user in users">

<td>{{ user.name }}</td>

<td>{{ user.age }}</td>

<td>

<button ng-click="editUser(user)">Edit</button>

<button ng-click="deleteUser(user)">Delete</button>

</td>

</tr>

</tbody>

</table>

<script>

var app = angular.module('crudApp', []);

app.controller('crudController', function ($scope) {

$scope.users = [{ name: 'Ram', age: 25 },

{ name: 'Sam', age: 30 },

];

$scope.addUser = function () {

$scope.users.push({ name: $scope.name, age: $scope.age });

$scope.name = '';

$scope.age = '';

};

$scope.editUser = function (user) {

var index = $scope.users.indexOf(user);

// Prompt for updated values with validation

var updatedName = prompt('Enter updated name:', user.name);

var updatedAge = prompt('Enter updated age:', user.age);

// Check if the user pressed cancel

if (!(updatedName == null && updatedAge == null) ){

// Update the user

var updatedUser = { name: updatedName, age: parseInt(updatedAge) };

$scope.users.splice(index, 1, updatedUser);

}

};

$scope.deleteUser = function (user) {

var index = $scope.users.indexOf(user);

$scope.users.splice(index, 1);

};

});

</script>

</body>

</html>
