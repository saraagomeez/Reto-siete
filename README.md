# Reto-siete

## Iterable Menu

Para este reto:

**1.** Se tomó el código previamente realizado en el reto 3, y se le agregó una función tipo **str** a cada clase que hace parte del menú, de forma que más adelante al querer iterar, se pueda representar el objeto en forma de cadena.

**2.** Se realizó un bloque para que se pueda iterar sobre los elementos de la orden, de modo que pueda mencionar todos los atributos importantes del item.

```
class MenuItem:
    def __init__(self, name, price):
        self.name = name
        self.price = price
    
    def calculate_total_price(self):
        return self.price
    
    def __str__(self):
        return f"Name: {self.name}, Price: {self.price}"
    
class Appetizers(MenuItem):
    def __init__(self, name:str, price:int, servings:int):
        super().__init__(name, price)
        self._servings = servings

    def __str__(self):
        return f"(Appetizer) Name: {self.name}, Price: {self.price}, Servings: {self._servings}"

class Soups(MenuItem):
    def __init__(self, name:str, price:int, type:str):
        super().__init__(name, price)
        self.type = type #cream or soup

    def __str__(self):
        return f"(soup) Name: {self.name}, Price: {self.price}, Type: {self.type}"

class Salads(MenuItem):
    def __init__(self, name:str, price:int, dressing:bool):
        super().__init__(name, price)
        self.dressing = dressing

    def __str__(self):
        return f"(Salad) Name: {self.name}, Price: {self.price}, Dressing: {self.dressing}"

class MainCourse(MenuItem):
    def __init__(self, name:str, price:int, portion_size:int):
        super().__init__(name, price)
        self.portion_size = portion_size

    def __str__(self):
        return f"(MainCourse) Name: {self.name}, Price: {self.price}, Portion sice: {self.portion_size}"

class Desserts(MenuItem):
    def __init__(self, name:str, price:int, flavor:str):
        super().__init__(name, price)
        self.flavor = flavor

    def __str__(self):
        return f"(Dessert) Name: {self.name}, Price: {self.price}, Flavor: {self.flavor}"

class Beverages(MenuItem):
    def __init__(self, name:str, price:int, alcoholic:bool):
        super().__init__(name, price)
        self.alcoholic = alcoholic

    def __str__(self):
        return f"(Beverage) Name: {self.name}, Price: {self.price}, Alcoholic: {self.alcoholic}"

class Order:
    def __init__(self):
        self.items = []

    def add_item(self, item):
        self.items.append(item)

    def calculate_total(self):
        total = sum(item.calculate_total_price() for item in self.items)
        return total
    
class MenuItemIterador:
    def __init__(self, items):
        self.items = items
        self.indice = 0

    def __iter__(self):
        return self
    
    def __next__(self):
        if self.indice < len(self.items):
            item = self.items[self.indice]
            self.indice += 1
            return item
    
menu_items = [
    Appetizers("Carpaccio", 25000, 1),
    Appetizers("Shrimps", 35000, 1),
    Appetizers("Cheese plate", 30000, 3),
    Soups("Onion soup", 25000, "soup"),
    Soups("Tomato soup", 30000, "Cream"),
    Soups("Mushrooms soup", 25000, "Cream"),
    Salads("Cesar salad", 20000, True),
    Salads("Smoked salmon salad", 35000, False),
    Salads("Caprese salad", 25000, True),
    MainCourse("steak with wine sauce", 60000, "Medium"),
    MainCourse("Seafood risotto", 50000, "Big"),
    MainCourse("Duck in red fruits", 65000, "Small"),
    Desserts("Chocolate cake", 25000, "Chocolate"),
    Desserts("Creme brulee", 20000, "Milk"),
    Desserts("Souffle", 30000, "Red fruits"),
    Beverages("Water", 8000, False),
    Beverages("Soda", 12000, False),
    Beverages("Bottle of wine", 120000, True),
    Beverages("Bottle of champagne", 250000, True)
    ]
    
order = Order()
order.add_item(menu_items[1])
order.add_item(menu_items[4])
order.add_item(menu_items[7])
order.add_item(menu_items[11])
order.add_item(menu_items[14])
order.add_item(menu_items[15])
order.add_item(menu_items[18])

print ("Order: ")
for item in order.items:
    print("\n", item)
```
