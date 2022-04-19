> a stack is a circlejerk of web specialisations that work together to build an SPA

We want to deploy things incrementally, with a supporting system in [[Continuous Integration]]



1. [[React]] <-> [[Express]]/Node <-> MongoDB
	+ Express is a neat wrapper over Node
	+ MongoDB seems to integrate easily with most cloud services
2. React <-> Django Rest <-> [[Django]] <-> PostgreSQL
	+ React is generally configured with [[Redux]] HTTP, Router
	+ React is compiled using webpack and Babel
	+ React interacts with Django using a Django REST framework
		+ Testing REST can be done with Postman or VS Code REST

+ #todo: 
	+ where does GraphQL fit? 
	+ Relational Databases?
	+ Containers?
