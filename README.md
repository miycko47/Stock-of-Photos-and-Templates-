# This is a project walkthrough note that consits of tags, block of codes, scripts etc..
    def get_tag(self):
        return self.kwargs.get('tag')

    def get_queryset(self):
        return self.model.objects.filter(tags__slug=self.get_tag())
    
    def get_context_data(self, **kwargs):
        context = super().get_context_data(**kwargs)
        context["tag"] = self.get_tag()
        return context
        
- This line defines a class called "TagCloud" which inherits from the Django "Context" class.

- This line defines a method called "get_tag" which takes no arguments and simply returns the value stored in the "kwargs" dictionary under the "tag" key.

- This line defines a method called "get_queryset" which simply filters the model "objects" using the "tags__slug" filter to find all objects that have the given tag.

- This line defines a method called "get_context_data" which takes **kwargs as an argument. This method simply overrides the "Context" class's "get_context_data" method and sets the "context["tag"]" key to the value returned by the "get_tag" method.

      def get_photo(self):
       return get_object_or_404(Photo, pk=self.kwargs.get('pk'))
    
      def test_func(self):
        
        if self.request.user.is_authenticated:
            return self.request.user == self.get_photo().submitter
        else:
            raise PermissionDenied('Sorry you are not allowed here')
    This is a custom method
    
- This is a class definition for a function that will get a photo from the database.

- The function will return an object or 404 if it can't find the photo.

- The function will test if the user is authenticated and if they are, it will return
whether or not the user is the submitter of the photo.

- If the user is not authenticated, the function will raise a PermissionDenied error.


<body>
        
    {% include 'navbar.html' %}

    <div class="container mt-4">
    {% block body %} 
    
    {% endblock body %}
    
    </div>

    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-p34f1UUtsS3wqzfto5wAAmdvj+osOnFyQFpp4Ua3gs/ZVWx6oOypYoCJhGGScy+8"
      crossorigin="anonymous">
    </script>
        
  </body>


- Includes the navbar.html file, which creates a navigation bar at the top of the page.

- The body block is defined, which will be used to create the content of the page.

- The content of the page is created, starting with a paragraph of text.

- A link to the Google homepage is added.

- The content of the page is finished.

- The bootstrap.bundle.min.js file is loaded, which provides Bootstrap styling for the page.

 The page is finished.
 
 
    <ul class="navbar-nav">
         {% if user.is_authenticated %}
        
        <li class="nav-item">
          <a class="nav-link active" href="{% url 'photo:create' %}">Add a photo</a>
        </li>
        <li class="nav-item">
          <a class="nav-link active" href="#">Hi {{user.username}}</a>
        </li>
        {% else %}

        <li class="nav-item">
          <a href="{% url 'user:login' %}" class="btn btn-sm btn-danger"
            >Sign In</a
          >
        </li>
        {% endif %}
      </ul>
      
 - The code checks if the user is authenticated. If so, it displays a list of links.

 -  If the user is not authenticated, it displays a list of links as well, but with a different class.

3-5) These lines create a list item with an active link to add a photo and a regular link to Hi {{user.username}}.
