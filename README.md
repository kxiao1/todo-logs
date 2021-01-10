# todo-logs
A decoupled webapp with a ReactJS frontend and Django backend. It collects, stores, and displays (in a daily or weekly format) a list of tasks and the status of each. Communication between frontend and backend is provided by ``Django Rest Framework``'s RESTful API, and accessed using JavaScript's ``Fetch`` API at the frontend.

There is a small bit of login code that requests for a ``JSON Web Tokens`` (JWTs) on each refresh, before the user can see the to-do logs. Upon successful authentication, the JWT token provided by ``django-rest-framework-simplejwt`` is stored in ``localstorage``. The presence of such a token is sufficient to expose all functionalities. Because this app is strictly for single-user, personal use at the moment, such a 'brute-force' framework seems reasonable.  

See the frontend and backend repositories, which are included as submodules, for details of their respective implementations.

## Future Work
* Allow for multiple users by adding a <i>User</i> field to each database entry (or otherwise associating each entry to a user) 
* Set object-level permissions, and override DRF's default permission classes such as ``isAuthenticatedOrReadOnly``. This allows JWT's to be used for per-request in addition to per-session authentication.
* Consider alternatives to ``localStorage`` (``localForage``?)
* Generate PDF's/Excels or other reports from given logs.
* Deploy to production!

## Credits
The app idea originated from <https://www.digitalocean.com/community/tutorials/build-a-to-do-application-using-django-and-react>, but the final product provides a slightly different set of features. The usage of ``djangorestframework-jwt`` (of whom ``django-rest-framework-simplejwt`` is a descendant) was suggested by <https://medium.com/@dakota.lillie/django-react-jwt-authentication-5015ee00ef9a>.