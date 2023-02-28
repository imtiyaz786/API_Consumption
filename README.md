# API_Consumption

This is a sample MVC Core project for consuming products api using javascript.
Everything is default in this project exception for an action method that returns Products view. The products view contains javascript code which is consuming api through fetch api.

Steps:
- Create an MVC core project.
- Inside HomeController(default template), add an action method Product():
  ```C#
      
     public IActionResult Products()
        {
            return View();
        }
    
  ```
- Add a view(Products.cshtml) for the same: 
  
  ```js
    <script>
    function getProducts() {
        fetch('https://localhost:44355/api/Products').then(response => response.json())
            .then(result => {
                alert('Successsssss');
                console.log(result);
                for (var i = 0; i < result.length; i++) {
                    $("table").append("<tr>" +
                        "<td>" + result[i].pId + "</td>" +
                        "<td>" + result[i].pName + "</td>" +
                        "<td>" + result[i].pCategory + "</td>" +
                        "<td>" + result[i].pPrice + "</td>" +
                        "<td>" + result[i].pIsInStock + "</td>" +
                        "<td><button class='btn btn-primary'> Add </button></td>" +
                        "<td><button class='btn btn-warning'> Edit </button></td>" +
                        "<td><button class='btn btn-danger'> Delete </button></td>" +

                        + "</tr>")
                }
            })
            .catch(err => {
                alert('errrrrorrr');
                console.log(err);
            })
    }
    </script>
    <button class="btn btn-primary" onclick="getProducts()"> Show products </button>
    <table class="table table-bordered"> </table> ```
- Under shared folder, within _Layout.cshtml, add these three lines with other actions:
  ```html
   <li class="nav-item">
       <a class="nav-link text-dark" asp-area="" asp-controller="Home" asp-action="Products">Products</a>
   </li>
  ```
- Now, build and run the project.
- You will see a navigation bar Products which you can click and navigate to Show products action.
- ProductAPI(to be consumed) repo: https://github.com/imtiyaz786/ProductAPI_EF
  
      
