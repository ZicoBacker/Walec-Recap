# SOLID 
SOLID staat voor :
- Single Responsibility Principle (SRP)
- Open-Closed Principle (OCP)
- Liskov Substitution Principle (LSP)
- Interface Segregation Principle (ISP)
- Dependency Inversion Principle (DIP)

Wij gaan hier later verder op in (ik zal linkjes correct maken wanneer we daar aan toe komen)
## OOP (Object Oriented Programming)
object oriented programming is simpel gezegd een variabel met meerdere waarden. Denk aan een associative array ongeveer. Wij leren dit in php door classes. Je maakt een class aan
```php
<?php
class hello{
	public $a = 'hello';
	public $b = 'doei';
}
 $hello1 = new hello;
  echo $hello1->a;
?>
```
in de class maak je public variabele aan die je vervolgens aan kan roepen via de class. Dit kan niet met private variabele, Die werken tevens ook alleen in de class. Om de class gebruiken maak je een nieuwe variabele met de class `$hello = new className`. Om dan vervolgens de variable in de class aan te roepen doe je `$hello->$a`

