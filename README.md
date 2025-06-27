# genericity
genericity or generics in java is a way to write code that works with different data types, without duplicating it.

### instead of writing the same code multiple times for String, Integer, Product, etc., you use a placeholder type, like T, and specify what type it is when u use it.

#### think of generics like baking molds:
- u have one mold (class/interface), but u can make different shapes (types) with it.

## example without generics
let's say we want to create a box that stores any object:
```
public class Box {
    private Object value;

    public void setValue(Object v) {
        value = v;
    }

    public Object getValue() {
        return value;
    }
}
```
when using the box
```
Box b = new Box();
b.setValue("hello");  // ok
String s = (String) b.getValue();  // need casting

//problem: u have to cast it to the right type. if u make a mistake, u get a runtime error!
```

---------------------------------------------------

## same example with generics
```
public class Box<T> {
    private T value;

    public void setValue(T v) {
        value = v;
    }

    public T getValue() {
        return value;
    }
}
```
usage
```
Box<String> b = new Box<>();
b.setValue("hello");
String s = b.getValue();  //no casting needed
```

---------------------------------------------------

## generic interface example
```
public interface IRepository<T> {
    void add(T item);
    T findById(int id);
}
```
u can use it like this Produit
```
public class ProduitRepository implements IRepository<Produit> {
    // implement add() and findById() for Produit
}

// then later u can create another class for Client, Commande, etc., without rewriting the interface.
```

-----------------------------------------------------

### when to use generics?
use henerics when:
- u want to write reusable code.
- u work with collections (like List<T>, Map<K, V>, etc.).
- u want to avoid casting and runtime type errors.

