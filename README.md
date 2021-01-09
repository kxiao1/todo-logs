# todo-logs
A decoupled webapp with a ReactJS frontend and Django backend. It collects, stores, and displays (in a daily or weekly format) a list of tasks and the status of each. Communication between frontend and backend is provided by ``Django Rest Framework``'s RESTful API, and accessed using JavaScript's ``Fetch`` API at the frontend.

There is a small bit of login code that authenticates the user with ``JSON Web Tokens`` (JWTs) before he/she can see the to-do logs. Upon successful login, a JWT token is provided by Django REST framework JWT and stored in ``localstorage``. The presence of such a token is sufficient to expose all functionalities. Because this app is strictly for single-user, personal use at the moment, such a framework seems adequate.  

See the frontend and backend repositories, which are included as submodules, for more details of their respective implementations.

## Future Work
* Allow for multiple users by adding a <i>User</i> field to each database entry (or otherwise associating each entry to a user) 
* Set object-level permissions, and use DRF properties such as ``properties.isAuthenticatedOrReadOnly`` to avoid relying on ``localstorage``. This allows JWT's to be used for per-request in addition to per-session authentication.
* Generate PDF's/Excels or other reports from given logs.

## Credits
The app idea originated from <https://www.digitalocean.com/community/tutorials/build-a-to-do-application-using-django-and-react>, but the final product provides a slightly different set of features. The usage of ``djangorestframework-jwt`` was suggested by <https://medium.com/@dakota.lillie/django-react-jwt-authentication-5015ee00ef9a>.