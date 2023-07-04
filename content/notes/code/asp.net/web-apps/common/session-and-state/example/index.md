---
title: notes > code > asp.net > web apps > common > session and state > example
date: 2023-03-24T00:00:00-07:00
draft: false
---

A session and state implementation example.  

# Demonstration — Adding a Shopping Cart
Create the shopping cart item model:  
`/Models/ShoppingCartItem.cs`
```cs
public class ShoppingCartItem
{
    public int ShoppingCartItemId { get; set; }
    public Pie Pie { get; set; } = default!; // the Pie added to the cart
    public int Amount { get; set; } // the cost of the Pie
    public string? ShoppingCartId { get; set; } // a GUID
}
```

Create a `DbSet` for the `ShoppingCartItems`:  
`/Models/BethanysPieShopDbContext.cs`
```cs
// …
    public DbSet<ShoppingCartItem> ShoppingCartItems { get; set; }
// …
```

Update the Database
```powershell
pm> add-migration ShoppingCartItem
pm> update-database
```

Create an interface for the shopping cart:  
`/Models/IShoppingCart.cs`
```cs
public interface IShoppingCart
{
    List<ShoppingCartItem> ShoppingCartItems { get; set; }

    void AddToCart(Pie pie);
    int RemoveFromCart(Pie pie);
    List<ShoppingCartItem> GetShoppingCartItems();
    void ClearCart();
    decimal GetShoppingCartTotal();
}
```

Create the shopping cart model:  
`/Models/ShoppingCart.cs`
```cs
// …
```

Update DI:  
`Program.cs`
```cs
builder.Services.AddSession();
builder.Services.AddHttpContextAccessor();

builder.Services.AddScoped<IShoppingCart, ShoppingCart>(ShoppingCart.GetCart);

app.UseSession();
```

Add a shopping cart controller:  
`Controllers/ShoppingCartController.cs`
```cs
public class ShoppingCartController : Controller
{
    private readonly IPieRepository _pieRepository;
    private readonly IShoppingCart _shoppingCart;

    public ShoppingCartController(IPieRepository pieRepository, IShoppingCart shoppingCart)
    {
        _pieRepository = pieRepository;
        _shoppingCart = shoppingCart;
    }

    
    public ViewResult Index()
    {
        var items = _shoppingCart.GetShoppingCartItems();
        _shoppingCart.ShoppingCartItems = items;

        var shoppingCartViewModel = new ShoppingCartViewModel(_shoppingCart, _shoppingCart.GetShoppingCartTotal());

        return View(shoppingCartViewModel);
    }

    public RedirectToActionResult AddToShoppingCart(int pieId)
    {
        var selectedPie = _pieRepository.AllPies.FirstOrDefault(p => p.PieId == pieId);

        if (selectedPie is not null)
            _shoppingCart.AddToCart(selectedPie);

        return RedirectToAction("Index"); // redirect to index of shopping cart
    }

    public RedirectToActionResult RemoveFromShoppingCart(int pieId)
    {
        var selectedPie = _pieRepository.AllPies.FirstOrDefault(p => p.PieId == pieId);

        if (selectedPie is not null)
            _shoppingCart.RemoveFromCart(selectedPie);

        return RedirectToAction("Index");
    }
}
```
Add a shopping cart viewmodel:  
`/ViewModels/ShoppingCartViewModel.cs`
```cs
public class ShoppingCartViewModel
{
    public IShoppingCart ShoppingCart { get; set; }
    public decimal ShoppingCartTotal { get; }

    public ShoppingCartViewModel(IShoppingCart shoppingCart, decimal shoppingCartTotal)
    {
        ShoppingCart = shoppingCart;
        ShoppingCartTotal = shoppingCartTotal;
    }
}
```

Add a shopping cart view (index page):  
`/Views/ShoppingCart/index.cshtml`
```html
@model ShoppingCartViewModel

<h3 class="my-5">
    Shopping cart
</h3>


<div class="row gx-3">
    <div class="col-8">
        @foreach (var line in Model.ShoppingCart.ShoppingCartItems)
        {
            <div class="card shopping-cart-card mb-2">
                <div class="row">
                    <div class="col-md-4">
                        <img src="@line.Pie.ImageThumbnailUrl" class="img-fluid rounded-start p-2" alt="@line.Pie.Name">
                    </div>
                    <div class="col-md-8">
                        <div class="card-body">
                            <h5 class="card-text">@line.Amount x @line.Pie.Name</h5>
                            <div class="d-flex justify-content-between">
                                <h6>@line.Pie.ShortDescription</h6>
                                <h2>@line.Pie.Price.ToString("c")</h2>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        }
    </div>
    <div class="col-4">
        <div class="card shopping-cart-card p-3">
            <div class="row">
                <h4 class="col">Total:</h4>
                <h4 class="col text-end">@Model.ShoppingCartTotal.ToString("c")</h4>
            </div>
            <hr />
            <div class="text-center d-grid">
            </div>
        </div>
    </div>
</div>
```
