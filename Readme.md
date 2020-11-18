# Reflexión

Utilización de reflexión para indagar sobre el acceso de los métodos de un tipo(Simple Class)

```csharp
 var method = member as MethodBase;
 if (method != null)
 {
     if (method.IsPublic)
         access = " Public";
     else if (method.IsPrivate)
	     access = " Private";
     else if (method.IsFamily)
    	 access = " Protected";
     else if (method.IsAssembly)
	     access = " Internal";
     else if (method.IsFamilyOrAssembly)
    	 access = " Protected Internal ";
     if (method.IsStatic)
	     stat = " Static";
 }
```



# Extensiones

Implementación de métodos de extension sobre tipo built-in (string)

```csharp
 public static bool ContainsNumbers(this String s)
 {
 // Use regular expressions determining whether the string contains any numerical digits.
     return Regex.IsMatch(s, @"\d");
 }
```

Implementación de métodos de extension sobre tipos custom

```csharp
public static void ListaDescendente(this EjemploExtension eE)
{
   for(int i = 10; i > 0; i--)
   {
       WriteLine($"i:{i}");
   }
}
```

```csharp
public struct EjemploExtension
{
    public void ListaNumeros()
    {
        for (int i = 0; i < 10; i++)
        {
            WriteLine($"i:{i}");
        }
    }
}
```



# Custom Exception

```csharp
public void UsingCustomException(bool generaException)
{
    try
    {
        WriteLine("Paso linea 78");
        if (generaException)
        {
            WriteLine("Paso linea antes del throw");
            throw new LoyaltyCardNotFoundException("The card number provided was not found");
        }
        WriteLine("Paso Linea 84");
    }
    catch (LoyaltyCardNotFoundException ex)
    {
        WriteLine("Paso Linea Catch");
        WriteLine(ex.Message);
    }
    finally
    {
        WriteLine("Paso Linea Finally");
    }
}
```

Implementación de un custom exception

```csharp
public class LoyaltyCardNotFoundException : Exception
{
    public LoyaltyCardNotFoundException()
    {
    // This implicitly calls the base class constructor.
    }
    public LoyaltyCardNotFoundException(string message) 
    : base(message)
    {
    }
    public LoyaltyCardNotFoundException(string message, Exception inner) 
    : base(message, inner)
    {
    }
}
```

# Tipo Date Time

Uso de Date Time combinando la cultura y la salida de formarto

```csharp
DateTime myBirthday = new DateTime(day:31,month:12,year:1968);
WriteLine(myBirthday.ToShortDateString());
//Format of DateTime.Parse("dia/mes/año");
try
{
    myBirthday = DateTime.Parse("31/12/1968");
}
catch (SystemException e)
{
    WriteLine(new String('=', 120));
    WriteLine($"{e}");
    WriteLine(new String('=', 120));
}
//Represent a interval of time
TimeSpan myAge = DateTime.Now.Subtract(myBirthday);
WriteLine(myAge.TotalDays);
string dateInput = "Dec 21, 2018"; // Esto no funciona si la cadena es "Dic 21, 2018"
DateTime parsedDated = DateTime.Parse(dateInput);
WriteLine("{0}", parsedDated);
CultureInfo myCultureInfo = new CultureInfo("es-ES");
Thread.CurrentThread.CurrentCulture = myCultureInfo;  // HEmos de cambiar el Thread para que a partir de ahora 
// cambie la cultura
string mySpanishDate = "23 octubre 2020";
DateTime myDateTimeSpanish = DateTime.Parse(mySpanishDate, myCultureInfo);
WriteLine("Fecha corta:{0}", myDateTimeSpanish.ToShortDateString());
WriteLine("Fecha larga:{0}", myDateTimeSpanish.ToLongDateString());
```



# Genéricos de condicionales de dos tipos

```csharp
public class MyClass<T, U>
//where T : class
//where U : struct
{
}
```

