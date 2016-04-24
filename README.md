# ui-router-route-to-components

Route to components today using Angular 1.5+ and ui-router 0.2.x+

# Usage

Add module dependency 'ui.router.components'

### Example state config:

```javascript
.state('users', {
	parent		: 'header',
	url			: '/users/:id',
	component  : 'users',
})
```
### Or
```javascript
.state('users', {
	parent		: 'header',
	url			: '/users/:id',
	views			: {
		'content@': {
			component  : 'users',
		}
	}
})
```
### Resolve:

```javascript
.state('users', {
	parent		: 'header',
	url			: '/users/:id',
	component  : 'users',
	resolve: {
        data: function () {
	        return "some data";
        }
	}
})

.component('users', {
    bindings: {
        data: '<'
    },
    controller: UsersController,
    templateUrl: '../app/users/users.template.html',
});

function UsersController() {
    console.log(this.data); // "some data"
}
```
# Credits

Code mostly borrowed from https://github.com/angular-ui/ui-router/issues/2547 but extended to also support multiple named views.
